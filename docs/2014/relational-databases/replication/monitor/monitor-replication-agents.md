---
title: レプリケーション エージェントの監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], agents
- Log Reader Agent, monitoring
- Replication Monitor, agents
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- Snapshot Agent, monitoring
- agents [SQL Server replication], monitoring
- Distribution Agent, monitoring
ms.assetid: d06ed24f-82d7-4b9e-9e40-cc9780476a71
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3a5cb81dcbfec1fead6c538d88abdd7d864cfa21
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37268548"
---
# <a name="monitor-replication-agents"></a>レプリケーション エージェントの監視
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション モニターを使用すると、レプリケーションの利用状況を体系的に表示でき、特定のエージェントに関する情報を簡単に見つけることもできます。 次の一覧に、各エージェント、各エージェントを利用できるレプリケーション モニターのタブ、およびそれらのタブへのアクセス方法について説明しているトピックへのリンクを示します。  
  
-   以下のエージェントは、レプリケーション モニターでパブリケーションと関連付けられています。  
  
    -   スナップショット エージェント  
  
    -   ログ リーダー エージェント (Log Reader Agent)  
  
    -   キュー リーダー エージェント (Queue Reader Agent)  
  
     これらのエージェントに関連付けられている情報およびタスクにアクセスするには、 **[エージェント]** タブ (各パブリッシャーおよびパブリケーションで利用可能) または **[警告]** タブ (各パブリケーションで利用可能) を使用します。 詳細については、「[パブリケーションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](view-information-and-perform-tasks-for-publication-agents.md)」を参照してください。  
  
-   以下のエージェントは、レプリケーション モニターでサブスクリプションと関連付けられています。  
  
    -   ディストリビューション エージェント  
  
    -   [マージ エージェント]  
  
     これらのエージェントに関連付けられている情報およびタスクにアクセスするには、 **[サブスクリプション ウォッチ リスト]** タブ (各パブリッシャーで利用可能) または **[すべてのサブスクリプション]** タブ (各パブリケーションで利用可能) を使用します。 詳細については、「[サブスクリプションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](view-information-and-perform-tasks-for-subscription-agents.md)」を参照してください。  
  
## <a name="using-sql-server-management-studio-to-monitor-replication-agents"></a>SQL Server Management Studio を使用してレプリケーション エージェントを監視する  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] には、レプリケーション エージェントの監視用に以下のダイアログ ボックスが用意されています。  
  
-   **[スナップショット エージェントの状態の表示]** ダイアログ ボックス (すべてのパブリケーション用)  
  
-   **[ログ リーダー エージェントの状態の表示]** ダイアログ ボックス (すべてのトランザクション パブリケーション用)  
  
-   **[同期の状態の表示]** ダイアログ ボックス (すべてのサブスクリプション用。このダイアログ ボックスからディストリビューション エージェントおよびマージ エージェントにアクセスできます)  
  
 レプリケーション モニターでは、各エージェントに関する追加情報が表示され、キュー リーダー エージェントが使用されている場合はその監視機能も提供されます。 詳細については、「[パブリケーションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](view-information-and-perform-tasks-for-publication-agents.md)」、「[パブリケーションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](view-information-and-perform-tasks-for-publication-agents.md)」および「[サブスクリプションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](view-information-and-perform-tasks-for-subscription-agents.md)」を参照してください。  
  
#### <a name="to-monitor-the-snapshot-agent-and-log-reader-agent"></a>スナップショット エージェントおよびログ リーダー エージェントを監視するには  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  パブリケーションを右クリックし、 **[ログ リーダー エージェントの状態の表示]** または **[スナップショット エージェントの状態の表示]** をクリックします。  
  
4.  **[ログ リーダー エージェントの状態の表示]** または **[スナップショット エージェントの状態の表示]** ダイアログ ボックスで、以下の操作を行います。  
  
    -   エージェントの状態を表示します。  
  
    -   必要に応じてエージェントを開始または停止します。  
  
    -   **[監視]** をクリックして **レプリケーション モニター**を起動します。  
  
5.  **[閉じる]** をクリックします。  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-publisher"></a>ディストリビューション エージェントおよびマージ エージェントを監視するには (パブリッシャー側から)  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  監視するサブスクリプションのパブリケーションを展開します。  
  
4.  サブスクリプションを右クリックし、 **[同期の状態の表示]** をクリックします。  
  
5.  **[同期の状態の表示]** ダイアログ ボックスで、以下の操作を行います。  
  
    -   エージェントの状態を表示します。  
  
    -   必要に応じてエージェントを開始または停止します。  
  
    -   プッシュ サブスクリプションの場合、 **[監視]** をクリックして **レプリケーション モニター**を起動します。  
  
    -   プル サブスクリプションの場合、 **[ジョブ履歴の表示]** をクリックして **ログ ファイル ビューアー**を起動します。エージェント ログからの出力が表示されます。  
  
6.  **[閉じる]** をクリックします。  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-subscriber"></a>ディストリビューション エージェントおよびマージ エージェントを監視するには (サブスクライバー側から)  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。  
  
3.  監視するサブスクリプションを右クリックして **[同期の状態の表示]** をクリックします。  
  
4.  **[同期の状態の表示]** ダイアログ ボックスで、以下の操作を行います。  
  
    -   エージェントの状態を表示します。  
  
    -   必要に応じてエージェントを開始または停止します。  
  
    -   **[ジョブ履歴の表示]** をクリックして **ログ ファイル ビューアー**を起動します。エージェント ログからの出力が表示されます。  
  
5.  **[閉じる]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [レプリケーションの監視](../monitoring-replication.md)   
 [レプリケーション エージェントの概要](../agents/replication-agents-overview.md)  
  
  
