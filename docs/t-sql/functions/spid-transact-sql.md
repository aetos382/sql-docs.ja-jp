---
title: '@@SPID (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@SPID'
- '@@SPID_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@SPID function'
- session_id
- server process IDs [SQL Server]
- IDs [SQL Server], user processes
- SPID
- session IDs [SQL Server]
- process ID of current user process
ms.assetid: df955d32-8194-438e-abee-387eebebcbb7
caps.latest.revision: 39
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 5f469447f7ede6812d5e2cd4bb441c4acc70d0be
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39455486"
---
# <a name="x40x40spid-transact-sql"></a>&#x40;&#x40;SPID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のユーザー プロセスのセッション ID を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
@@SPID  
```  
  
## <a name="return-types"></a>戻り値の型  
 **smallint**  
  
## <a name="remarks"></a>Remarks  
 @@SPID は、**sp_who** の出力で、現在のユーザー プロセスを識別する場合に使用できます。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のユーザー プロセスのセッション ID、ログイン名、およびユーザー名を返します。  
  
```  
SELECT @@SPID AS 'ID', SYSTEM_USER AS 'Login Name', USER AS 'User Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
ID     Login Name                     User Name                       
------ ------------------------------ ------------------------------  
54     SEATTLE\joanna                 dbo                             
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、現在のユーザー プロセスに対応する [!INCLUDE[ssDW](../../includes/ssdw-md.md)] セッション ID、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 制御ノード、セッション ID、ログイン名、ユーザー名を返します。  
  
```  
SELECT SESSION_ID() AS ID, @@SPID AS 'Control ID', SYSTEM_USER AS 'Login Name', USER AS 'User Name';  
```  
  
## <a name="see-also"></a>参照  
 [構成関数](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [sp_lock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sp_who](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
  
  

