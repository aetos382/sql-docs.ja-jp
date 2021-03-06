---
title: SQL Server Data Tools (SSDT) のダウンロード | Microsoft Docs
ms.custom: ''
ms.date: 07/02/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssdt
ms.reviewer: ''
ms.suite: sql
ms.technology: ssdt
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords:
- ssdt のインストール, ssdt のダウンロード, 最新の ssdt
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 78eb769a8f37ca055628a89aeebe7dd444673434
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37988224"
---
# <a name="download-and-install-sql-server-data-tools-ssdt-for-visual-studio"></a>Visual Studio の SQL Server Data Tools (SSDT) をダウンロードし、インストールする
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
**SQL Server Data Tools** は、SQL Server リレーショナル データベース、Azure SQL データベース、Analysis Services (AS) データ モデル、Integration Services (IS) パッケージ、Reporting Services (RS) レポートをビルドするための最新の開発ツールです。 SSDT では、Visual Studio でアプリケーションを開発する場合と同じくらい簡単に、SQL Server のコンテンツの種類を設計および展開できます。

*ほとんどのユーザーの場合、SQL Server Data Tools (SSDT) は Visual Studio インストール中にインストールされます。Visual Studio インストーラーを利用して SSDT をインストールすると、基本 SSDT 機能が追加されます。そのため、AS、IS、RS ツールを入手するには、[SSDT スタンドアロン インストーラー](#ssdt-for-vs-2017-standalone-installer)を実行する必要があります。*

## <a name="install-ssdt-with-visual-studio-2017"></a>Visual Studio 2017 で SSDT をインストールする

[Visual Studio インストール](https://docs.microsoft.com/visualstudio/install/install-visual-studio)中に SSDT をインストールするには、**[データの保存と処理]** ワークロードを選択し、**[SQL Server Data Tools]** を選択します。 Visual Studio が既にインストールされている場合、[ワークロードの一覧を編集し](https://docs.microsoft.com/visualstudio/install/modify-visual-studio)、SSDT: ![データの保存と処理ワークロード](../ssdt/media/download-sql-server-data-tools-ssdt/data-workload.png)を含めることができます。



## <a name="install-analysis-services-integration-services-and-reporting-services-tools"></a>Analysis Services、Integration Services、Reporting Services ツールをインストールする
AS、IS、RS プロジェクト サポートをインストールするには、[SSDT スタンドアロン インストーラー](#ssdt-for-vs-2017-standalone-installer)を実行します。 

このインストーラーは、SSDT ツールの追加先となる Visual Studio インスタンスを一覧表示します。 Visual Studio がインストールされていない場合、**[Install a new SQL Server Data Tools instance]\(新しい SQL Server Data Tools インスタンスをインストールする\)** を選択すると、SSDT と最小バージョンの Visual Studio がインストールされますが、SSDT と共に、最も使い勝手の良い[最新バージョンの Visual Studio](https://www.visualstudio.com/downloads) を利用することをお勧めします。 

![AS、IS、RS を選択する](../ssdt/media/download-sql-server-data-tools-ssdt/select-services.png)



## <a name="ssdt-for-vs-2017-standalone-installer"></a>SSDT for VS 2017 (スタンドアロン インストーラー)

[![ダウンロード](../ssdt/media/download.png) SSDT for Visual Studio 2017 (15.7.1) をダウンロードする](https://go.microsoft.com/fwlink/?linkid=875613) 

> [!IMPORTANT]
> - SSDT for Visual Studio 2017 (15.7.1) をインストールする前に、"*Analysis Services プロジェクト*" と "*Reporting Services プロジェクト*" 拡張機能を既にインストールしてある場合はアンインストールし、すべての VS インスタンスを閉じます。
> - Windows 10 に SSDT をインストールし、**[新しい SQL Server Data Tools for Visual Studio 2017 インスタンスをインストールします]** を選択するときは、すべてのチェック ボックスをオフにして、最初に新しいインスタンスをインストールしてください。 新しいインスタンスをインストールした後、コンピューターを再起動し、SSDT インストーラーを再度開いて、インストールを続行してください。  



**バージョン情報**  
  
リリース番号: 15.7.1  
ビルド番号: 14.0.16167.0  
リリース日: 2018 年 7 月 2 日  

詳細な変更一覧については、[変更ログ](changelog-for-sql-server-data-tools-ssdt.md)を参照してください。

SSDT for Visual Studio 2017 の[システム要件](https://docs.microsoft.com/visualstudio/productinfo/vs2017-system-requirements-vs)は Visual Studio と同じです。  

### <a name="available-languages---ssdt-for-vs-2017"></a>使用できる言語 - SSDT for VS 2017

**SSDT for VS 2017** の今回のリリースは、次の言語でインストールできます。  

[中国語 (中華人民共和国)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x804) | 
[中国語 (台湾)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x404) | 
[英語 (米国)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x409) | 
[フランス語]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x40c)  
[ドイツ語]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x407) | 
[イタリア語]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x410) | 
[日本語]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x411) | 
[韓国語]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x412) | 
[ポルトガル語 (ブラジル)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x416) | 
[ロシア語]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x419) | 
[スペイン語]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x40a)  



