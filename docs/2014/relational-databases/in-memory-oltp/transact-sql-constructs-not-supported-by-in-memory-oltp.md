---
title: インメモリ OLTP でサポートされていない Transact-SQL の構造 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e3f8009c-319d-4d7b-8993-828e55ccde11
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fe4388cff478cf3d8f8fd773c8b0926793b0cc0b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37258858"
---
# <a name="transact-sql-constructs-not-supported-by-in-memory-oltp"></a>インメモリ OLTP でサポートされていない Transact-SQL の構造
  メモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャでは、ディスク ベース テーブルおよび解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャでサポートされる完全な [!INCLUDE[tsql](../../includes/tsql-md.md)] 領域はサポートされません。 サポートされていない機能を使用しようとすると、サーバーはエラーを返します。  
  
 エラー メッセージのテキストには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの種類 (機能、操作、オプションなど) と、機能名または [!INCLUDE[tsql](../../includes/tsql-md.md)] キーワード名が含まれます。 ほとんどのサポートされていない機能では、サポートされていない機能を示すエラー メッセージ テキストと共にエラー 10794 が返されます。 次の表に、エラー メッセージのテキストに表示される可能性がある [!INCLUDE[tsql](../../includes/tsql-md.md)] の機能およびキーワードと、エラーを解決するための修正措置を示します。  
  
 メモリ最適化テーブルとネイティブ コンパイル ストアド プロシージャでサポートされる機能の詳細については、次のトピックを参照してください。  
  
-   [ネイティブ コンパイル ストアド プロシージャの移行に関する問題](migration-issues-for-natively-compiled-stored-procedures.md)  
  
-   [Transact-SQL によるインメモリ OLTP のサポート](transact-sql-support-for-in-memory-oltp.md)  
  
-   [サポートされる SQL Server の機能](unsupported-sql-server-features-for-in-memory-oltp.md)  
  
-   [ネイティブ コンパイル ストアド プロシージャ](../in-memory-oltp/natively-compiled-stored-procedures.md)  
  
## <a name="databases-that-use-in-memory-oltp"></a>インメモリ OLTP を使用するデータベース  
 次の表は、インメモリ OLTP データベースに関するエラーのメッセージ テキストに含まれる [!INCLUDE[tsql](../../includes/tsql-md.md)] 機能とキーワードを示します。  
  
|型|名前|解決策|  
|----------|----------|----------------|  
|オプション|AUTO_CLOSE|データベース オプション AUTO_CLOSE=ON は、MEMORY_OPTIMIZED_DATA ファイル グループのあるデータベースではサポートされていません。|  
|オプション|ATTACH_REBUILD_LOG|CREATE データベース オプション ATTACH_REBUILD_LOG は、MEMORY_OPTIMIZED_DATA ファイル グループのあるデータベースではサポートされていません。|  
|機能|DATABASE SNAPSHOT|データベース スナップショットの作成は、MEMORY_OPTIMIZED_DATA ファイル グループのあるデータベースではサポートされていません。|  
|機能|sync_method 'database snapshot' または 'database snapshot character' の使用によるレプリケーション|sync_method 'database snapshot' または 'database snapshot character' の使用によるレプリケーションは、MEMORY_OPTIMIZED_DATA ファイル グループのあるデータベースではサポートされていません。|  
|機能|DBCC CHECKDB<br /><br /> DBCC CHECKTABLE|DBCC CHECKDB では、データベース内のメモリ最適化テーブルがスキップされます。<br /><br /> DBCC CHECKTABLE は、メモリ最適化テーブルで失敗します。|  
  
## <a name="memory-optimized-tables"></a>メモリ最適化テーブル  
 次の表に、メモリ最適化テーブルに関連したエラー メッセージのテキストに表示される可能性がある [!INCLUDE[tsql](../../includes/tsql-md.md)] の機能およびキーワードと、エラーを解決するための修正措置を示します。  
  
