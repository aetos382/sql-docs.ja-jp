---
title: レプリケーションの種類 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], types
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
caps.latest.revision: 36
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9d3f322f79d005b9579130c34ba9185f6dd9fa74
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37251924"
---
# <a name="types-of-replication"></a>レプリケーションの種類
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、以下の種類のレプリケーションを分散アプリケーションで利用できます。  
  
-   トランザクション レプリケーション。 詳細については、「[Transactional Replication](transactional/transactional-replication.md)」 (トランザクション レプリケーション) を参照してください。  
  
-   マージ レプリケーション。 詳細については、「[Merge Replication](merge/merge-replication.md)」 (マージ レプリケーション) をご覧ください。  
  
-   スナップショット レプリケーション。 詳細については、「[Snapshot Replication](snapshot-replication.md)」 (スナップショット レプリケーション) をご覧ください。  
  
 アプリケーションで使用するレプリケーションの種類は、物理的なレプリケーション環境、レプリケートするデータの種類と量、データをサブスクライバーで更新するかどうかなどの、さまざまな要因によって異なります。 物理環境には、レプリケーションに関係するコンピューターの数と場所、これらのコンピューターがクライアント (ワークステーション、ラップトップ、またはハンドヘルド デバイス) なのかサーバーなのか、などが含まれます。  
  
 どの種類のレプリケーションも、通常、パブリッシュされたオブジェクトをパブリッシャーとサブスクライバー間で初期同期することから始まります。 初期同期は、 *スナップショット*を使用したレプリケーションで実行できます。スナップショットは、パブリケーションで指定されたすべてのオブジェクトおよびデータのコピーです。 作成されたスナップショットはサブスクライバーに配信されます。 アプリケーションによっては、スナップショット レプリケーションのみで十分なこともあります。 スナップショット レプリケーションだけでは不十分なアプリケーションでは、その後行われたデータ変更が、一定期間にわたって増分としてサブスクライバーに渡されることが重要です。 また、アプリケーションによっては、サブスクライバーからパブリッシャーに変更を送り返す必要もあります。 トランザクション レプリケーションおよびマージ レプリケーションには、このような種類のアプリケーション用のオプションがあります。  
  
 スナップショット レプリケーションでは、データの変更は追跡されず、スナップショットが適用されるたびに、既存のデータがすべて上書きされます。 トランザクション レプリケーションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] トランザクション ログを使用して変更が追跡され、マージ レプリケーションでは、トリガーとメタデータ テーブルを使用して変更が追跡されます。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェントの概要](agents/replication-agents-overview.md)  
  
  
