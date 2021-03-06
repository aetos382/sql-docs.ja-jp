---
title: その他のレプリケーションのアップグレードに関する問題 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- system tables [SQL Server], replication
- passwords [SQL Server replication]
- versions [SQL Server replication]
- connections [SQL Server replication]
- scripts [SQL Server replication]
- ActiveX controls [SQL Server replication]
ms.assetid: 8a5e74be-4992-4f17-b20c-c3dce8f49329
caps.latest.revision: 34
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1aa132e53e3d3328863c8f30fc86277fc6b394ea
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200682"
---
# <a name="other-replication-upgrade-issues"></a>レプリケーションのアップグレードに関するその他の問題
  このトピックでは、アップグレード アドバイザーによって報告されない多くのアップグレード問題について説明します。  
  
## <a name="versions-supported"></a>サポートされているバージョン  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、レプリケートされたデータベースを以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からアップグレードできます。 ノードのアップグレード中に、その他のノードでの操作を停止する必要はありません。 トポロジでサポートされるバージョンに関する以下の規則に従っていることを確認してください。  
  
 間または異なるバージョンの間でレプリケートするときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、通常は、使用されている最も古いバージョンの機能に制限されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のディスク上ストレージ形式は、64 ビット環境と 32 ビット環境で同じため、レプリケーション トポロジでは、32 ビット環境で実行されているサーバー インスタンスと 64 ビット環境で実行されているサーバー インスタンスを組み合わせることができます。  
  
 どの種類のレプリケーションでも、ディストリビューターのバージョンがパブリッシャーのバージョン以上である必要があります  (多くの場合、ディストリビューターはパブリッシャーと同じインスタンスです)。  
  
 トランザクション レプリケーションの場合、トランザクション パブリケーションのサブスクライバーは、2 つのパブリッシャー バージョンのうちどちらでも使用できます。  
  
 マージ レプリケーションの場合、マージ パブリケーションのサブスクライバーは、パブリッシャーのバージョン以前であればどのバージョンでも使用できます。  
  
## <a name="merge-replication-batches-changes"></a>マージ レプリケーションのバッチの変更  
 マージ エージェントによって行われた変更がパフォーマンス向上のためにバッチ処理されるため、1 つのステートメント内で複数の行を挿入、更新、または削除できます。 パブリケーション データベースまたはサブスクリプション データベースでパブリッシュされたテーブルにトリガーがある場合には、トリガーによって複数行の挿入、更新、および削除が処理されることを確認してください。 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「DML トリガーの複数行に関する注意点」を参照してください。  
  
## <a name="activex-control-changes"></a>ActiveX コントロールの変更  
 レプリケーション ActiveX コントロールに対する変更は次のとおりです。  
  
-   すべての ActiveX コントロールに、スクリプトおよび初期化に対して安全でないことを示すマークが付けられます。  
  
-   スナップショット ActiveX コントロールはサポートされなくなりました。 スナップショットを作成および管理するには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用するか、レプリケーション ストアド プロシージャを使用してプログラムによって実行します。 詳細については、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オンライン ブックの「初期スナップショットを作成および適用する方法 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])」および「初期スナップショットを作成する方法 (レプリケーション Transact-SQL プログラミング)」を参照してください。  
  
-   ディストリビューション ActiveX コントロールおよびマージ ActiveX コントロールは非推奨とされます。 同様の機能は、レプリケーション管理オブジェクト (RMO) を使用したマネージド コード アプリケーションに提供されます。 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「サブスクリプションの同期 (RMO プログラミング)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レプリケーションのアップグレードに関する問題](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