|型|名前|解決策|  
|----------|----------|----------------|  
|機能|ON|メモリ最適化テーブルをファイル グループまたはパーティション構成に配置できません。 `CREATE TABLE` ステートメントから ON 句を削除します。|  
|データ型|*データ型名*|指示されたデータ型はサポートされていません。 サポートされているデータ型に置き換えます。 詳細については、次を参照してください。 [Supported Data Types](supported-data-types-for-in-memory-oltp.md)します。|  
|機能|計算列|計算列は、メモリ最適化テーブルではサポートされていません。 計算列を削除、`CREATE TABLE`ステートメント。|  
|機能|のレプリケーション|レプリケーションはメモリ最適化テーブルではサポートされていません。|  
|機能|FILESTREAM|FILESTREAM ストレージは、メモリ最適化テーブルのサポートされた列ではありません。 削除、`FILESTREAM`列定義からのキーワード。|  
|機能|SPARSE|メモリ最適化テーブルの列を SPARSE として定義することはできません。 削除、`SPARSE`列定義からのキーワード。|  
|機能|ROWGUIDCOL|ROWGUIDCOL オプションはメモリ最適化テーブルの列ではサポートされていません。 削除、`ROWGUIDCOL`列定義からのキーワード。|  
|機能|FOREIGN KEY|FOREIGN KEY 制約は、メモリ最適化テーブルではサポートされていません。 テーブル定義から制約を削除します。<br /><br /> 制約がサポートの不足を軽減する方法については、次を参照してください。[移行を確認し、外部キー制約](../../database-engine/migrating-check-and-foreign-key-constraints.md)します。|  
|機能|CHECK|CHECK 制約は、メモリ最適化テーブルではサポートされていません。 テーブル定義から制約を削除します。<br /><br /> 制約がサポートの不足を軽減する方法については、次を参照してください。[移行を確認し、外部キー制約](../../database-engine/migrating-check-and-foreign-key-constraints.md)します。|  
|機能|UNIQUE|UNIQUE 制約は、メモリ最適化テーブルではサポートされていません。 テーブル定義から制約を削除します。<br /><br /> 制約がサポートの不足を軽減する方法については、次を参照してください。[移行を確認し、外部キー制約](../../database-engine/migrating-check-and-foreign-key-constraints.md)します。|  
|機能|COLUMNSTORE|COLUMNSTORE インデックスは、メモリ最適化テーブルでサポートされていません。 代わりに、NONCLUSTERED インデックスまたは NONCLUSTERED HASH インデックスを指定します。|  
|機能|クラスター化インデックス|非クラスター化インデックスを指定します。 主キー インデックスの場合は `PRIMARY KEY NONCLUSTERED [HASH]` を指定する必要があります。|  
|機能|1252 以外のコード ページ|メモリ最適化テーブルの `char` および `varchar` データ型の列では、コード ページ 1252 を使用する必要があります。 (var)char の代わりに n(var)char を使用するか、コード ページ 1252 で照合順序を使用します (たとえば、Latin1_General_BIN2)。 詳細については、「 [Collations and Code Pages](../../database-engine/collations-and-code-pages.md)」を参照してください。|  
|機能|DDL 内部トランザクション|メモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャは、ユーザー トランザクションのコンテキストで作成または削除できません。 トランザクションを開始せず、CREATE または DROP ステートメントを実行する前にセッション設定 IMPLICIT_TRANSACTION を OFF に設定していることを確認します。|  
|機能|DDL トリガー|DDL 操作のサーバーまたはデータベース トリガーがある場合は、メモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャを作成または削除できません。 CREATE/DROP TABLE および CREATE/DROP PROCEDURE のサーバーおよびデータベース トリガーを削除します。|  
|機能|EVENT NOTIFICATION|DDL 操作のサーバーまたはデータベース イベント通知がある場合は、メモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャを作成または削除できません。 CREATE TABLE または DROP TABLE および CREATE PROCEDURE または DROP PROCEDURE のサーバーおよびデータベース イベント通知を削除します。|  
|機能|FileTable|メモリ最適化テーブルをファイル テーブルとして作成できません。 引数 `AS FileTable` を `CREATE TABLE` ステートメントから削除してください。|  
|演算|主キー列の更新|メモリ最適化テーブルおよびテーブル型の主キー列を更新できません。 主キーを更新する必要がある場合は、古い行を削除し、更新された主キーで新しい行を挿入します。|  
|演算|CREATE INDEX|メモリ最適化テーブルのインデックスは、`CREATE TABLE` ステートメントでインラインで指定する必要があります。 メモリ最適化テーブルにインデックスを追加するには、テーブルを削除し、新しいインデックスの指定を含むテーブルを再作成します。|  
|演算|ALTER TABLE|メモリ最適化テーブルの変更はサポートされていません。 テーブルを削除し、更新されたテーブル定義を使用して再作成します。|  
|演算|CREATE FULLTEXT INDEX|フルテキスト インデックスは、メモリ最適化テーブルでサポートされていません。|  
|演算|スキーマの変更|メモリ最適化テーブルとネイティブ コンパイル ストアド プロシージャでは、`sp_rename` などのスキーマの変更はサポートされません。<br /><br /> テーブルの名前変更などのスキーマ変更を試みると、エラー 12320 (名前変更などスキーマ バージョンへの変更を要する操作は、メモリ最適化テーブルでサポートされない) が生成されます。<br /><br /> スキーマを変更するには、テーブルまたはプロシージャを削除し、更新された定義を使用して再作成します。|  
|演算|CREATE TRIGGER|メモリ最適化テーブルではトリガーはサポートされません。|  
|演算|TRUNCATE TABLE|メモリ最適化テーブルでは TRUNCATE 操作はサポートされません。 テーブルからすべての行を削除するを使用してすべての行を削除`DELETE FROM`*テーブル*かを削除して、テーブルを再作成します。|  
|演算|ALTER AUTHORIZATION|既存のメモリ最適化テーブルまたはネイティブ コンパイル ストアド プロシージャでの所有者の変更はサポートされていません。 所有者を変更するには、テーブルまたはプロシージャを削除した後、再作成します。|  
|演算|ALTER SCHEMA|既存のメモリ最適化テーブルまたはネイティブ コンパイル ストアド プロシージャでのスキーマの変更はサポートされていません。 スキーマを変更するには、テーブルまたはプロシージャを削除した後、再作成します。|  
|演算|DBCC CHECKTABLE|DBCC CHECKTABLE はメモリ最適化テーブルではサポートされていません。|  
|機能|ANSI_PADDING OFF|セッション オプション`ANSI_PADDING`テーブルまたはネイティブ コンパイル ストアド プロシージャをメモリ最適化を作成するときにあります。 CREATE ステートメントを実行する前に、`SET ANSI_PADDING ON` を実行します。|  
|オプション|DATA_COMPRESSION|データ圧縮は、メモリ最適化テーブルではサポートされていません。 テーブル定義からオプションを削除します。|  
|機能|DTC|メモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャは、分散トランザクションからアクセスできません。 代わりに SQL トランザクションを使用してください。|  
|機能|複数のアクティブな結果セット (MARS)|複数のアクティブな結果セット (MARS) は、メモリ最適化テーブルではサポートされていません。 また、このエラーは、リンク サーバーの使用を示します。 リンク サーバーは MARS を使用できます。 リンク サーバーは、メモリ最適化テーブルでサポートされていません。 代わりに、メモリ最適化テーブルをホストするサーバーとデータベースに直接接続してください。|  
|演算|MERGE のターゲットとしてのメモリ最適化テーブル|メモリ最適化テーブルを `MERGE` 操作の対象にすることはできません。 使用`INSERT`、 `UPDATE`、または`DELETE`ステートメント代わりにします。|  
  
