---
title: Microsoft Connectors for Oracle and Teradata by Attunity (SSIS) | Microsoft Docs
ms.date: 05/16/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b72d8b374df110a85221137302b8247b29acd95a
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35331536"
---
# <a name="microsoft-connectors-for-oracle-and-teradata-by-attunity-for-integration-services-ssis"></a>Integration Services (SSIS) 用の Microsoft Connectors for Oracle and Teradata by Attunity

SSIS パッケージでの Oracle または Teradata との間でデータを読み込むときのパフォーマンスを最適化する Attunity による Integration Services 用のコネクタをダウンロードできます。

## <a name="download-the-latest-attunity-connectors"></a>最新の Attunity コネクタをダウンロードする

最新バージョンのコネクタは次の場所から入手できます。  
[Microsoft Connectors v5.0 for Oracle and Teradata](https://www.microsoft.com/download/details.aspx?id=55179)

## <a name="issue---the-attunity-connectors-arent-visible-in-the-ssis-toolbox"></a>問題 - Attunity コネクタが SSIS ツールボックスに表示されない

SSIS ツールボックスに Attunity コネクタを表示するには常に、お使いのコンピューターにインストールされている SQL Server Data Tools (SSDT) と同じバージョンの SQL Server が対象になっているコネクタのバージョンをインストールする必要があります  (以前のバージョンのコネクタもインストールされている場合があります)。この要件は、SSIS プロジェクトとパッケージで対象になっている SQL Server のバージョンとは関係ありません。

たとえば、最新バージョンの SSDT をインストールしてある場合、SSDT のバージョンは 17 で、ビルド番号は 14 で始まっています。 このバージョンの SSDT では、SQL Server 2017 のサポートさ追加されます。 SSIS パッケージの開発で Attunity コネクタを表示および使用するには、以前のバージョンの SQL Server を対象にする場合であっても、最新バージョンの Attunity コネクタ (バージョン 5.0) をインストールする必要があります。 このバージョンのコネクタも、SQL Server 2017 のサポートを追加します。

Visual Studio の **[ヘルプ]** | **[Microsoft Visual Studio のバージョン情報]** またはコントロール パネルの **[プログラムと機能]** で、インストールされている SSDT のバージョンを確認します。 その後、次の表から対応するバージョンの Attunity コネクタをインストールします。

|SSDT のバージョン|SSDT のビルド番号|対象の SQL Server のバージョン|必要なコネクタのバージョン|
|---------|---------|---------|---------|
|17|14 で始まる値|SQL Server 2017|[Microsoft Connectors v5.0 for Oracle and Teradata](https://www.microsoft.com/download/details.aspx?id=55179)|
|16|13 で始まる値|SQL Server 2016|[Microsoft Connectors v4.0 for Oracle and Teradata](https://www.microsoft.com/download/details.aspx?id=52950)|
||||

## <a name="download-the-latest-sql-server-data-tools-ssdt"></a>最新の SQL Server Data Tools (SSDT) をダウンロードする

最新バージョンの SSDT を次の場所から入手します。  
[SQL Server Data Tools (SSDT) のダウンロード](..//ssdt/download-sql-server-data-tools-ssdt.md)