## <a name="ssdt-for-vs-2015-standalone-installer"></a>SSDT for VS 2015 (スタンドアロン インストーラー)

[![ダウンロード](../ssdt/media/download.png) SSDT for Visual Studio 2015 (17.4) をダウンロードする](https://go.microsoft.com/fwlink/?linkid=863440)

**バージョン情報**  
  
リリース番号: 17.4

このリリースのビルド番号: 14.0.61712.050
  
詳細な変更一覧については、[変更ログ](changelog-for-sql-server-data-tools-ssdt.md)を参照してください。

### <a name="available-languages---ssdt-for-vs-2015"></a>使用できる言語 - SSDT for VS 2015
  
**SSDT for VS 2015** の今回のリリースは、次の言語でインストールできます。  

[中国語 (中華人民共和国)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x804) | 
[中国語 (台湾)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x404) | 
[英語 (米国)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x409) | 
[フランス語]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x40c)  
[ドイツ語]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x407) | 
[イタリア語]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x410) | 
[日本語]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x411) | 
[韓国語]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x412) | 
[ポルトガル語 (ブラジル)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x416) | 
[ロシア語]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x419) | 
[スペイン語]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x40a)  

### <a name="iso-images---ssdt-for-vs-2015"></a>ISO イメージ - SSDT for VS 2015

SSDT のインストールまたは管理者用インストール ポイントのセットアップの代替方法として、SSDT の ISO イメージを使用できます。 この ISO イメージは、SSDT に必要なすべてのコンポーネントが含まれた自己完結型ファイルであり、ダウンロード マネージャーを使用してダウンロードできます。ダウンロード マネージャーは再開可能であるため、ネットワークの帯域幅が限られている場合や信頼性が低い場合に便利です。 ダウンロードが完了したら、ISO イメージはドライブとしてマウントすることも、DVD に書き込むこともできます。

> [!NOTE]
> VS 2015 17.4 ISO イメージの SSDT が使用可能になりました。

[中国語 (中華人民共和国)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x804) |
[中国語 (台湾)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x404) |
[英語 (米国)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x409) |
[フランス語]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x40c)  
[ドイツ語]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x407) |
[イタリア語]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x410) |
[日本語]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x411) |
[韓国語]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x412) |
[ポルトガル語 (ブラジル)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x416) |
[ロシア語]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x419) |
[スペイン語]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x40a)



## <a name="supported-sql-versions"></a>サポートされる SQL のバージョン
  
|プロジェクト テンプレート|サポートされている SQL プラットフォーム|  
|-------------------|--------------------|  
リレーショナル データベース|  SQL Server 2005* - SQL Server 2017<br> (SSDT 17.x または SSDT for Visual Studio 2017 を使って、[SQL Server on Linux](../linux/sql-server-linux-overview.md) に接続します)<br /><br />Azure SQL データベース<br /><br />Azure SQL Data Warehouse (クエリのみサポートします。データベース プロジェクトはまだサポートされていません)<br /><br />  * SQL Server 2005 のサポートは非推奨とされます。<br /><br /> 正式にサポートされている SQL バージョンに移行してください。|
  |Analysis Services モデル<br /><br />Reporting Services レポート | SQL Server 2008 – SQL Server 2017|
  |Integration Services パッケージ| SQL Server 2012 – SQL Server 2017    |
  
## <a name="dacfx"></a>DacFx
SSDT for Visual Studio 2015 と SSDT for Visual Studio 2017 は両方とも DacFx 17.4.1 を使用: [Data-Tier Application Framework (DacFx) 17.4.1 をダウンロードする](https://www.microsoft.com/download/details.aspx?id=56508)。


## <a name="next-steps"></a>次の手順  
SSDT をインストールした後、次のチュートリアルを使用して、SSDT を使ったデータベース、パッケージ、データ モデル、およびレポートの作成方法を学ぶことができます。  

- [プロジェクト指向のオフライン データベース開発](project-oriented-offline-database-development.md)  
- [SSIS チュートリアル: 簡単な ETL パッケージの作成](../integration-services/ssis-how-to-create-an-etl-package.md)  
- [Analysis Services チュートリアル](../analysis-services/analysis-services-tutorials-ssas.md)  
- [基本的なテーブル レポートの作成 (SSRS チュートリアル)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]


## <a name="see-also"></a>参照  
[SSDT MSDN フォーラム](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[SSDT チーム ブログ](http://blogs.msdn.com/b/ssdt/)  
[DACFx API リファレンス](https://msdn.microsoft.com/library/dn645454.aspx)  
[SQL Server Management Studio (SSMS) のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)  