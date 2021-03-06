---
title: sp_rename (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 01/09/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_rename_TSQL
- sp_rename
dev_langs:
- TSQL
helpviewer_keywords:
- renaming indexes
- renaming columns
- sp_rename
- renaming tables
ms.assetid: bc3548f0-143f-404e-a2e9-0a15960fc8ed
caps.latest.revision: 54
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 836ef351d2af7e187420b680a90382fc504b9e89
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39563076"
---
# <a name="sprename-transact-sql"></a>sp_rename (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベースでユーザーが作成したオブジェクトの名前を変更します。 このオブジェクトは、テーブル、インデックス、列、別名データ型、または[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]共通言語ランタイム (CLR) ユーザー定義の型。  
  
> [!CAUTION]  
>  オブジェクト名の一部または全部を変更すると、スクリプトおよびストアド プロシージャが壊れる可能性があります。 ストアド プロシージャ、トリガー、ユーザー定義関数、またはビューの名前を変更する場合は、このステートメントを使用しないことをお勧めします。代わりに、オブジェクトを削除して新しい名前で再作成してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_rename [ @objname = ] 'object_name' , [ @newname = ] 'new_name'   
    [ , [ @objtype = ] 'object_type' ]   
```  
  
## <a name="arguments"></a>引数  
 [ @objname =] '*object_name*'  
 ユーザー オブジェクトやデータ型に関する現在の修飾名または非修飾名を指定します。 名前を変更するオブジェクトがテーブルの列の場合*object_name*形式である必要があります*table.column*または*schema.table.column*します。 名前を変更するオブジェクトが、インデックスの場合*object_name*形式である必要があります*table.index*または*schema.table.index*します。 名前を変更するオブジェクトが、制約の場合*object_name*形式である必要があります*schema.constraint*します。  
  
 引用符は、修飾オブジェクトを指定する場合のみ必要です。 データベース名を含む完全修飾名を指定する場合、データベース名は現在のデータベースの名前である必要があります。 *object_name*は**nvarchar (776)**、既定値はありません。  
  
 [ @newname =] '*new_name*'  
 指定したオブジェクトの新しい名前を指定します。 *新しい名前*は、1 つの要素名と識別子の規則に従う必要があります。 *newname*は**sysname**、既定値はありません。  
  
> [!NOTE]  
>  トリガー名の先頭に # または ## は使用できません。  
  
 [ @objtype =] '*object_type*'  
 名前を変更するオブジェクトの種類を指定します。 *object_type*は**varchar (13)**、既定値は null の場合、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|COLUMN|名前を変更する列。|  
|DATABASE|ユーザー定義のデータベース。 データベースの名前を変更する場合は、このオブジェクトの種類が必要です。|  
|INDEX|ユーザー定義のインデックス。 統計のあるインデックスの名前を変更すると、統計の名前も自動的に変更されます。|  
|OBJECT|型の項目の追跡で[sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)します。 たとえば、OBJECT を使用して、制約 (CHECK、FOREIGN KEY、PRIMARY/UNIQUE KEY)、ユーザー テーブル、ルールなどのオブジェクトの名前を変更できます。|  
|STATISTICS|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。<br /><br /> ユーザーによって明示的に作成された統計、作成またはインデックスで暗黙的に作成された統計です。 インデックスの統計の名前を変更すると、インデックスの名前も自動的に変更されます。|  
|USERDATATYPE|A [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)を実行して追加[CREATE TYPE](../../t-sql/statements/create-type-transact-sql.md)または[sp_addtype](../../relational-databases/system-stored-procedures/sp-addtype-transact-sql.md)します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 0 以外の数値 (失敗)  
  
## <a name="remarks"></a>コメント  
 名前を変更できるのは、現在のデータベース内にあるオブジェクトまたはデータ型だけです。 ほとんどのシステム データ型およびシステム オブジェクトの名前は変更できません。  
  
 sp_rename では、PRIMARY KEY (主キー) または UNIQUE (一意) 制約の名前を変更した場合、関連するインデックスの名前も自動的に変更されます。 名前を変更したインデックスが PRIMARY KEY 制約に関連付けられている場合は、sp_rename によって PRIMARY KEY 制約の名前も自動的に変更されます。  
  
 sp_rename は、プライマリおよびセカンダリ XML インデックスの名前を変更する場合に使用できます。  
  
 ストアド プロシージャ、関数、ビュー、またはトリガーは変更されません、対応するオブジェクトの名前の definition 列にあるいずれか、 [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)カタログ ビューまたはを使用して取得、 [object _定義](../../t-sql/functions/object-definition-transact-sql.md)組み込み関数。 したがって、これらのオブジェクトの種類の名前を変更する場合は、sp_rename を使用しないことをお勧めします。 代わりに、オブジェクトを削除して新しい名前で再作成してください。  
  
 テーブルや列などのオブジェクトの名前を変更しても、そのオブジェクトに対する参照は自動的には変更されません。 名前を変更したオブジェクトを参照しているオブジェクトに対しては、手動で変更を加える必要があります。 たとえば、テーブルの列の名前を変更するとき、その列がトリガーで参照されている場合は、新しい列名が反映されるようにトリガーに変更を加える必要があります。 オブジェクトの名前を変更する前には、 [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) を使ってオブジェクトの従属関係を一覧表示できます。  
  
## <a name="permissions"></a>アクセス許可  
 オブジェクト、列、およびインデックスの名前を変更するには、そのオブジェクトに対する ALTER 権限が必要です。 ユーザー定義型の名前を変更するには、その型に対する CONTROL 権限が必要です。 データベースの名前を変更するには、sysadmin 固定サーバー ロールまたは dbcreator 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-renaming-a-table"></a>A. テーブル名を変更する  
 次の例では、 `SalesTerritory` スキーマの `SalesTerr` テーブルの名前を `Sales` に変更します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_rename 'Sales.SalesTerritory', 'SalesTerr';  
GO  
```  
  
### <a name="b-renaming-a-column"></a>B. 列名を変更する  
 次の例の名前を変更、`TerritoryID`内の列、`SalesTerritory`テーブル`TerrID`します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_rename 'Sales.SalesTerritory.TerritoryID', 'TerrID', 'COLUMN';  
GO  
```  
  
### <a name="c-renaming-an-index"></a>C. インデックス名を変更する  
 次の例の名前を変更、`IX_ProductVendor_VendorID`への索引`IX_VendorID`します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_rename N'Purchasing.ProductVendor.IX_ProductVendor_VendorID', N'IX_VendorID', N'INDEX';  
GO  
```  
  
### <a name="d-renaming-an-alias-data-type"></a>D. 別名データ型の名前を変更する  
 次の例の名前を変更、`Phone`別名データ型を`Telephone`します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_rename N'Phone', N'Telephone', N'USERDATATYPE';  
GO  
```  
  
### <a name="e-renaming-constraints"></a>E. 制約の名前を変更する  
 次の例では、PRIMARY KEY 制約、CHECK 制約、および FOREIGN KEY 制約の名前を変更します。 制約の名前を変更する際は、制約が属するスキーマを指定する必要があります。  
  
```  
USE AdventureWorks2012;   
GO  
-- Return the current Primary Key, Foreign Key and Check constraints for the Employee table.  
SELECT name, SCHEMA_NAME(schema_id) AS schema_name, type_desc  
FROM sys.objects  
WHERE parent_object_id = (OBJECT_ID('HumanResources.Employee'))   
AND type IN ('C','F', 'PK');   
GO  
  
-- Rename the primary key constraint.  
sp_rename 'HumanResources.PK_Employee_BusinessEntityID', 'PK_EmployeeID';  
GO  
  
-- Rename a check constraint.  
sp_rename 'HumanResources.CK_Employee_BirthDate', 'CK_BirthDate';  
GO  
  
-- Rename a foreign key constraint.  
sp_rename 'HumanResources.FK_Employee_Person_BusinessEntityID', 'FK_EmployeeID';  
  
-- Return the current Primary Key, Foreign Key and Check constraints for the Employee table.  
SELECT name, SCHEMA_NAME(schema_id) AS schema_name, type_desc  
FROM sys.objects  
WHERE parent_object_id = (OBJECT_ID('HumanResources.Employee'))   
AND type IN ('C','F', 'PK');  
  
```  
  
```  
  
name                                  schema_name        type_desc  
------------------------------------- ------------------ ----------------------  
FK_Employee_Person_BusinessEntityID   HumanResources     FOREIGN_KEY_CONSTRAINT  
PK_Employee_BusinessEntityID          HumanResources     PRIMARY_KEY_CONSTRAINT  
CK_Employee_BirthDate                 HumanResources     CHECK_CONSTRAINT  
CK_Employee_MaritalStatus             HumanResources     CHECK_CONSTRAINT  
CK_Employee_HireDate                  HumanResources     CHECK_CONSTRAINT  
CK_Employee_Gender                    HumanResources     CHECK_CONSTRAINT  
CK_Employee_VacationHours             HumanResources     CHECK_CONSTRAINT  
CK_Employee_SickLeaveHours            HumanResources     CHECK_CONSTRAINT  
  
(7 row(s) affected)  
  
name                                  schema_name        type_desc  
------------------------------------- ------------------ ----------------------  
FK_Employee_ID                        HumanResources     FOREIGN_KEY_CONSTRAINT  
PK_Employee_ID                        HumanResources     PRIMARY_KEY_CONSTRAINT  
CK_BirthDate                          HumanResources     CHECK_CONSTRAINT  
CK_Employee_MaritalStatus             HumanResources     CHECK_CONSTRAINT  
CK_Employee_HireDate                  HumanResources     CHECK_CONSTRAINT  
CK_Employee_Gender                    HumanResources     CHECK_CONSTRAINT  
CK_Employee_VacationHours             HumanResources     CHECK_CONSTRAINT  
CK_Employee_SickLeaveHours            HumanResources     CHECK_CONSTRAINT  
  
(7 row(s) affected)  
  
```  
  
### <a name="f-renaming-statistics"></a>F. 統計の名前を変更する  
 次の例では、contactMail1 をという名前の統計オブジェクトを作成し、sp_rename を使用して NewContact にし、統計の名前を変更します。 統計の名前を変更する際は、オブジェクトを schema.table.statistics_name の形式で指定する必要があります。  
  
```  
CREATE STATISTICS ContactMail1  
    ON Person.Person (BusinessEntityID, EmailPromotion)  
    WITH SAMPLE 5 PERCENT;  
  
sp_rename 'Person.Person.ContactMail1', 'NewContact','Statistics';  
  
```  
  
## <a name="see-also"></a>参照  
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