## <a name="indexes-on-memory-optimized-tables"></a>メモリ最適化テーブルのインデックス  
 次の表に、メモリ最適化テーブルのインデックスに関連したエラー メッセージのテキストに表示される可能性がある [!INCLUDE[tsql](../../includes/tsql-md.md)] の機能およびキーワードと、エラーを解決するための修正措置を示します。  
  
|型|名前|解決策|  
|----------|----------|----------------|  
|機能|フィルター選択されたインデックス|フィルター選択されたインデックスは、メモリ最適化テーブルでサポートされていません。 省略、`WHERE`インデックスの指定から句。|  
|機能|UNIQUE|一意インデックスは、メモリ最適化テーブルではサポートされていません。 引数 `UNIQUE` をインデックスの指定から削除します。|  
|機能|NULL 値を許容する列|メモリ最適化テーブルのインデックスのキー内のすべての列を `NOT NULL` として指定する必要があります。 インデックス キー内のすべての列に `NOT NULL` 制約を含めます。|  
|機能|非 BIN2 照合順序|メモリ最適化インデックスのキー内のすべての文字型列を、BIN2 照合順序を使用して宣言する必要があります。 列定義で照合順序を設定するには、`COLLATE` 句を使用します。 詳細については、「 [Collations and Code Pages](../../database-engine/collations-and-code-pages.md)」を参照してください。|  
|機能|[付加列]|付加列の指定は、メモリ最適化テーブルにとって必須ではありません。 メモリ最適化テーブルのすべての列は、各メモリ最適化インデックスに暗黙的に含まれています。|  
|演算|ALTER INDEX|メモリ最適化テーブルのインデックスの変更はサポートされていません。 代わりに、テーブルを削除し、更新されたインデックスの指定を使用して再作成します。|  
|演算|DROP INDEX|メモリ最適化テーブルのインデックスの削除はサポートされていません。 代わりに、テーブルを削除し、必要なインデックスで再作成します。|  
|インデックス オプション|*インデックス オプション*|指定したインデックス オプションはメモリ最適化テーブルのインデックスではサポートされていません。 オプションをインデックスの指定から削除してください。|  
  
