---
title: '[SQL Server エージェントのプロパティ]\([履歴] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c41f0abf97f2373ca087ccc411d74320046c3def
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38035822"
---
# <a name="sql-server-agent-properties-history-page"></a>SQL Server エージェントのプロパティ ([履歴] ページ)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このページを使用すると、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービス履歴ログの管理設定の表示と設定を行うことができます。  
  
## <a name="options"></a>および  
**[ジョブ履歴ログのサイズを制限する]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントがログで保持するジョブ履歴情報のサイズの上限を設定します。  
  
**[ジョブ履歴ログの最大サイズ (行)]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントによって保持される行の最大数を設定します。 ログの大きさがここで設定した行数に達すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントは新しい行を入力するときにログの最も古い行を削除します。  
  
**[ジョブごとのジョブ履歴の最大行数]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントによってジョブごとに保持される行の最大数を設定します。 特定のジョブの履歴サイズがここで設定した行数に達すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントは新しい行を入力するときにログの最も古い行を削除します。  
  
**[エージェントの履歴を削除する]**  
ログ内のエントリの保存期間が指定された期間を超えたときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントがそのエントリを削除するように指定します。 これは、履歴を削除するために、1 回だけ実行されます。 繰り返し実行する必要がある場合は、クリーンアップ ジョブのメンテナンス プランを作成してスケジュールします。  
  
**[経過期間]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントがエントリを保持する期間を設定します。  
  
## <a name="see-also"></a>参照  
[SQL Server エージェント エラー ログ](../../ssms/agent/sql-server-agent-error-log.md)  
  
