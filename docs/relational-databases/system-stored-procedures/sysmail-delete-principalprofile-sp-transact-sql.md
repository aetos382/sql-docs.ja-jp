---
title: sysmail_delete_principalprofile_sp (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_delete_principalprofile_sp_TSQL
- sysmail_delete_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_principalprofile_sp
ms.assetid: 8fc14700-e17a-4073-9a96-7fc23e775c69
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6f1f7fc964f5be9e045614f7a49c7f5fec194537
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysmaildeleteprincipalprofilesp-transact-sql"></a>sysmail_delete_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベースのユーザーやロールから、パブリックまたはプライベートなデータベース メール プロファイルを使用する権限を削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_delete_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>引数  
 [ **@principal_id** =] *principal_id*  
 データベース ユーザーまたはロールの id を指定します、 **msdb**データベースの関連付けを削除します。 *principal_id*は**int**、既定値は NULL です。 パブリック プロファイルをプライベート プロファイルをようにするには、プリンシパル ID を指定して**0**またはプリンシパル名 **'public'** です。 いずれか*principal_id*または*principal_name*指定する必要があります。  
  
 [ **@principal_name** =] **'***principal_name***'**  
 データベース ユーザーまたはロールの名前を指定します、 **msdb**データベースの関連付けを削除します。 *principal_name*は**sysname**、既定値は NULL です。 パブリック プロファイルをプライベート プロファイルをようにするには、プリンシパル ID を指定して**0**またはプリンシパル名 **'public'** です。 いずれか*principal_id*または*principal_name*指定する必要があります。  
  
 [ **@profile_id** = ] *profile_id*  
 関連付けを削除するプロファイルの ID を指定します。 *profile_id*は**int**、既定値は NULL です。 いずれか*profile_id*または*profile_name*指定する必要があります。  
  
 [ **@profile_name** =] **'***profile_name***'**  
 関連付けを削除するプロファイルの名前を指定します。 *profile_name*は**sysname**、既定値は NULL です。 いずれか*profile_id*または*profile_name*指定する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 パブリック プロファイルをプライベート プロファイルにするには、するには指定 **'public'** のプリンシパル名または**0**プリンシパルの id。  
  
 ユーザーの既定のプライベート プロファイルや、既定のパブリック プロファイルを削除する場合は慎重に行ってください。 既定のプロファイルを使用できない場合、 **sp_send_dbmail**を引数としてプロファイルの名前が必要です。 これにより、既定のプロファイルを削除することがありますとへの呼び出し**sp_send_dbmail**が失敗します。 詳細については、次を参照してください。 [sp_send_dbmail &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md)です。  
  
 ストアド プロシージャ**sysmail_delete_principalprofile_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマです。 現在のデータベースがない場合は、3 部構成の名前を持つプロシージャを実行する必要があります**msdb**です。  
  
## <a name="permissions"></a>権限  
 メンバーにこのプロシージャの既定の実行権限、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、プロファイルの間の関連付けを削除する**AdventureWorks Administrator**とログインの**ApplicationUser**で、 **msdb**データベース。  
  
```  
EXECUTE msdb.dbo.sysmail_delete_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール構成オブジェクト](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [データベース メール ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
