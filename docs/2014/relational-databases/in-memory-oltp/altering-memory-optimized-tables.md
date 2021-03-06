---
title: メモリ最適化テーブルの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 690b70b7-5be1-4014-af97-54e531997839
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65d72bac30b1a531d332e88c4b8e59afc73f7afb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37193344"
---
# <a name="altering-memory-optimized-tables"></a>メモリ最適化テーブルの変更
  メモリ最適化テーブルに対する ALTER 操作はサポートされていません。 これには、bucket_count の変更、インデックスの追加または削除、列の追加または削除などが含まれます。 このトピックでは、メモリ最適化テーブルを更新する方法のガイドラインについて説明します。  
  
## <a name="updating-the-definition-of-a-memory-optimized-table"></a>メモリ最適化テーブルの定義の更新  
 メモリ最適化テーブルの定義を更新すると、更新されたテーブル定義を使用して新しいテーブルを作成し、新しいテーブルにデータをコピーし、新しいテーブルの使用を開始することが必要になります。 テーブルが読み取り専用でない限り、データ コピーが行われている間にテーブルに変更が行われないように、テーブル上のワークロードを停止する必要があります。  
  
 以下に、テーブルの更新手順の概要を示します。 この例では、インデックスを追加します。 この手順はテーブルの名前を保持し、一時テーブルに 1 回、新しいテーブルに 1 回の、2 つのデータ コピー操作が必要となります。 インデックスの bucket_count の変更や、列の追加または削除も同じように実行されます。  
  
1.  テーブル上のワークロードを停止します。  
  
2.  テーブルのスクリプトを生成し、スクリプトに新しいインデックスを追加します。  
  
3.  T とその権限を参照するスキーマ バインド オブジェクト (主にネイティブ コンパイル ストアド プロシージャ) のスクリプトを生成します。  
  
     テーブルを参照するスキーマ バインド オブジェクトは、次のクエリを使用して見つけることができます。  
  
    ```tsql  
    declare @t nvarchar(255) = N'<table name>'  
  
    select r.referencing_schema_name, r.referencing_entity_name  
    from sys.dm_sql_referencing_entities (@t, 'OBJECT') as r join sys.sql_modules m on r.referencing_id=m.object_id  
    where r.is_caller_dependent = 0 and m.is_schema_bound=1;  
    ```  
  
     ストアド プロシージャの権限は、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用してスクリプト化できます。  
  
    ```tsql  
    declare @sp nvarchar(255) = N'<procedure name>'  
    declare @permissions nvarchar(max) = N''  
  
    select @permissions += dp.state_desc + N' ' + dp.permission_name + N' ON ' +   
       quotename(schema_name(o.schema_id)) + N'.' + quotename(o.name) + N' TO ' +  
       quotename(u.name) + N'; ' + char(13)  
    from sys.database_permissions as dp  
  
    join sys.database_principals as u  
       on u.principal_id = dp.grantee_principal_id  
  
    join sys.objects as o  
       on o.object_id = dp.major_id  
    where dp.class = 1 /* object */  
       and dp.minor_id = 0 and o.object_id=object_id(@sp);  
  
    select @permissions  
    ```  
  
4.  テーブルのコピーを作成し、元のテーブルからテーブルのコピーにデータをコピーします。 次を使用して、コピーを作成できます[!INCLUDE[tsql](../../includes/tsql-md.md)] <sup>1</sup>します。  
  
    ```tsql  
    select * into dbo.T_copy from dbo.T  
    ```  
  
     使用可能なメモリ不足のために場合、`T_copy`データのコピーを高速化は、メモリ最適化テーブルになります<sup>。2</sup>  
  
5.  元のテーブルを参照するスキーマ バインド オブジェクトを削除します。  
  
6.  元のテーブルを削除します。  
  
7.  新しいインデックスを含むスクリプトで、新しいテーブル (`T`) を作成します。  
  
8.  `T_copy` から `T` にデータをコピーします。  
  
9. 参照しているスキーマ バインド オブジェクトを再作成し、権限を適用します。  
  
10. `T` のワークロードを起動します。  
  
 <sup>1</sup>なお`T_copy`が永続化されるこの例ではディスクにします。 `T` のバックアップが使用可能であれば、`T_copy` に一時的または持続性のないテーブルを指定することもできます。  
  
 <sup>2</sup>のに十分なメモリが必要があります`T_copy`します。 `DROP TABLE` ではメモリがすぐには解放されません。 `T_copy` がメモリ最適化されている場合は、`T` のコピーを 2 つ作成するための十分なメモリが必要です。 `T_copy` がディスク ベース テーブルの場合は、`T` の古いバージョンを削除した後にガベージ コレクターによって補完されるため、`T` の付加的なコピーを 1 つ作成するためのメモリがあれば問題ありません。  
  
