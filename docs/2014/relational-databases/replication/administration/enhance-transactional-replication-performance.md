---
title: トランザクション レプリケーションのパフォーマンスの向上 | Microsoft Docs
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
- publications [SQL Server replication], design and performance
- performance [SQL Server replication], transactional replication
- designing databases [SQL Server], replication performance
- performance [SQL Server replication], snapshot replication
- snapshot replication [SQL Server], performance
- subscriptions [SQL Server replication], performance considerations
- agents [SQL Server replication], performance
- Distribution Agent, performance
- transactional replication, performance
- Log Reader Agent, performance
ms.assetid: 67084a67-43ff-4065-987a-3b16d1841565
caps.latest.revision: 39
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 97df339dc126d76476790b5bdc983f4bb5053d6c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177779"
---
# <a name="enhance-transactional-replication-performance"></a>トランザクション レプリケーションのパフォーマンスの向上
  「 [レプリケーションの全般的パフォーマンスの向上](enhance-general-replication-performance.md)」で説明した全般的なパフォーマンス向上のヒントを検討した後、トランザクション レプリケーションに固有なこれらの項目を併せて検討してください。  
  
## <a name="database-design"></a>データベースの設計  
  
-   アプリケーションの設計で、トランザクションのサイズを最小化する。  
  
     既定では、トランザクション レプリケーションはトランザクションの境界に従って変更を反映させます。 トランザクションが小さくなると、ネットワークの問題によりディストリビューション エージェントがトランザクションを再送信しなければならなくなる可能性は低くなります。 エージェントがトランザクションを再送信する必要があっても、送信されるデータは少なくなります。  
  
## <a name="distributor-configuration"></a>ディストリビューターの構成  
  
-   ディストリビューション専用サーバーを構成する。  
  
     リモート ディストリビューターを構成することにより、パブリッシャーの処理オーバーヘッドを減らすことができます。 詳しくは、「 [Configure Distribution](../configure-distribution.md)」を参照してください。  
  
-   ディストリビューション データベースのサイズを適切に設定する。  
  
     システムの典型的な負荷でレプリケーションをテストし、コマンドを格納するために必要な領域を決定します。 データベースが頻繁に自動拡張しなくてもコマンドを格納できるだけの大きさを備えていることを確認します。 データベースのサイズの変更に関する詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。  
  
## <a name="publication-design"></a>パブリケーションの設計  
  
-   パブリッシュされたテーブルに対してバッチ更新を行う場合は、ストアド プロシージャの実行をレプリケートする。  
  
     バッチ更新がサブスクライバーで多数の行に影響することがある場合には、パブリッシュされたテーブルをストアド プロシージャで更新することを検討して、ストアド プロシージャの実行をパブリッシュしてください。 ディストリビューション エージェントは、影響を受けたすべての列に対する更新または削除を送信するのではなく、サブスクライバーで同じパラメーター値を使用して同じプロシージャを実行します。 詳細については、「 [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)」を参照してください。  
  
-   複数のパブリケーションにアーティクルを分散する。  
  
     **-SubscriptionStreams** パラメーター (このトピックで後ほど説明します) を使用できない場合は、複数のパブリケーションを作成することを検討してください。 これらのパブリケーションにアーティクルを分散させると、サブスクライバーに対する変更をレプリケーションで並列的に適用できます。  
  
## <a name="subscription-considerations"></a>サブスクリプションに関する注意点  
  
-   同一のパブリッシャーに複数のパブリケーションがある場合は、共有エージェントの代わりに独立エージェントを使用する (これはパブリケーションの新規作成ウィザードの既定の設定です)。  
  
-   エージェントを連続して実行し、高い頻度のスケジュールにはしない。  
  
     エージェントを連続的に実行するようにし、高い頻度のスケジュール、たとえば毎分などのスケジュールの作成を避けることで、レプリケーションのパフォーマンスが向上します。これは、エージェントが開始および停止する必要がなくなるからです。 ディストリビューション エージェントを連続的に実行するように設定すると、トポロジ内で接続しているその他のサーバーに、短い待機時間で変更が反映されます。 詳細については、以下をご覧ください。  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]: [同期スケジュールの指定](../specify-synchronization-schedules.md)  
  
## <a name="distribution-agent-and-log-reader-agent-parameters"></a>ディストリビューション エージェントおよびログ リーダー エージェントのパラメーター  
  
