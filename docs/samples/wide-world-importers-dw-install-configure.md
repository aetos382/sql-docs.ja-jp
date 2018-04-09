---
title: WideWorldImporters OLAP サンプル データベースのインストールし、構成の SQL |Microsoft ドキュメント
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: samples
ms.technology:
- samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
author: BarbKess
ms.author: barbkess
manager: craigg
robots: noindex,nofollow
ms.workload: On Demand
ms.openlocfilehash: e4328da10d2ec51083f3b1dbc23d6b0f5fa5da21
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2018
---
# <a name="wideworldimportersdw-installation-and-configuration"></a>WideWorldImportersDW インストールと構成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
WideWorldImportersDW データベースのインストールと構成の手順です。

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (またはそれ以降) または[Azure SQL Database](https://azure.microsoft.com/services/sql-database/)です。 サンプルの完全バージョンを使用するのには、SQL Server Evaluation/Developer または Enterprise Edition を使用します。
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md)。 最良の結果は、2016 年 6 月リリースを使用またはそれ以降。

## <a name="download"></a>ダウンロード

サンプルの最新リリース。

[wide-world-importers-release](http://go.microsoft.com/fwlink/?LinkID=800630)

SQL Server または Azure SQL データベースのエディションにサンプル WideWorldImportersDW データベースのバックアップ/bacpac には、対応するをダウンロードします。

サンプル データベースを再作成するソース コードは、次の場所から使用可能なです。 データ カタログの作成は、OLTP データベース (WideWorldImporters) から ETL に基づいていることに注意してください。

[wide-world-importers-source](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-dw-database-scripts)

## <a name="install"></a>インストール


### <a name="sql-server"></a>SQL Server

SQL Server インスタンスにバックアップを復元するには、Management Studio を使用できます。

1. SQL Server Management Studio を開き、対象の SQL Server インスタンスに接続します。
2. 右クリックし、**データベース**ノード、および選択**Restore Database**です。
3. 選択**デバイス**、ボタンをクリック**しています.**
4. ダイアログ ボックスで**バックアップ デバイスの選択**、 をクリックして**追加**データベースのバックアップをサーバーのファイル システムに移動し、バックアップを選択します。 **[OK]**をクリックします。
5. 必要な場合は、データのターゲットの場所を変更し、で、ログ ファイル、**ファイル**ウィンドウです。 ベスト プラクティスにデータを配置し、ログ ファイルを別のドライブにあることに注意してください。
6. **[OK]**をクリックします。 データベースの復元が開始されます。 それが完了した後、データベース、SQL Server インスタンスにインストールされている WideWorldImporters があります。

### <a name="azure-sql-database"></a>Azure SQL Database

新しい SQL データベースに bacpac をインポートするには、Management Studio を使用できます。

1. (省略可能)Azure で SQL Server がいない場合に移動、 [Azure ポータル](https://portal.azure.com/)し、新しい SQL データベースを作成します。 途中でデータベースを作成、サーバーを作成します。 サーバーのメモしてをおきます。
   - 参照してください[このチュートリアル](https://azure.microsoft.com/documentation/articles/sql-database-get-started/)分単位でデータベースを作成するには
2. SQL Server Management Studio を開き、Azure 内のサーバーに接続します。
3. 右クリックし、**データベース**ノード、および選択**データ層アプリケーションのインポート**です。
4. **設定のインポート**選択**ローカル ディスクからインポート**し、ファイル システムから、サンプル データベースの bacpac を選択します。
5. **データベース設定**するデータベースの名前を変更*WideWorldImportersDW*しを使用するターゲットのエディションやサービスの目標を選択します。
6. をクリックして**[次へ]**と**完了**展開を開始します。 完了するまで数分をかかります。 S2 より低いサービス目標を指定する場合は長くかかる場合があります。

## <a name="configuration"></a>構成

[SQL Server 2016 (およびそれ以降) の Developer、Evaluation、/Enterprise Edition に適用されます]

サンプル データベースは、PolyBase Hadoop または Azure blob ストレージ内のクエリ ファイルを使用することです。 ただし、既定では SQL Server とその機能がインストールされていません - SQL Server のセットアップ中に選択する必要があります。 そのため、インストール後の手順が必要です。

1. SQL Server Management Studio で WideWorldImportersDW データベースに接続し、新しいクエリ ウィンドウを開きます。
2. データベースでの PolyBase の使用を有効にするのには、次の T-SQL コマンドを実行します。

   EXECUTE [Application].[Configuration_ApplyPolyBase]