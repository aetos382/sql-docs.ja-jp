---
title: sp_droprolemember (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_droprolemember_TSQL
- sp_droprolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droprolemember
ms.assetid: c2f19ab1-e742-4d56-ba8e-8ffd40cf4925
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: cc774ca7b734f3a46728f694aa99272d7b4104c0
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39534372"
---
# <a name="spdroprolemember-transact-sql"></a>sp_droprolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ロールからセキュリティ アカウントを削除します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
sp_droprolemember [ @rolename = ] 'role' ,   
     [ @membername = ] 'security_account'  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_droprolemember 'role' ,  
     'security_account'  
```  
  
## <a name="arguments"></a>引数  
 [  **@rolename =** ] **'***ロール***'**  
 メンバーを削除するロールの名前を指定します。 *ロール*は**sysname**、既定値はありません。 *ロール*現在のデータベースに存在する必要があります。  
  
 [  **@membername =** ] **'***これ***'**  
 ロールから削除するセキュリティ アカウントの名前を指定します。 *これ*は**sysname**、既定値はありません。 *これ*データベース ユーザー、別のデータベース ロール、Windows ログイン、または Windows グループにすることができます。 *これ*現在のデータベースに存在する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 sp_droprolemember の各は、sysmembers テーブルから行を削除することによって、データベース ロールからメンバーを削除します。 メンバーがロールから削除されると、メンバーはそのロール内のメンバーシップに基づくすべての権限を失います。  
  
 固定サーバー ロールからユーザーを削除するには、sp_dropsrvrolemember を使用します。 パブリック ロールからユーザーを削除して、dbo は、任意のロールから削除することはできません。  
  
 メンバーを表示する sp_helpuser を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ロール、および使用する ALTER ROLE をロールにメンバーを追加します。  
  
## <a name="permissions"></a>アクセス許可  
 ロールに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、ロール `JonB` からユーザー `Sales` を削除します。  
  
```  
EXEC sp_droprolemember 'Sales', 'Jonb';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、ロール `JonB` からユーザー `Sales` を削除します。  
  
```  
EXEC sp_droprolemember 'Sales', 'JonB'  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md)   
 [sp_dropsrvrolemember &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpuser &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

