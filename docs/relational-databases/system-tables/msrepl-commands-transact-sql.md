---
title: MSrepl_commands (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSrepl_commands
- MSrepl_commands_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_commands system table
ms.assetid: 53b9f9cd-9429-47a0-aba2-908fc60e7036
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7eec90fb29378f4cea3530093f2b505b87593fd8
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102400"
---
# <a name="msreplcommands-transact-sql"></a>MSrepl_commands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSrepl_commands**テーブルには、レプリケートされたコマンドの行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|パブリッシャー データベースの ID。|  
|**xact_seqno**|**varbinary(16)**|トランザクション シーケンス番号です。|  
|**type**|**int**|コマンドの種類。|  
|**article_id**|**int**|アーティクルの ID。|  
|**originator_id**|**int**|オリジネータの ID です。|  
|**command_id**|**int**|コマンドの ID です。|  
|**partial_command**|**bit**|これが部分的なコマンドかどうかを示します。|  
|**command**|**varbinary(1024)**|コマンドの値。|  
|**hashkey**|**int**|内部使用のみ。|  
|**originator_lsn**|**varbinary(16)**|発生元パブリケーションのコマンドの LSN を識別します。 これは、ピア ツー ピア トランザクション レプリケーションで使用されます。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_replcmds &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)  
  
  
