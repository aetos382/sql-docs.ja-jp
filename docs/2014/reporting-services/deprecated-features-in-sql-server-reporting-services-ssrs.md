---
title: 非推奨の SQL Server 2014 における SQL Server Reporting Services の機能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
caps.latest.revision: 49
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6817f31ff83e1a502506893f66b5080399200fd8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37305142"
---
# <a name="deprecated-features-in-sql-server-reporting-services-in-sql-server-2014"></a>SQL Server 2014 における SQL Server Reporting Services の非推奨機能
  このトピックでは、非推奨とされた [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 機能について説明します。 非推奨とされたリリースで機能を引き続き使用できますが、これらの機能は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の今後のリリースで削除される予定です。 非推奨の機能を新しいアプリケーションで使用しないでください。  
  
 このトピックの内容  
  
-   [SQL Server 2014 Reporting Services の非推奨の機能](#bkmk_2014)  
  
-   [SQL Server 2012 SP1 Reporting Services の非推奨の機能](#bkmk_2012sp1)  
  
-   [SQL Server 2012 Reporting Services の非推奨の機能](#bkmk_2012)  
  
-   [SQL Server 2008 R2 Reporting Services の非推奨の機能](#bkmk_kj)  
  
##  <a name="bkmk_2014"></a> SQL Server 2014 Reporting Services の非推奨の機能  
  
### <a name="features-not-supported-in-the-next-version-of-sql-server"></a>SQL Server の次のバージョンでサポートされない機能  
 次[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]で機能はサポートされない、**次**バージョンの[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。 新規の開発作業ではこれらの機能を使用しないようにし、現在これらの機能を使用しているアプリケーションはできるだけ早く修正してください。  
  
#### <a name="html-rendering-extension-device-information-settings"></a>HTML 表示拡張機能のデバイス情報設定  
 HTML 表示拡張機能の次のデバイス情報設定は、非推奨とされます。  
  
-   ActionScript  
  
-   ActiveXControls  
  
-   GetImage  
  
-   OnlyVisibleStyles  
  
-   ReplacementRoot  
  
-   ResourceStreamRoot  
  
-   StreamRoot  
  
-   UsePx  
  
-   [ズーム]  
  
 HTML 表示拡張機能の詳細については、次を参照してください[HTML デバイス情報設定。](html-device-information-settings.md)  
  
#### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a>Microsoft Word および Microsoft Excel 1997-2003 表示拡張機能  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] BIFF8 表示拡張機能[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]にレポートを[!INCLUDE[msCoName](../includes/msconame-md.md)]Word と[!INCLUDE[msCoName](../includes/msconame-md.md)]Excel 1997-2003 バイナリ交換ファイル形式。 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 表示する拡張機能が含まれています、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 Open XML 形式。  
  
#### <a name="report-definition-language-rdl-2005-and-earlier"></a>レポート定義言語 (RDL) 2005 以前  
 レポート定義言語 (RDL) 2005 およびそれ以前のバージョンは非推奨とされます。 RDL の詳細については、次を参照してください。[レポート定義言語&#40;SSRS&#41;](reports/report-definition-language-ssrs.md)します。  
  
 レポートをアップグレードする方法の詳細については、次を参照してください。[レポートのアップグレード](install-windows/upgrade-reports.md)します。  
  
#### <a name="sql-server-2005-and-earlier-custom-report-items"></a>SQL Server 2005 およびそれ以前のバージョンのカスタム レポート アイテム  
 カスタム レポート アイテム (CRI) 用にコンパイルされた[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 およびそれ以前は非推奨とされます。  
  
#### <a name="reporting-services-snapshots-2005-and-earlier"></a>Reporting Services Snapshots 2005 およびそれ以前のバージョン  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] スナップショットの表示と[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 およびそれ以前は非推奨とされます。  
  
#### <a name="report-models"></a>レポート モデル  
 セマンティック モデリング言語 (SMDL) レポート モデルは非推奨とされます。 内のデータ ソースとして既存のレポート モデルを使用する続行できますが、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]レポート、レポートをレポート モデルへの依存関係を削除する更新を検討してください。  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] には、レポート モデルの作成または更新のためのツールは含まれません。 詳細については、次を参照してください。 [SQL Server 2014 における SQL Server Reporting Services における重大な変更](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)します。  
  
#### <a name="deprecated-methods-in-the-web-service-endpoint"></a>Web サービス エンドポイントで非推奨のメソッド  
 次の操作は非推奨、 <xref:ReportService2010.ReportingService2010> Web サービスのエンドポイント。  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
#### <a name="sharepoint-web-parts"></a>Sharepoint Web パーツ  
 インストール キャビネット ファイル **RSWebParts.cab** とその cab ファイルから抽出できる SharePoint Web パーツは非推奨とされています。 非推奨の web パーツには、レポート エクスプ ローラー (**SPExplorer.dwp**) とレポート ビューアー (**SPViewer.dwp**)。  
  
 非推奨の web パーツの詳細については、次を参照してください[ビューと探索ネイティブ モードのレポートを使用して SharePoint Web パーツ (SSRS)。](http://msdn.microsoft.com/library/ms159772.aspx)  
  
### <a name="features-not-supported-in-a-future-version-of-sql-server"></a>SQL Server の今後のバージョンでサポートされない機能  
 以下の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 機能は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の次のバージョンではサポートされますが、その後のバージョンでは削除されます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のどのバージョンであるかは決定していません。  
  
 いいえ[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]で機能が非推奨とされた[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]します。  
  
##  <a name="bkmk_2012sp1"></a> SQL Server 2012 SP1 Reporting Services の非推奨の機能  
 このセクションについて説明します[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]で非推奨の機能[!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]します。 以下の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 機能は [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]の次のバージョンではサポートされますが、その後のバージョンでは削除されます。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のどのバージョンであるかは決定していません。  
  
### <a name="sharepoint-web-parts"></a>Sharepoint Web パーツ  
 インストール キャビネット ファイル **RSWebParts.cab** とその cab ファイルから抽出できる SharePoint Web パーツは非推奨とされています。 非推奨の web パーツには、レポート エクスプ ローラー (**SPExplorer.dwp**) とレポート ビューアー (**SPViewer.dwp**)。  
  
 非推奨の web パーツの詳細については、次を参照してください[ビューと探索ネイティブ モードのレポートを使用して SharePoint Web パーツ (SSRS)。](http://msdn.microsoft.com/library/ms159772.aspx)  
  
##  <a name="bkmk_2012"></a> SQL Server 2012 Reporting Services の非推奨の機能  
 このセクションについて説明します[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]で非推奨の機能[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]します。  
  
### <a name="html-rendering-extension-device-information-settings"></a>HTML 表示拡張機能のデバイス情報設定  
 HTML 表示拡張機能の次のデバイス情報設定は、非推奨とされます。  
  
-   ActionScript  
  
-   ActiveXControls  
  
-   GetImage  
  
-   OnlyVisibleStyles  
  
-   ReplacementRoot  
  
-   ResourceStreamRoot  
  
-   StreamRoot  
  
-   UsePx  
  
-   [ズーム]  
  
 HTML 表示拡張機能の詳細については、次を参照してください[HTML デバイス情報設定。](html-device-information-settings.md)  
  
### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a>Microsoft Word および Microsoft Excel 1997-2003 表示拡張機能  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] BIFF8 表示拡張機能[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]にレポートを[!INCLUDE[msCoName](../includes/msconame-md.md)]Word と[!INCLUDE[msCoName](../includes/msconame-md.md)]Excel 1997-2003 バイナリ交換ファイル形式。 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 表示する拡張機能が含まれています、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 Open XML 形式。  
  
### <a name="report-definition-language-rdl-2005-and-earlier"></a>レポート定義言語 (RDL) 2005 以前  
 レポート定義言語 (RDL) 2005 およびそれ以前のバージョンは非推奨とされます。 RDL の詳細については、次を参照してください。[レポート定義言語&#40;SSRS&#41;](reports/report-definition-language-ssrs.md)します。  
  
 レポートをアップグレードする方法の詳細については、次を参照してください。[レポートのアップグレード](install-windows/upgrade-reports.md)します。  
  
### <a name="sql-server-2005-and-earlier-custom-report-items"></a>SQL Server 2005 およびそれ以前のバージョンのカスタム レポート アイテム  
 カスタム レポート アイテム (CRI) 用にコンパイルされた[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 およびそれ以前は非推奨とされます。  
  
### <a name="reporting-services-snapshots-2005-and-earlier"></a>Reporting Services Snapshots 2005 およびそれ以前のバージョン  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] スナップショットの表示と[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 およびそれ以前は非推奨とされます。  
  
### <a name="report-models"></a>レポート モデル  
 セマンティック モデリング言語 (SMDL) レポート モデルは非推奨とされます。 内のデータ ソースとして既存のレポート モデルを使用する続行できますが、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]レポート、レポートをレポート モデルへの依存関係を削除する更新を検討してください。  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] には、レポート モデルの作成または更新のためのツールは含まれません。 詳細については、次を参照してください。 [SQL Server 2014 における SQL Server Reporting Services における重大な変更](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)します。  
  
### <a name="deprecated-methods-in-the-web-service-endpoint"></a>Web サービス エンドポイントで非推奨のメソッド  
 次の操作は非推奨、 <xref:ReportService2010.ReportingService2010> Web サービスのエンドポイント。  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
##  <a name="bkmk_kj"></a> SQL Server 2008 R2 Reporting Services の非推奨の機能  
  
> [!NOTE]  
>  SQL Server 2008 R2 は SQL Server 2008 のマイナー バージョン アップグレードなので、SQL Server 2008 のセクションのコンテンツも確認することをお勧めします。  
  
### <a name="report-server-web-service-endpoints"></a>レポート サーバー Web サービスのエンドポイント  
 Web サービス<xref:ReportService2005.ReportingService2005>と<xref:ReportService2006.ReportingService2006>このリリースで廃止されました。 これらのエンドポイントに置換された新しいエンドポイント:<xref:ReportService2010.ReportingService2010>します。  
  
 新しいエンドポイントには、非推奨のエンドポイントで使用できるすべての機能と SQL Server 2008 R2 で導入された新しい機能が含まれています。  
  
## <a name="see-also"></a>参照  
 [新機能については&#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [旧バージョンとの互換性](../getting-started/backward-compatibility.md)   
 [SQL Server 2014 における SQL Server Reporting Services の動作変更します。](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [SQL Server 2014 で廃止された SQL Server Reporting Services の機能](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