-   予期せずに 1 回だけ発生するボトルネックを解決するには、ログ リーダー エージェントに対して **–MaxCmdsInTran** パラメーターを使用します。  
  
     **–MaxCmdsInTran** パラメーターは、ログ リーダーがディストリビューション データベースにコマンドを書き込む際に、トランザクションにグループ化されるステートメントの最大数を指定します。 このパラメーターを使用すると、ログ リーダー エージェントおよびディストリビューション エージェントは、サブスクライバーでコマンドを適用するときに、パブリッシャーで (多数のコマンドで構成される) 大きなトランザクションを複数の小さなトランザクションに分割できます。 このパラメーターを指定すると、ディストリビューターでの競合を減らし、パブリッシャーとサブスクライバーの間の待機時間を減らすことができます。 元のトランザクションはより小さな単位で適用されるため、サブスクライバーは元のトランザクションが終了する前に、大きな論理パブリッシャー トランザクションの行にアクセスし、トランザクションの厳密な原子性を損なうことがあります。 既定値は **0**です。この場合、パブリッシャーのトランザクション境界が保護されます。 このパラメーターは、Oracle パブリッシャーには適用されません。  
  
    > [!WARNING]  
    >  `MaxCmdsInTran` は、常に有効になるようには設計されていませんでした。 このパラメーターは、ユーザーが誤って 1 つのトランザクションで多数の DML 操作を実行した場合に対応するためのものです (このような場合、トランザクション全体がディストリビューション データベースに格納されるまでコマンドの配布で遅延が発生したり、ロックが保持されたりするなどの問題が発生します)。 このような状況が定期的に発生する場合は、アプリケーションを確認し、トランザクションのサイズを縮小する方法を見つけてください。  
  
-   ディストリビューション エージェントの **–SubscriptionStreams** パラメーターを使用する。  
  
     **–SubscriptionStreams** パラメーターを使用すると、集計レプリケーションのスループットを大幅に向上できます。 このパラメーターを使用すると、単一のスレッドを使用するときに存在するトランザクション特性の多くを維持しつつ、変更のバッチをサブスクライバーへの複数の接続で並列的に適用できます。 いずれかの接続が実行またはコミットに失敗した場合、進行中のバッチがすべての接続について中止されます。その場合、エージェントは、単一のストリームを使用して、失敗したバッチを再試行します。 この再試行フェーズが完了するまでは、サブスクライバー側に、トランザクションの一時的な不整合が存在する可能性があります。 サブスクライバーのトランザクション一貫性は、前回失敗したバッチが正常にコミットされた後で復元されます。  
  
     このエージェント パラメーターの値は、[sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) の **@subscriptionstreams** を使用して指定できます。  
  
-   ログ リーダー エージェントの **-ReadBatchSize** パラメーターの値を大きくする。  
  
     ログ リーダー エージェントとディストリビューション エージェントは、トランザクションの読み取りとコミット操作のバッチ サイズをサポートしています。 バッチ サイズの既定値は 500 トランザクションです。 ログ リーダー エージェントは、レプリケーション用にマークが付けられているかどうかにかかわらず、一定の数のトランザクションをログから読み取ります。 多数のトランザクションがパブリケーション データベースに書き込まれているが、その中のごくわずかなサブセットだけにレプリケーションのマークが付いている場合、 **-ReadBatchSize** パラメーターでログ リーダー エージェントの読み取りバッチ サイズを増やす必要があります。 このパラメーターは、Oracle パブリッシャーには適用されません。  
  
-   ディストリビューション エージェントの **-CommitBatchSize** パラメーターの値を大きくする。  
  
     一連のトランザクションをコミットすると、一定のオーバーヘッドが生じます。より多くのトランザクションを、より低い頻度でコミットするほど、オーバーヘッドは多くのデータに分散されます。 しかし、変更を適用するコストは、ログを含むディスクの最大 I/O などのその他の要因によって制限されるため、このパラメーターを大きくする利点は少なくなります。 さらに、検討すべきトレード オフもあります。ディストリビューション エージェントのやり直しの原因となる失敗をすべてロールバックし、多くのトランザクションを再適用する必要があります。 信頼性の低いネットワークでは、値を小さくすると失敗が少なくなり、失敗が発生した場合にロールバックおよび再適用するトランザクションの数が減ります。  
  
-   ログ リーダー エージェントの **-PollingInterval** パラメーターの値を小さくする。  
  
     **-PollingInterval** パラメーターは、トランザクションをレプリケートするために、パブリッシュされたデータベースのトランザクション ログをクエリする頻度を指定します。 既定値は 5 秒です。 この値を小さくすると、ログを呼び出す頻度は高くなります。これにより、パブリケーション データベースからディストリビューション データベースへのトランザクションの配信の待機時間を減らすことができます。 しかし、待機時間を減らす必要性と、照会の頻度が高くなることによるサーバーの負荷の増加とのバランスをとる必要があります。  
  
 エージェント パラメーターは、エージェント プロファイルおよびコマンド ラインで指定できます。 詳細については、以下をご覧ください。  
  
-   [レプリケーション エージェント プロファイルの操作](../agents/replication-agent-profiles.md)  
  
-   [レプリケーション エージェント コマンド プロンプト パラメーターを表示および変更する &#40;SQL Server Management Studio&#41;](../agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
-   [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md)  
  
  
