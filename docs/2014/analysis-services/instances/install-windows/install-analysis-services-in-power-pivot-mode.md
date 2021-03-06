---
title: PowerPivot for SharePoint 2013 のインストール |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d3310562-82c1-454f-9c48-33a241749238
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d5eafcfacf8aa39cd100ed767232becd474bacd0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37210252"
---
# <a name="powerpivot-for-sharepoint-2013-installation"></a>PowerPivot for SharePoint 2013 のインストール
  このトピックの手順に従って、シングル サーバー インストールの[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]SharePoint 配置モードでのサーバー。 手順には、SQL Server インストール ウィザードの実行と、SharePoint 2013 サーバーの全体管理を使用する構成タスクが含まれます。  
  
 **[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013 |SharePoint 201  
  
 **このトピックの内容:**  
  
 [背景情報](#bkmk_background)  
  
 [前提条件](#bkmk_prereq)  
  
 [手順 1: SharePoint の PowerPivot をインストールします。](#InstallSQL)  
  
 [手順 2. 基本的な Analysis Services SharePoint 統合の構成](#bkmk_config)  
  
 [手順 3. 統合の確認](#bkmk_verify)  
  
 [Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](#bkmk_firewall)  
  
 [ブックのアップグレードと定期データ更新](#bkmk_upgrade_workbook)  
  
 [シングル サーバー インストール: PowerPivot for Microsoft SharePoint を超える](#bkmk_multiple_servers)  
  
##  <a name="bkmk_background"></a> 背景情報  
 PowerPivot for SharePoint は、SharePoint 2013 ファームでの PowerPivot データ アクセスを提供する中間層のバックエンド サービスです。  
  
-   **バックエンド サービス:** PowerPivot for Excel を使用して分析データが含まれたブックを作成した場合、サーバー環境でそのデータにアクセスするには PowerPivot for SharePoint が必要です。 SQL Server セットアップは、SharePoint Server 2013 がインストールされているコンピューターで実行することも、SharePoint ソフトウェアがインストールされていない別のコンピューターで実行することもできます。 Analysis Services には、SharePoint との依存関係はありません。  
  
     **注:** このトピックでは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーおよびバックエンド サービスのインストールについて説明します。  
  
-   **中間層:** PowerPivot ギャラリー、定期データ更新、管理ダッシュボード、データ プロバイダーなどの SharePoint の PowerPivot エクスペリエンスを強化します。 中間層のインストールと構成の詳細については、以下を参照してください。  
  
    -   [For SharePoint アドインの PowerPivot のアンインストールをインストールまたは&#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)  
  
    -   [PowerPivot の構成し、ソリューションの配置&#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)  
  
##  <a name="bkmk_prereq"></a> 前提条件  
  
1.  SQL Server セットアップを実行するには、ローカル管理者である必要があります。  
  
2.  PowerPivot for SharePoint には SharePoint Server 2013 Enterprise Edition が必要です。 評価版の Enterprise Edition を使用することもできます。  
  
3.  コンピューターは、Excel Services と同じ Active Directory フォレストのドメインに参加する必要があります。  
  
4.  PowerPivot インスタンスの名前を使用できる必要があります。 PowerPivot 名前付きインスタンスが既に存在するコンピューターに、SharePoint モードの Analysis Services をインストールすることはできません。  
  
5.  レビュー [Hardware and Software Requirements の SharePoint モードで Analysis Services サーバー &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md)します。  
  
6.  リリース ノートを確認して[SQL Server 2012 Service Pack 1 リリース ノート](http://go.microsoft.com/fwlink/?LinkID=248389)(http://go.microsoft.com/fwlink/?LinkID=248389)します。  
  
###  <a name="bkmk_sqleditions"></a> SQL Server エディションの要件  
 ビジネス インテリジェンス機能は、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のすべてのエディションで利用できるわけではありません。 詳細については、次を参照してください。 [SQL Server 2012 の各エディションでサポートされる機能 (http://go.microsoft.com/fwlink/?linkid=232473) ](http://go.microsoft.com/fwlink/?linkid=232473)と[エディションと SQL Server 2014 のコンポーネントの](../../../sql-server/editions-and-components-of-sql-server-2016.md)します。  
  
 現在のリリース ノートをご覧[SQL Server 2012 SP1 リリース ノート](ttp://go.microsoft.com/fwlink/?LinkID=248389)(http://go.microsoft.com/fwlink/?LinkID=248389)します。  
  
 [Microsoft SQL Server 2012 リリース ノート (http://go.microsoft.com/fwlink/?LinkId=236893)](http://go.microsoft.com/fwlink/?LinkId=236893)します。  
  
##  <a name="InstallSQL"></a> 手順 1: SharePoint の PowerPivot をインストールします。  
 この手順では、SQL Server セットアップを実行して、SharePoint モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーをインストールします。 後の手順で、このサーバーをブックのデータ モデルで使用するように Excel Services を構成します。  
  
1.  SQL Server インストール ウィザード (Setup.exe) を実行します。  
  
2.  左側のナビゲーション ウィンドウで、 **[インストール]** をクリックします。  
  
3.  **[SQL Server の新規スタンドアロン インストールを実行するか、既存のインストールに機能を追加します]** をクリックします。  
  
4.  **[プロダクト キー]** ページが表示されたら、Evaluation Edition を指定するか、Enterprise Edition のライセンス コピーのプロダクト キーを入力します。 **[次へ]** をクリックします。 エディションの詳細については、次を参照してください。[エディションと SQL Server 2014 のコンポーネントの](../../../sql-server/editions-and-components-of-sql-server-2016.md)します。  
  
5.  マイクロソフト ソフトウェア ライセンス条項を確認して同意し、 **[次へ]** をクリックします。  
  
6.  **[グローバル ルール]** ページが表示されたら、セットアップ ウィザードに表示されるすべてのルールの情報を確認します。  
  
7.  **[Microsoft Update]** ページで、Microsoft Update を使用して更新プログラムを確認することをお勧めします。確認したら、 **[次へ]** をクリックします。  
  
8.  **[セットアップ ファイルのインストール]** ページが数分間実行されます。 ルールの警告または失敗したルールを確認し、 **[次へ]** をクリックします。  
  
9. 別の **[セットアップ サポート ルール]** が表示されたら、警告を確認し、 **[次へ]** をクリックします。  
  
     **注:** Windows ファイアウォールが有効になっているため、ポートを開いてリモート アクセスを有効にするよう求める警告が表示されます。  
  
10. **[セットアップ ロール]** ページで、 **[SQL Server PowerPivot for SharePoint]** を選択します。 このオプションを選択すると、SharePoint モードの Analysis Services がインストールされます。  
  
     オプションで、データベース エンジンのインスタンスをインストールに追加することができます。 新しいファームを設定し、ファームの構成データベースとコンテンツ データベースを実行するためにデータベース サーバーが必要な場合に、データベース エンジンを追加できます。 このオプションでは、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] もインストールされます。  
  
     データベース エンジンを追加した場合は、 **PowerPivot** 名前付きインスタンスとしてインストールされます。 このインスタンスへの接続を指定するには、次の形式でデータベース名を入力します。 [`servername`] \PowerPivot します。  
  
     **[次へ]** をクリックします。  
  
     ![セットアップ ロール](../../../sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "セットアップ ロール")  
  
11. [機能の選択] に、機能の一覧が表示されます。この一覧は情報提供を目的としており、読み取り専用になっています。 このロールに対してあらかじめ選択されている項目を、追加または削除することはできません。 **[次へ]** をクリックします。  
  
12. **[インスタンスの構成]** ページに、"PowerPivot" というインスタンス名が表示されます。この名前は情報として示されており、読み取り専用になっています。 このインスタンス名は必須であり、変更することはできません。 ただし、ディレクトリ名とレジストリ キーをわかりやすく示した独自のインスタンス ID を入力することができます。 **[次へ]** をクリックします。  
  
13. **[サーバー構成]** のページで、すべてのサービスの **[スタートアップの種類]** を [自動] に設定します。 **SQL Server Analysis Services**に必要なドメイン アカウントとパスワードを指定します。次の図の **(1)** です。  
  
    -   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]では、 **ドメイン ユーザー** アカウントまたは **NetworkService** アカウントを使用できます。 LocalSystem アカウントまたは LocalService アカウントは使用しないでください。  
  
    -   SQL Server データベース エンジンと SQL Server エージェントを追加した場合は、サービスがドメイン ユーザー アカウントまたは既定の仮想アカウントで実行されるように構成できます。  
  
    -   サービス アカウントには自分のドメイン ユーザー アカウントを指定しないでください。 このようなアカウントを使用すると、ネットワークのリソースに対して持っている権限と同じ権限をサーバーに付与することになります。 悪意のあるユーザーがサーバーに侵入した場合、そのユーザーは管理者のドメイン資格情報を使用してログオンします。 そのユーザーは、管理者と同じデータやアプリケーションをダウンロードしたり使用したりする権限を持ちます。  
  
     **[次へ]** をクリックします。  
  
     ![SSAS サーバーの構成](../../../sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "SSAS サーバーの構成")  
  
14. [!INCLUDE[ssDE](../../../includes/ssde-md.md)]をインストールする場合は、 **[データベース エンジンの構成]** ページが表示されます。 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]構成では、をクリックして **[現在のユーザー**ユーザー、データベース エンジン インスタンスに対するアカウント管理者のアクセス許可を付与します。  
  
     **[次へ]** をクリックします。  
  
15. **[Analysis Services の構成]** ページで、 **[現在のユーザーの追加]** をクリックして、ユーザー アカウントに管理権限を付与します。 セットアップの完了後にサーバーを構成するには、管理権限が必要になります。  
  
    -   同じページで、同じく管理権限が必要なユーザーの Windows ユーザー アカウントを追加します。 たとえば、データベース接続の問題のトラブルシューティングを行うために、 [!INCLUDE[ssGeminiSrv](../../../includes/ssgeminisrv-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] インスタンスに接続するユーザーには、システム管理者権限が必要です。 サーバーのトラブルシューティングや管理を担当する可能性があるユーザーのユーザー アカウントをここで追加しておきます。  
  
    -   > [!NOTE]  
        >  Analysis Services サーバー インスタンスにアクセスする必要があるすべてのサービス アプリケーションに、Analysis Services 管理権限が必要です。 たとえば、Excel Services、Power View、Performance Point Services のサービス アカウントを追加します。 また、サーバーの全体管理をホストする Web アプリケーションの ID として使用される SharePoint ファーム アカウントも追加します。  
  
     **[次へ]** をクリックします。  
  
16. **[エラー レポート]** ページで **[次へ]** をクリックします。  
  
17. **[インストールの準備完了]** ページで **[インストール]** をクリックします。  
  
18. **[コンピューターの再起動が必要です]** ダイアログ ボックスが表示されたら、 **[OK]** をクリックします。  
  
19. インストールが完了したら、 **[閉じる]** をクリックします。  
  
20. コンピューターを再起動します。  
  
21. 環境内にファイアウォールがある場合は、SQL Server オンライン ブックの「 [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md)」を確認します。  
  
### <a name="verify-the-sql-server-installation"></a>SQL Server のインストールの確認  
 Analysis Services サービスが実行されているかどうかを確認します。  
  
1.  Windows の **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** をクリックして、 **[Microsoft SQL Server 2012]** をクリックします。  
  
2.  **[SQL Server Management Studio]** をクリックします。  
  
3.  Analysis Services インスタンス (たとえば、 **[サーバー名]\POWERPIVOT**) に接続します。 インスタンスに接続できたら、サービスが実行されていることがわかります。  
  
##  <a name="bkmk_config"></a> 手順 2. 基本的な Analysis Services SharePoint 統合の構成  
 SharePoint ドキュメント ライブラリ内で Excel の高度なデータ モデルを操作できるようにするには、次の手順を実行して構成を変更する必要があります。 これらの手順は、SharePoint Server 2013 と SQL Server Analysis Services をインストールしてから実行します。  
  
### <a name="grant-excel-services-server-administration-rights-on-analysis-services"></a>Excel Services への Analysis Services に対するサーバー管理権限の付与  
 Analysis Services のインストール時に、Analysis Services 管理者として Excel Services アプリケーションのサービス アカウントを追加した場合は、このセクションの手順を実行する必要はありません。  
  
1.  Analysis Services サーバーで、SQL Server Management Studio を起動し、Analysis Services インスタンス (たとえば、`[MyServer]\POWERPIVOT`) に接続します。  
  
2.  オブジェクト エクスプローラーで、インスタンス名を右クリックし、 **[プロパティ]** をクリックします。  
  
     ![SSAS サーバーのプロパティを表示](../../../sql-server/install/media/as-ssms-proeprties.gif "SSAS サーバーのプロパティの表示")  
  
3.  左ペインで、 **[セキュリティ]** をクリックします。 手順 1. で Excel Services アプリケーション用に構成したドメイン ログインを追加します。  
  
     ![SSAS サーバーのセキュリティ設定](../../../sql-server/install/media/as-ssms-security.gif "SSAS サーバーのセキュリティ設定")  
  
### <a name="configure-excel-services-for-analysis-services-integration"></a>Analysis Services 統合のための Excel Services の構成  
  
1.  SharePoint サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  サービス アプリケーションの名前をクリックします。既定の名前は **"Excel Services アプリケーション"** です。  
  
3.  **[Excel Services アプリケーションの管理]** ページで、 **[データ モデルの設定]** をクリックします。  
  
4.  **[サーバーの追加]** をクリックします。  
  
5.  **[サーバー名]** に、Analysis Services サーバー名と PowerPivot インスタンス名を入力します。 たとえば、 `MyServer\POWERPIVOT`があります。 PowerPivot インスタンス名は必須です。  
  
     説明を入力します。  
  
6.  **[OK]** をクリックします。  
  
7.  変更は数分で有効になりますが、 **Excel Calculation Services** サービスを **停止** および **開始**することもできます。 変換先  
  
     別の方法として、管理者特権でコマンド プロンプトを開き、「 `iisreset /noforce`」と入力します。  
  
     ULS ログのエントリを確認することで、サーバーが Excel Services によって認識されているかどうかを確認できます。 実際のエントリの例を次に示します。  
  
    ```  
    Excel Services Application            Data Model        27           Medium                Check Administrator Access ([ServerName]\POWERPIVOT): Pass.        f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Server Version ([ServerName]\POWERPIVOT): Pass (11.0.2809.24 >= 11.0.2800.0).         f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Deployment Mode ([ServerName]\POWERPIVOT): Pass.            f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
  
    ```  
  
##  <a name="bkmk_verify"></a> 手順 3. 統合の確認  
 ここでは、Analysis Services 統合を確認するために、新しいブックを作成し、アップロードする手順を示します。 この手順を実行するには、SQL Server データベースが必要です。  
  
1.  **注:** スライサーやフィルターが含まれた高度なブックが既にある場合は、そのブックを SharePoint ドキュメント ライブラリにアップロードし、ドキュメント ライブラリ ビューからスライサーとフィルターを操作できるかどうかを確認します。  
  
2.  Excel で新しいブックを開きます。  
  
3.  [データ] タブの **[外部データの取り込み]** で、 **[その他のデータ ソース]** をクリックします。  
  
4.  **[SQL Server]** を選択します。  
  
5.  **データ接続ウィザード**で、使用するデータベースがある SQL Server インスタンスの名前を入力します。  
  
6.  または、ログオン資格情報を入力し、 **[Windows 認証を使用する]** が選択されていることを確認して、 **[次へ]** をクリックします。  
  
7.  使用するデータベースを選択します。  
  
8.  **[指定したテーブルに接続]** チェック ボックスがオンになっていることを確認します。  
  
9. **[複数のテーブルの選択を有効にし、テーブルを Excel データ モデルに追加する]** チェック ボックスをオンにします。  
  
10. インポートするテーブルを選択します。  
  
11. **[選択したテーブル間のリレーションシップをインポートする]** チェック ボックスをオンにし、 **[次へ]** をクリックします。 リレーショナル データベースから複数のテーブルをインポートすると、既に関連付けられているテーブルを使用できます。 リレーションシップを手動で作成する必要がないため、手間を省くことができます。  
  
12. ウィザードの **[データ接続ファイルを保存して終了]** ページで、接続の名前を入力し、 **[完了]** をクリックします。  
  
13. **[データのインポート]** ダイアログ ボックスが表示されます。 **[ピボットテーブル レポート]** を選択し、 **[OK]** をクリックします。  
  
14. ブックにピボットテーブル フィールド リストが表示されます。   
    フィールド リストで、 **[すべて]** タブをクリックします。  
  
15. フィールド リストの [行]、[列]、[値] の各領域にフィールドを追加します。  
  
16. ピボットテーブルにスライサーまたはフィルターを追加します。 **この手順は省略しないでください**。 スライサーまたはフィルターは、Analysis Services のインストールの確認に役立つ要素です。  
  
17. Excel Services が構成されている SharePoint Server 2013 のドキュメント ライブラリにブックを保存します。 また、ブックをファイル共有に保存し、SharePoint Server 2013 ドキュメント ライブラリにアップロードすることもできます。  
  
18. ブックの名前をクリックして SharePoint で表示し、スライサーをクリックするか、以前に追加したフィルターを変更します。 データ更新が行われたら、Analysis Services がインストールされ、Excel Services で利用できることがわかります。 ブックを Excel で開いた場合は、Analysis Services サーバーではなく、キャッシュ コピーが使用されます。  
  
##  <a name="bkmk_firewall"></a> Analysis Services のアクセスを許可するための Windows ファイアウォールの構成  
 トピックの情報を使用して[Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../configure-the-windows-firewall-to-allow-analysis-services-access.md)for SharePoint を Analysis Services または PowerPivot へのアクセスを許可するファイアウォールのポートのブロックを解除する必要があるかどうか判断します。 このトピックに示された手順に従って、ポートとファイアウォールを構成できます。 実際に Analysis Services サーバーへのアクセスを許可するためには、これらの手順を組み合わせて実行する必要があります。  
  
##  <a name="bkmk_upgrade_workbook"></a> ブックのアップグレードと定期データ更新  
 PowerPivot の以前のバージョンで作成したブックのアップグレードに必要な手順は、そのブックを作成した PowerPivot のバージョンによって異なります。 詳細については、「 [ブックのアップグレードと定期データ更新 &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)」を参照してください。  
  
##  <a name="bkmk_multiple_servers"></a> シングル サーバー インストール: PowerPivot for Microsoft SharePoint を超える  
 **Web フロント エンド (WFE)** または**中間層:**: を使用する、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インストーラーパッケージを実行して、ファームにPowerPivotの追加機能をインストールして大規模なSharePointファームでSharePointモードサーバー**spPowerPivot.msi**各 SharePoint サーバー上でします。 spPowerPivot.msi では、必要なデータ プロバイダーと PowerPivot for SharePoint 2013 の構成ツールをインストールします。  
  
 中間層のインストールと構成の詳細については、以下を参照してください。  
  
-   [For SharePoint アドインの PowerPivot のアンインストールをインストールまたは&#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)  
  
-   .msi をダウンロードするには、「 [Microsoft SQL Server 2014 PowerPivot for Microsoft SharePoint 2013](http://go.microsoft.com/fwlink/?LinkID=324854)」を参照してください。  
  
-   [PowerPivot の構成し、ソリューションの配置&#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)  
  
 **冗長性とサーバー負荷:** 秒以上をインストールする[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]SharePoint モードのサーバーでの冗長性が実現、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]サーバーの機能です。 サーバーを追加すると、サーバー間の負荷分散も行われます。 詳細については、以下を参照してください。  
  
-   [Excel Services でのデータ モデルを処理するための Analysis Services を構成する](http://technet.microsoft.com/library/jj614437\(v=office.15\))(http://technet.microsoft.com/library/jj614437(v=office.15))します。  
  
-   [Excel Services データ モデルの設定 (SharePoint Server 2013) を管理](http://technet.microsoft.com/library/jj219780\(v=office.15\))(http://technet.microsoft.com/library/jj219780(v=office.15))します。  
  
 ![SharePoint の設定](../../../analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 設定")[フィードバックや連絡先の情報を Microsoft SQL Server の接続を介して送信](https://connect.microsoft.com/SQLServer/Feedback)(https://connect.microsoft.com/SQLServer/Feedback)します。  
  
## <a name="see-also"></a>参照  
 [SharePoint 2013 への PowerPivot を移行します。](../../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)   
 [For SharePoint アドインの PowerPivot のアンインストールをインストールまたは&#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)   
 [ブックと定期データ更新のアップグレード&#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
