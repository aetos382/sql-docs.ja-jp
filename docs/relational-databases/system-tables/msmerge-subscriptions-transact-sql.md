---
title: MSmerge_subscriptions (TRANSACT-SQL) |Microsoft Docs
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
- MSmerge_subscriptions
- MSmerge_subscriptions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_subscriptions system table
ms.assetid: cafd954a-92f8-44cb-a5d0-dce9aafa5ee1
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 825b41072c6114271c295488ff0ff700a8de74c6
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102930"
---
# <a name="msmergesubscriptions-transact-sql"></a>MSmerge_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_subscriptions**テーブルには、サブスクライバーでマージ エージェントによって処理される各サブスクリプションの 1 つの行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャー データベースの名前。|  
|**publication_id**|**int**|パブリケーションの ID。|  
|**subscriber_id**|**smallint**|サブスクライバーの ID。|  
|**@subscriber_db**|**sysname**|サブスクリプション データベースの名前。|  
|**subscription_type**|**int**|サブスクリプションの種類です。<br /><br /> 0 = プッシュ<br /><br /> 1 = プル<br /><br /> 2 = 匿名です。|  
|**sync_type**|**tinyint**|同期の種類。<br /><br /> 1 = 自動同期<br /><br /> 2 = 同期しない|  
|**status**|**tinyint**|サブスクリプションの状態。|  
|**subscription_time**|**datetime**|サブスクリプションが追加された時刻。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
