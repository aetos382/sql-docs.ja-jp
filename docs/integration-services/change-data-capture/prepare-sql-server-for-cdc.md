---
title: CDC 用の SQL Server の準備 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- prepSqlSrv
ms.assetid: 20b51dbf-a545-4234-87ae-4228268a0fb2
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d2b7a7c0e9e6da50bc067840516ad9ceed4e116f
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35329046"
---
# <a name="prepare-sql-server-for-cdc"></a>CDC 用の SQL Server の準備
  Oracle CDC サービスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのターゲット インスタンスに MSXDBCDC データベースが含まれている必要があります。 このデータベースを作成するには、CDC Service 構成コンソールの "SQL Server の準備" アクションを使用します。 これによって作成される特別なスクリプトを実行すると、このデータベースに必要なテーブル、ストアド プロシージャ、およびその他のアーティファクトが作成されます。 このタスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各ターゲット インスタンスに対して一度だけ実行します。  
  
 MSXDBCDC データベースの詳細については、「MSXDBCDC データベース」を参照してください。  
  
 CDC Service 構成コンソールで **[SQLServer の準備]** をクリックします。 このオプションを利用できない場合は、コンソールの左ペインで **[ローカルの CDC Service]** が選択されていることを確認してください。  
  
## <a name="options"></a>および  
  
### <a name="server-name"></a>[サーバー名]  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が存在するサーバーの名前を入力します。  
  
### <a name="authentication"></a>[認証]  
 次のいずれかを選択します。  
  
-   **[Windows 認証]**  
  
-   **[SQL Server 認証]**: このオプションを選択する場合、接続先の **のユーザーの** [ユーザー名] **と** [パスワード] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を入力する必要があります。  
  
 Oracle CDC 用に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを準備するには、ログインが MSXDBCDC データベースに対する書き込み権限を持っている必要があります。 `sysasmin` ロールのメンバーなど、MSXDBCDC データベースに対する書き込み権限を持つログインの資格情報を入力します。  
  
### <a name="options"></a>および  
 矢印をクリックして、構成するオプションを表示します。 これらのオプションを既定値のままにすることもできます。 使用可能なオプションは次のとおりです。  
  
-   **[接続タイムアウト]**: CDC Service for Oracle が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は **15**です。  
  
-   **[実行タイムアウト]**: Oracle CDC Windows Service がコマンドの実行を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は、 **30**です。  
  
-   **[暗号化接続]**: Oracle CDC Service とターゲットの **インスタンスの間の暗号化された接続を使用した通信に対しては、** [暗号化接続] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択します。  
  
-   **[詳細設定]**: 必要に応じて、追加の接続プロパティを入力します。  
  
### <a name="view-script"></a>[スクリプトの表示]  
 セットアップ スクリプトの読み取り専用バージョンを表示するには、 **[スクリプトの表示]** をクリックします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム管理者は、必要に応じて、SQL Server 管理コンソールにこのスクリプトをコピーして編集することができます。 SQL Server スクリプトの準備については、「 [Oracle CDC 表示スクリプト用の SQL Server の準備](../../integration-services/change-data-capture/prepare-sql-server-for-oracle-cdc-view-script.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CDC Service の操作方法](../../integration-services/change-data-capture/how-to-work-with-cdc-services.md)   
 [CDC 用に SQL Server を準備する方法](../../integration-services/change-data-capture/how-to-prepare-sql-server-for-cdc.md)  
  
  
