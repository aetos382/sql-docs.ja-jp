---
title: sys.database_credentials (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.database_credentials
- sys.database_credentials_TSQL
- database_credentials
- database_credentials_TSQL
helpviewer_keywords:
- sys.database_credentials catalog view
ms.assetid: 796322df-e62a-45bf-b519-89e1d521abce
caps.latest.revision: 8
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: ed1a494823c661710d1a5c184ff72c9f5099565e
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39533472"
---
# <a name="sysdatabasecredentials-transact-sql"></a>sys.database_credentials (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  データベースごとに 1 つの行を返しますでは、データベース内の資格情報がスコープ設定されます。  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)代わりにします。    
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|データベースの ID には、資格情報がスコープ設定されます。 データベース内で一意です。|  
|NAME|**sysname**|データベースの名前には、資格情報がスコープ設定されます。 データベース内で一意です。|  
|credential_identity|**nvarchar (4000)**|使用する識別情報の名前。 通常は Windows ユーザーです。 一意である必要はありません。|  
|create_date|**datetime**|データベース スコープの資格情報が作成された時刻です。|  
|modify_date|**datetime**|データベース スコープの資格情報が最後に変更された時刻です。|  
|target_type|**nvarchar(100)**|データベースの種類には、資格情報がスコープ設定されます。 データベースの NULL を返しますには、資格情報がスコープ設定されます。|  
|target_id|**int**|データベース スコープの資格情報にマップされているオブジェクトの ID。 データベースの 0 を返します。 資格情報のスコープ|  
  
## <a name="permissions"></a>アクセス許可  
 データベースに対する `CONTROL` 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [#40 です。 (&)、データベース スコープ ベースの資格情報を変更します。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
