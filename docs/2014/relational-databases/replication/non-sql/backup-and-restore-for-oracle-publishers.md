---
title: Oracle パブリッシャーのバックアップと復元 | Microsoft Docs
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
- recovery [SQL Server replication], Oracle publishing
- backups [SQL Server replication], Oracle publishing
- Oracle publishing [SQL Server replication], backup and restore
- restoring [SQL Server replication], Oracle publishing
ms.assetid: e5f181d0-cacf-442b-8b7a-202b3cfc358b
caps.latest.revision: 32
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 55270122c19f014f16ef62dcdc5efa52395d3ec1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238832"
---
# <a name="backup-and-restore-for-oracle-publishers"></a>Oracle パブリッシャーのバックアップと復元
  バックアップと復元を実行する場合は、次のガイドラインに従ってください。  
  
-   パブリッシャーのバックアップ中は、ログ リーダー エージェントを実行したり、パブリッシュされたテーブルでその他のデータベースの処理を実行しないようにします。  
  
-   パブリッシャーとディストリビューターは同時にバックアップします。  
  
-   パブリッシャーまたはディストリビューターを復元する必要がある場合は、すべてのサブスクリプションを再初期化します。  
  
-   バックアップからサブスクライバーを復元するには (サブスクリプションの再初期化は不要)、前回のサブスクリプション データベースのバックアップ完了後にディストリビューション データベースに配信されたトランザクションも使用できる必要があります。 トランザクションが使用できる時間の長さは、ディストリビューションの保有期間の設定によって異なります。 これらの設定については、「[サブスクリプションの有効期限と非アクティブ化](../subscription-expiration-and-deactivation.md)」を参照してください。  
  
-   データベースを復元した結果、パブリッシャーまたはディストリビューターが同期しなくなった場合は、レプリケーション エージェントによってエラー メッセージが記録されます。 この時点で、関連するパブリケーションとサブスクリプションをすべて削除して再作成する必要があります。  
  
    1.  パブリケーションおよびサブスクリプションの定義のスクリプトを作成します。 詳細については、「 [Scripting Replication](../scripting-replication.md)」を参照してください。  
  
         パブリッシャーとディストリビューターの状態のバージョン間でパブリケーションの定義が変更された場合は、スクリプトを変更する必要があります。  
  
    2.  パブリケーションとサブスクリプションを削除します。  
  
    3.  手順 1. で作成したスクリプトを実行します。  
  
     パブリッシャーを削除および再構成する必要がある場合は、 **MSSQLSERVERDISTRIBUTOR** パブリック シノニムと、 **CASCADE** オプションで構成した Oracle レプリケーション ユーザーを削除して、Oracle パブリッシャーからすべてのレプリケーション オブジェクトを削除します。  
  
## <a name="see-also"></a>参照  
 [レプリケートされたデータベースのバックアップと復元](../administration/back-up-and-restore-replicated-databases.md)   
 [Configure an Oracle Publisher (Oracle パブリッシャーの構成)](configure-an-oracle-publisher.md)   
 [Oracle パブリッシングの概要](oracle-publishing-overview.md)  
  
  