## <a name="changing-schema-powershell"></a>スキーマの変更 (PowerShell)  
 次の PowerShell スクリプトは、テーブルや関連する権限のスクリプトを作成することで、スキーマの変更に備えます。  
  
 使用法: prepare_schema_change.ps1 *server_name * * db_name`schema_name`table_name*  
  
 このスクリプトは、引数としてテーブルを受け取り、オブジェクトとその権限のスクリプトを作成し、現在のフォルダーのスキーマ バインド オブジェクトとその権限を参照します。 入力テーブルのスキーマを更新するために、合計 7 種類のスクリプトが生成されます。  
  
-   一時テーブル (ヒープ) にデータをコピーします。  
  
-   テーブルを参照するスキーマ バインド オブジェクトを削除します。  
  
-   テーブルを削除します。  
  
-   新しいスキーマでテーブルを再作成し、権限を再適用します。  
  
-   一時テーブルから再作成されたテーブルにデータをコピーします。  
  
-   テーブルとその権限を参照しているスキーマ バインド オブジェクトを再作成します。  
  
-   一時テーブルを削除します。  
  
 目的のスキーマの変更を反映するように、手順 4. のスクリプトを更新する必要があります。 テーブルの列にすべての変更がある場合 (一時テーブルからデータをコピーする) のスクリプトの手順 5 と 6 (ストアド プロシージャを再作成) する必要がありますが必要に応じて更新されます。  
  
```tsql  
# Prepare for schema changes by scripting out the table, as well as associated permissions  
# --------  
# Usage: prepare_schema_change.ps1 server_name db_name schema_name table_name  
# stop execution once an error occurs  
$ErrorActionPreference="Stop"  
  
if($args.Count -le 3)  
{  
   throw "Usage prepare_schema_change.ps1 server_name db_name schema_name table_name"  
}  
  
$servername = $args[0]  
$database = $args[1]  
$schema = $args[2]  
$object = $args[3]  
  
$object_heap = "$object$(Get-Random)"  
  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | out-null  
  
$server =  New-Object ("Microsoft.SqlServer.Management.SMO.Server") ($servername)  
$scripter = New-Object ("Microsoft.SqlServer.Management.SMO.Scripter") ($server)  
  
## initialize table variable  
$tableUrn = $server.Databases[$database].Tables[$object, $schema]  
if($tableUrn.Count -eq 0)  
{  
   throw "Table or database not found"  
}  
  
## initialize scripting object  
$scriptingOptions = New-Object ("Microsoft.SqlServer.Management.SMO.ScriptingOptions")   
$scriptingOptions.Permissions = $True  
$scriptingOptions.ScriptDrops = $True  
  
$scripter.Options = $scriptingOptions;  
  
write-host "(1) Scripting SELECT INTO $object_heap for table [$object] to 1_copy_to_heap_for_$schema`_$object.sql"  
Echo "SELECT * INTO $schema.$object_heap FROM $schema.$object WITH (SNAPSHOT)" | Out-File "1_copy_to_heap_$schema`_$object.sql";  
write-host "--done--"  
write-host ""  
  