## <a name="nonclustered-hash-indexes"></a>非クラスター化ハッシュ インデックス  
 次の表に、非クラスター化ハッシュ インデックスに関連したエラー メッセージのテキストに表示される可能性がある [!INCLUDE[tsql](../../includes/tsql-md.md)] の機能およびキーワードと、エラーを解決するための修正措置を示します。  
  
|型|名前|解決策|  
|----------|----------|----------------|  
|オプション|ASC/DESC|非クラスター化ハッシュ インデックスは順序付けされません。 インデックス キーの指定からキーワード `ASC` および `DESC` を削除します。|  
  
## <a name="natively-compiled-stored-procedures"></a>ネイティブ コンパイル ストアド プロシージャ  
 次の表に、ネイティブ コンパイル ストアド プロシージャに関連したエラー メッセージのテキストに表示される可能性がある [!INCLUDE[tsql](../../includes/tsql-md.md)] の機能およびキーワードと、エラーを解決するための修正措置を示します。  
  
|型|機能|解決策|  
|----------|-------------|----------------|  
|機能|インライン テーブル変数|テーブル型は、変数宣言を使用してインラインで宣言できません。 テーブル型を使用して明示的に宣言する必要があります、`CREATE TYPE`ステートメント。|  
|機能|カーソル|カーソルは、ネイティブ コンパイル ストアド プロシージャではサポートされていません。<br /><br /> -クライアントからプロシージャを実行するときに、カーソル API ではなく RPC を使用します。 ODBC で、[!INCLUDE[tsql](../../includes/tsql-md.md)] のステートメント `EXECUTE` を避け、代わりにプロシージャの名前を直接指定します。<br /><br /> -からプロシージャを実行するときに、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチまたは別のストアド プロシージャ、ネイティブ コンパイル ストアド プロシージャでカーソルを使用しないでください。<br /><br /> -、カーソルを使用するのではなく、ネイティブ コンパイル ストアド プロシージャの作成は、セットベースのロジックを使用する場合または`WHILE`ループします。|  
|機能|定数以外のパラメーターの既定値|ネイティブ コンパイル ストアド プロシージャのパラメーターで既定値を使用する場合、値は定数にする必要があります。 パラメーター宣言からワイルドカードを削除します。|  
|機能|EXTERNAL|CLR ストアド プロシージャをネイティブでコンパイルすることはできません。 CREATE PROCEDURE ステートメントから AS EXTERNAL 句または NATIVE_COMPILATION オプションを削除します。|  
|機能|番号付きストアド プロシージャ|ネイティブ コンパイル ストアド プロシージャには番号を付けられません。 削除、 `;`*数*から、`CREATE PROCEDURE`ステートメント。|  
|機能|複数行の INSERT... VALUES ステートメント|ネイティブ コンパイル ストアド プロシージャでは、同じ `INSERT` ステートメントを使用して複数行を挿入できません。 作成`INSERT`各行のステートメント。|  
|機能|共通テーブル式 (CTE)|共通テーブル式 (CTE) は、ネイティブ コンパイル ストアド プロシージャでサポートされません。 クエリを書き直します。|  
|機能|サブクエリ|サブクエリ (クエリ内に入れ子になっているクエリ) はサポートされていません。 クエリを書き直します。|  
|機能|COMPUTE|`COMPUTE` 句はサポートされていません。 クエリから削除します。|  
|機能|SELECT INTO|`INTO` 句は `SELECT` ステートメントではサポートされていません。 としてクエリを書き直します`INSERT INTO`*テーブル*`SELECT`します。|  
|機能|OUTPUT|`OUTPUT` 句はサポートされていません。 クエリから削除します。|  
|機能|不完全な挿入列リスト|`INSERT` ステートメントでは、テーブルのすべての列に値を指定する必要があります。|  
|機能|*関数*|ネイティブ コンパイル ストアド プロシージャ内では、組み込み関数はサポートされません。 ストアド プロシージャから関数を削除します。 サポートされる組み込み関数の詳細については、次を参照してください。 [Natively Compiled Stored Procedures](../in-memory-oltp/natively-compiled-stored-procedures.md)します。|  
|機能|CASE|ネイティブ コンパイル ストアド プロシージャ内のクエリでは、`CASE` ステートメントはサポートされません。 各ケースのクエリを作成します。 詳細については、次を参照してください。 [、CASE ステートメントを実装する](implementing-a-case-expression-in-a-natively-compiled-stored-procedure.md)します。|  
|機能|ユーザー定義関数|ユーザー定義関数はネイティブ コンパイル ストアド プロシージャ内で使用できません。 プロシージャの定義から関数への参照を削除します。|  
|機能|ユーザー定義集計|ユーザー定義集計関数はネイティブ コンパイル ストアド プロシージャ内で使用できません。 プロシージャから関数への参照を削除します。|  
|機能|ブラウズ モード メタデータ|ネイティブ コンパイル ストアド プロシージャでは、ブラウズ モード メタデータはサポートされていません。 セッション オプション `NO_BROWSETABLE` を OFF に設定します。|  
|機能|FROM 句と DELETE|ネイティブ コンパイル ストアド プロシージャ内でテーブル ソースを指定した `FROM` ステートメントに対して `DELETE` 句はサポートされません。<br /><br /> `DELETE` `FROM`をから削除するテーブルを示すために使用した場合、句はサポートされています。|  
|機能|FROM 句と UPDATE|ネイティブ コンパイル ストアド プロシージャ内の `FROM` ステートメントに対して `UPDATE` 句はサポートされません。|  
|機能|一時プロシージャ|一時ストアド プロシージャはネイティブでコンパイルできません。 永続的なネイティブ コンパイル ストアド プロシージャまたは解釈された一時 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを作成します。|  
|分離レベル|READ UNCOMMITTED|ネイティブ コンパイル ストアド プロシージャに対して分離レベル READ UNCOMMITTED はサポートされません。 SNAPSHOT など、サポートされる分離レベルを使用します。|  
|分離レベル|READ COMMITTED|ネイティブ コンパイル ストアド プロシージャに対して分離レベル READ UNCOMMITTED はサポートされません。 SNAPSHOT など、サポートされる分離レベルを使用します。|  
|機能|一時テーブル|tempdb 内のテーブルはネイティブ コンパイル ストアド プロシージャ内では使用できません。 代わりに、テーブル変数または DURABILITY=SCHEMA_ONLY のメモリ最適化テーブルを使用します。|  
|機能|MARS|複数のアクティブな結果セット (MARS) は、ネイティブ コンパイル ストアド プロシージャではサポートされていません。 また、このエラーは、リンク サーバーの使用を示します。 リンク サーバーは MARS を使用できます。 リンク サーバーは、ネイティブ コンパイル ストアド プロシージャではサポートされていません。 代わりに、ネイティブ コンパイル ストアド プロシージャをホストするサーバーとデータベースに直接接続します。|  
|機能|DTC|メモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャは、分散トランザクションからアクセスできません。 代わりに SQL トランザクションを使用してください。|  
|機能|非 BIN2 照合順序|ネイティブ コンパイル ストアド プロシージャの文字列の比較、並べ替え、その他の操作には、BIN2 照合順序を使用する必要があります。 COLLATE 句を使用するか、適切な照合順序で列と変数を使用します。 詳細については、「 [Collations and Code Pages](../../database-engine/collations-and-code-pages.md)」を参照してください。|  
|機能|SC 照合順序を使用した文字列の切り捨て|`_SC` 照合順序を使用した文字列は、UTF-16 エンコードを使用します。 n(var)char 値を短い長さの n(var)char 値に変換すると、切り捨てが行われます。 これは、ネイティブ コンパイル ストアド プロシージャの UTF-16 値ではサポートされていません。 UTF-16 文字列の切り捨てをしないでください。|  
|機能|EXECUTE WITH RECOMPILE|オプション`WITH RECOMPILE`ネイティブ コンパイル ストアド プロシージャはサポートされていません。|  
|機能|SC 照合順序の引数を持つ LEN および SUBSTRING|_SC 照合順序を使用した文字列では、UTF-16 エンコードが使用されます。 組み込み関数 LEN および SUBSTRING (ネイティブ コンパイル ストアド プロシージャ内で使用された場合) は、UTF-16 エンコードをサポートしていません。 別の照合順序を使用するか、これらの関数の使用を回避します。|  
|機能|専用管理者接続からの実行|ネイティブ コンパイル ストアド プロシージャでは、専用管理者接続 (DAC) から実行することはできません。 通常の接続を使用してください。|  
|演算|ALTER PROCEDURE|ネイティブ コンパイル ストアド プロシージャは変更できません。 プロシージャの定義を変更するには、ストアド プロシージャを削除して再作成します。|  
|演算|セーブポイント (savepoint)|ネイティブ コンパイル ストアド プロシージャは、アクティブなセーブポイントを含むトランザクションから呼び出すことはできません。 トランザクションからセーブポイントを削除します。|  
|演算|ALTER AUTHORIZATION|既存のメモリ最適化テーブルまたはネイティブ コンパイル ストアド プロシージャでの所有者の変更はサポートされていません。 所有者を変更するには、テーブルまたはプロシージャを削除した後、再作成します。|  
|演算子|OPENROWSET|この演算子はサポートされていません。 削除`OPENROWSET`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|OPENQUERY|この演算子はサポートされていません。 削除`OPENQUERY`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|OPENDATASOURCE|この演算子はサポートされていません。 削除`OPENDATASOURCE`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|OPENXML|この演算子はサポートされていません。 削除`OPENXML`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|CONTAINSTABLE|この演算子はサポートされていません。 削除`CONTAINSTABLE`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|FREETEXTTABLE|この演算子はサポートされていません。 削除`FREETEXTTABLE`からネイティブ コンパイル ストアド プロシージャ。|  
|機能|テーブル値関数|テーブル値関数はネイティブ コンパイル ストアド プロシージャから参照できません。 この制限に関する対処方法の 1 つは、プロシージャの本体にテーブル値関数のロジックを追加することです。|  
|演算子|CHANGETABLE|この演算子はサポートされていません。 削除`CHANGETABLE`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|GOTO|この演算子はサポートされていません。 WHILE など他の構造を使用します。|  
|演算子|EXECUTE, INSERT EXEC|入れ子のネイティブ コンパイル ストアド プロシージャはサポートされていません。 必要な操作は、ストアド プロシージャ定義の一部としてインラインで指定できます。|  
|演算子|OFFSET|この演算子はサポートされていません。 削除`OFFSET`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|UNION|この演算子はサポートされていません。 削除`UNION`からネイティブ コンパイル ストアド プロシージャ。 単一の結果セットへのいくつかの結果セットの結合は、テーブル変数を使用しても実行できます。|  
|演算子|INTERSECT|この演算子はサポートされていません。 削除`INTERSECT`からネイティブ コンパイル ストアド プロシージャ。 場合によっては INNER JOIN を使用して同じ結果を得ることができます。|  
|演算子|EXCEPT|この演算子はサポートされていません。 削除`EXCEPT`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|OUTER JOIN|この演算子はサポートされていません。 削除`OUTER JOIN`からネイティブ コンパイル ストアド プロシージャ。 詳細については、次を参照してください。 [Outer Join を実装する](implementing-an-outer-join.md)します。|  
|演算子|APPLY|この演算子はサポートされていません。 削除`APPLY`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|PIVOT|この演算子はサポートされていません。 削除`PIVOT`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|UNPIVOT|この演算子はサポートされていません。 削除`UNPIVOT`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|OR, IN|ネイティブ コンパイル ストアド プロシージャ内のクエリの WHERE 句では、論理和 (OR, IN) はサポートされません。 各ケースのクエリを作成します。|  
|演算子|CONTAINS|この演算子はサポートされていません。 削除`CONTAINS`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|FREETEXT|この演算子はサポートされていません。 削除`FREETEXT`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|NOT|この演算子はサポートされていません。 削除`NOT`からネイティブ コンパイル ストアド プロシージャ。 場合によっては、`NOT` を非等値に置き換えることができます。 たとえば、`NOT a=b` は `a!=b` に置き換えることができます。|  
|演算子|TSEQUAL|この演算子はサポートされていません。 削除`TSEQUAL`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|LIKE|この演算子はサポートされていません。 削除`LIKE`からネイティブ コンパイル ストアド プロシージャ。|  
|演算子|NEXT VALUE FOR|シーケンスは、ネイティブ コンパイル ストアド プロシージャ内で参照できません。 解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して値を取得し、それをネイティブ コンパイル ストアド プロシージャに渡します。 詳細については、「 [メモリ最適化テーブルへの IDENTITY の実装](implementing-identity-in-a-memory-optimized-table.md)」を参照してください。|  
|SET オプション|*オプション*|SET オプションは、ネイティブ コンパイル ストアド プロシージャ内で変更できません。 特定のオプションは BEGIN ATOMIC ステートメントで設定できます。 詳細については、「 [Natively Compiled Stored Procedures](../in-memory-oltp/natively-compiled-stored-procedures.md)」の ATOMIC ブロックに関するセクションを参照してください。|  
|オペランド|TABLESAMPLE|この演算子はサポートされていません。 削除`TABLESAMPLE`からネイティブ コンパイル ストアド プロシージャ。|  
|オプション|RECOMPILE|ネイティブ コンパイル ストアド プロシージャは、作成時にコンパイルされます。 ネイティブ コンパイル ストアド プロシージャを再コンパイルするには、一度削除して再作成します。 削除`RECOMPILE`プロシージャの定義からです。|  
|オプション|ENCRYPTION|このオプションはサポートされていません。 削除`ENCRYPTION`プロシージャの定義からです。|  
|オプション|FOR REPLICATION|ネイティブ コンパイル ストアド プロシージャはレプリケーション用に作成できません。 プロシージャの定義から `FOR REPLICATION` を削除します。|  
|オプション|FOR XML|このオプションはサポートされていません。 削除`FOR XML`からネイティブ コンパイル ストアド プロシージャ。|  
|オプション|FOR BROWSE|このオプションはサポートされていません。 削除`FOR BROWSE`からネイティブ コンパイル ストアド プロシージャ。|  
|結合ヒント|HASH、MERGE|ネイティブ コンパイル ストアド プロシージャは、入れ子になったループ結合のみをサポートします。 HASH および MERGE 結合はサポートされていません。 結合ヒントを削除します。|  
|クエリ ヒント|*クエリ ヒント*|このクエリ ヒントはネイティブ コンパイル ストアド プロシージャ内にありません。 サポートされているクエリ ヒントについては、「[クエリ ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query)」を参照してください。|  
|オプション|DISTINCT|このオプションはサポートされていません。 ネイティブ コンパイル ストアド プロシージャのクエリから `DISTINCT` を削除します。|  
|オプション|PERCENT|このオプションはサポートされていません`TOP`句。 ネイティブ コンパイル ストアド プロシージャのクエリから `PERCENT` を削除します。|  
|オプション|WITH TIES|このオプションはサポートされていません`TOP`句。 ネイティブ コンパイル ストアド プロシージャのクエリから `WITH TIES` を削除します。|  
|集計関数|*集計関数*|この句はサポートされていません。 ネイティブ コンパイル ストアド プロシージャ内の集計関数の詳細については、「 [Natively Compiled Stored Procedures](../in-memory-oltp/natively-compiled-stored-procedures.md)」を参照してください。|  
|順位付け関数|*順位付け関数*|順位付け関数は、ネイティブ コンパイル ストアド プロシージャではサポートされていません。 プロシージャの定義から削除します。|  
|機能|*関数*|この関数はサポートされません。 ネイティブ コンパイル ストアド プロシージャから削除します。|  
|ステートメントから削除してください。|*ステートメント*|このステートメントはサポートされていません。 ネイティブ コンパイル ストアド プロシージャから削除します。|  
|機能|バイナリおよび文字列で使用される MIN と MAX|集計関数 `MIN` および `MAX` は、ネイティブ コンパイル ストアド プロシージャ内の文字やバイナリ文字列値に使用できません。|  
|機能|集計関数なしの GROUP BY|ネイティブ コンパイル ストアド プロシージャでは、クエリに `GROUP BY` 句がある場合、このクエリの SELECT 句または HAVING 句で集計関数も使用する必要があります。 クエリに集計関数を追加します。|  
|機能|GROUP BY ALL|ALL は、ネイティブ コンパイル ストアド プロシージャ内の GROUP BY 句では使用できません。 GROUP BY 句から ALL を削除します。|  
|機能|GROUP BY ()|空のリストによる GROUP BY はサポートされていません。 GROUP BY 句を削除するか、グループ化リストに列を含めます。|  
|機能|ROLLUP|`ROLLUP` は、ネイティブ コンパイル ストアド プロシージャ内の `GROUP BY` 句では使用できません。 削除`ROLLUP`プロシージャの定義からです。|  
|機能|CUBE|`CUBE` は、ネイティブ コンパイル ストアド プロシージャ内の `GROUP BY` 句では使用できません。 削除`CUBE`プロシージャの定義からです。|  
|機能|GROUPING SETS|`GROUPING SETS` は、ネイティブ コンパイル ストアド プロシージャ内の `GROUP BY` 句では使用できません。 削除`GROUPING SETS`プロシージャの定義からです。|  
|機能|BEGIN TRANSACTION、COMMIT TRANSACTION、ROLLBACK TRANSACTION|ATOMIC ブロックを使用してトランザクションおよびエラー処理を制御します。 詳細については、「 [Atomic Blocks](atomic-blocks-in-native-procedures.md)」を参照してください。|  
|機能|インライン テーブル変数の宣言。|テーブル変数は、明示的に定義されたメモリ最適化テーブル型を参照する必要があります。 メモリ最適化テーブル型を作成し、(インライン型を指定する変わりに) 変数の宣言でその型を使用します。|  
|機能|sp_recompile|ネイティブ コンパイル ストアド プロシージャの再コンパイルはサポートされていません。 プロシージャを削除および再作成します。|  
|機能|EXECUTE AS CALLER|`EXECUTE AS` 句は必須です。 ただし `EXECUTE AS CALLER` はサポートされていません。 使用`EXECUTE AS OWNER`、 `EXECUTE AS`*ユーザー*、または`EXECUTE AS SELF`します。|  
|機能|ディスク ベース テーブル|ディスク ベース テーブルには、ネイティブ コンパイル ストアド プロシージャからアクセスできません。 ディスク ベース テーブルへの参照をネイティブ コンパイル ストアド プロシージャから削除します。 または、ディスク ベース テーブルをメモリ最適化テーブルに移行します。|  
|機能|ビュー|ビューには、ネイティブ コンパイル ストアド プロシージャからアクセスできません。 ビューではなく、基になるベース テーブルを参照します。|  
|機能|テーブル値関数|テーブル値関数には、ネイティブ コンパイル ストアド プロシージャからアクセスできません。 テーブル値関数への参照をネイティブ コンパイル ストアド プロシージャから削除します。|  
  
## <a name="transactions-that-access-memory-optimized-tables"></a>メモリ最適化テーブルにアクセスするトランザクション  
 次の表に、メモリ最適化テーブルにアクセスするトランザクションに関連したエラー メッセージのテキストに表示される可能性がある [!INCLUDE[tsql](../../includes/tsql-md.md)] の機能およびキーワードと、エラーを解決するための修正措置を示します。  
  
|型|名前|解決策|  
|----------|----------|----------------|  
|機能|セーブポイント (savepoint)|メモリ最適化テーブルにアクセスするトランザクション内での明示的なセーブポイントの作成はサポートされていません。|  
|機能|バインドされたトランザクション|バインドされたセッションは、メモリ最適化テーブルにアクセスするトランザクションに参加できません。 プロシージャを実行する前にセッションをバインドしないでください。|  
|機能|DTC|メモリ最適化テーブルにアクセスするトランザクションは、分散トランザクションにすることはできません。|  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP への移行](migrating-to-in-memory-oltp.md)  
  
  