write-host "(2) Scripting DROP for procs schema-bound to [$object] 2_drop_procs_$schema`_$object.sql"  
## query referencing schema-bound objects  
$dt = $server.Databases[$database].ExecuteWithResults("select r.referencing_schema_name, r.referencing_entity_name  
from sys.dm_sql_referencing_entities ('$schema.$object', 'OBJECT') as r join sys.sql_modules m on r.referencing_id=m.object_id  
where r.is_caller_dependent = 0 and m.is_schema_bound=1;")  
  
## initialize out file  
Echo "" | Out-File "2_drop_procs_$schema`_$object.sql"  
## loop through schema-bound objects  
Foreach ($t in $dt.Tables)  
{    
   Foreach ($r in $t.Rows)  
   {    
      ## script object   
      $so =  $server.Databases[$database].StoredProcedures[$r[1], $r[0]]  
      $scripter.Script($so) | Out-File -Append "2_drop_procs_$schema`_$object.sql"  
   }  
}  
write-host "--done--"  
write-host ""  
  
write-host "(3) Scripting DROP table for [$object] to 3_drop_table_$schema`_$object.sql"  
$scripter.Script($tableUrn) | Out-File "3_drop_table_$schema`_$object.sql";  
write-host "--done--"  
write-host ""  
  
## now script creates  
$scriptingOptions.ScriptDrops = $False  
  
write-host "(4) Scripting CREATE table and permissions for [$object] to !please_edit_4_create_table_$schema`_$object.sql"  
write-host "***** rename this script to 4_create_table.sql after completing the updates to the schema"  
$scripter.Script($tableUrn) | Out-File "!please_edit_4_create_table_$schema`_$object.sql";  
write-host "--done--"  
write-host ""  
  
write-host "(5) Scripting INSERT INTO table from heap and UPDATE STATISTICS for [$object] to 5_copy_from_heap_$schema`_$object.sql"  
write-host "[update this script if columns are added to or removed from the table]"  
Echo "INSERT INTO [$schema].[$object] SELECT * FROM [$schema].[$object_heap]; UPDATE STATISTICS [$schema].[$object] WITH FULLSCAN, NORECOMPUTE" | Out-File "5_copy_from_heap_$schema`_$object.sql";  
write-host "--done--"  
write-host ""  
  
write-host "(6) Scripting CREATE PROC and permissions for procedures schema-bound to [$object] to 6_create_procs_$schema`_$object.sql"  
write-host "[update the procedure definitions if columns are renamed or removed]"  
## initialize out file  
Echo "" | Out-File "6_create_procs_$schema`_$object.sql"  
## loop through schema-bound objects  
Foreach ($t in $dt.Tables)  
{    
   Foreach ($r in $t.Rows)  
   {    
      ## script the schema-bound object  
      $so =  $server.Databases[$database].StoredProcedures[$r[1], $r[0]]  
      foreach($s in $scripter.Script($so))  
        {  
            Echo $s | Out-File -Append "6_create_procs_$schema`_$object.sql"  
            Echo "GO" | Out-File -Append "6_create_procs_$schema`_$object.sql"  
        }  
   }  
}  
write-host "--done--"  
write-host ""  
  
write-host "(7) Scripting DROP $object_heap to 7_drop_heap_$schema`_$object.sql"  
Echo "DROP TABLE $schema.$object_heap" | Out-File "7_drop_heap_$schema`_$object.sql";  
write-host "--done--"  
write-host ""  
  
```  
  
 次の PowerShell スクリプトでは、前のサンプルでスクリプトを作成したスキーマの変更を実行します。 このスクリプトは、テーブルを引数として受け取り、このテーブルや関連付けられたストアド プロシージャ用に生成されたスキーマ変更スクリプトを実行します。  
  
 使用法: execute_schema_change.ps1 *server_name * * db_name`schema_name`table_name*  
  
```tsql  
# stop execution once an error occurs  
$ErrorActionPreference="Stop"  
  
if($args.Count -le 3)  
{  
   throw "Usage execute_schema_change.ps1 server_name db_name schema_name table_name"  
}  
  
$servername = $args[0]  
$database = $args[1]  
$schema = $args[2]  
$object = $args[3]  
  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | out-null  
  
$server =  New-Object ("Microsoft.SqlServer.Management.SMO.Server") ($servername)  
$database = $server.Databases[$database]  
$table = $database.Tables[$object, $schema]  
if($table.Count -eq 0)  
{  
   throw "Table or database not found"  
}  
  
$1 = Get-Item "1_copy_to_heap_$schema`_$object.sql"  
$2 = Get-Item "2_drop_procs_$schema`_$object.sql"  
$3 = Get-Item "3_drop_table_$schema`_$object.sql"  
$4 = Get-Item "4_create_table_$schema`_$object.sql"  
$5 = Get-Item "5_copy_from_heap_$schema`_$object.sql"  
$6 = Get-Item "6_create_procs_$schema`_$object.sql"  
$7 = Get-Item "7_drop_heap_$schema`_$object.sql"  
  
write-host "(1) Running SELECT INTO heap for table [$object] from 1_copy_to_heap_for_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $1.OpenText().ReadToEnd())")  
write-host "--done--"  
write-host ""  
  
write-host "(2) Running DROP for procs schema-bound from [$object] 2_drop_procs_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $2.OpenText().ReadToEnd())")  
write-host "--done--"  
write-host ""  
  
write-host "(3) Running DROP table for [$object] to 4_drop_table_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $3.OpenText().ReadToEnd())")  
write-host "--done--"  
write-host ""  
  
write-host "(4) Running CREATE table and permissions for [$object] from 4_create_table_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $4.OpenText().ReadToEnd())")  
write-host "--done--"  
write-host ""  
  
write-host "(5) Running INSERT INTO table from heap for [$object] and UPDATE STATISTICS from 5_copy_from_heap_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $5.OpenText().ReadToEnd())")  
write-host "--done--"  
write-host ""  
  
write-host "(6) Running CREATE PROC and permissions for procedures schema-bound to [$object] from 6_create_procs_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $6.OpenText().ReadToEnd())")  
write-host "--done--"  
write-host ""  
  
write-host "(7) Running DROP heap from 7_drop_heap_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $7.OpenText().ReadToEnd())")  
write-host "--done--"  
write-host ""  
```  
  
## <a name="see-also"></a>参照  
 [メモリ最適化テーブル](memory-optimized-tables.md)  
  
  
