---
title: SAP NetWeaver BI の接続の種類 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f985856b-31d5-4e56-844b-8a8ee38da67e
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b05c961fcd9d3a4a64715f6bc96754000969a6ca
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37216882"
---
# <a name="sap-netweaver-bi-connection-type-ssrs"></a>SAP NetWeaver BI の接続の種類 (SSRS)
  SAP NetWeaver® Business Intelligence の外部データ ソースのデータをレポートに含めるには、種類が [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)]のレポート データ ソースに基づいたデータセットが必要です。 このビルトイン データ ソースの種類は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework Data Provider 1.0 for [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)]のデータ拡張機能に基づいています。  
  
 このデータ拡張機能を使用すると、 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] の外部データ ソースで定義された InfoCube、MultiProvider (仮想 InfoCube)、および Web 対応クエリから多次元データを取得できます。  
  
 このトピックの情報を使用して、データ ソースを構築してください。 手順については、次を参照してください。[データ接続またはデータ ソース追加および確認&#40;レポート ビルダーおよび SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)します。  
  
##  <a name="support"></a> サポートされているバージョン  
 SAP BW 3.5 および 7.0 に対して、データ プロバイダーが開発され、テストが実施されています。  
  
-   SAP BW 3.5 および 7.0 の サポート パッケージ 20  
  
 次のシステムに対して、Windows 統合認証用のプロバイダーが開発され、テストが実施されています。  
  
-   SAP Portals 6.40 サポート パッケージ 20  
  
-   7.0 のポータル サポート パッケージ 11 を SAP します。  
  
-   SAP Duet 1.0  
  
##  <a name="Connection"></a> 接続文字列  
 データ ソースに接続するときに使用する接続情報および資格情報については、データベース管理者に問い合わせてください。 次の接続文字列では、8000 番ポートを使用してサーバー上の [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] データ ソースを指定し、SOAP を使用してインターネット経由の XML for Analysis Services (XMLA) を指定しています。  
  
```  
DataSource=http://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla  
```  
  
 接続文字列の例の詳細については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」を参照してください。  
  
  
  
##  <a name="Credentials"></a> [資格情報]  
 クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。  
  
 レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。  
  
 詳細については、次を参照してください。[データ接続、データ ソース、および Reporting Services の接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)または[レポート ビルダーでの資格情報の指定](../specify-credentials-in-report-builder.md)します。  
  
  
  
##  <a name="Query"></a> クエリ  
 グラフィカル クエリ デザイナーのデザイン モードまたはクエリ モードを使用すると、データ ソース上の基になるデータ構造を参照しながら、多次元式 (MDX) クエリを作成できます。 デザイン時には、クエリ デザイナーから対話的にクエリを実行して結果を確認することができます。 作成したクエリによって、データセットのフィールドが定義されます。 実行時には、データ ソースから実際のデータが返されます。 グラフィカル クエリ デザイナーでは、次の操作を実行できます。  
  
-   デザイン モードでは、ディメンション、メンバー、メンバーのプロパティ、主要データなどを、データ ソースからデータ ペインにドラッグして、多次元式 (MDX) クエリを作成できます。 計算されるメンバー ペインから、計算されるメンバーをデータ ペインにドラッグして、追加のデータセット フィールドを定義できます。  
  
-   クエリ モードでは、ディメンション、メンバー、メンバーのプロパティ、主要データなどをクエリ ペインにドラッグするか、MDX テキストを直接クエリ ペインに入力できます。 計算されるメンバー ペインから、計算されるメンバーをデータ ペインにドラッグして、追加のデータセット フィールドを定義できます。  
  
 クエリを作成すると、クエリ デザイナーは MDX クエリに既定のプロパティを自動的に追加します。 既定のプロパティ以外のプロパティを含めるには、MDX クエリを手動で変更する必要があります。  
  
 関連付けられているクエリ デザイナーについて詳しくは、「[SAP NetWeaver BI Query Designer のユーザー インターフェイス&#40;レポート ビルダー&#41;](../sap-netweaver-bi-query-designer-user-interface-report-builder.md)」をご覧ください。  
  
  
  
##  <a name="Extended"></a> 拡張フィールド プロパティ  
 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] データ ソースは、拡張フィールド プロパティをサポートしています。 拡張フィールド プロパティに追加するは`Value`と`IsMissing`データ処理拡張機能によってデータセットのフィールド定義されています。 拡張プロパティには、定義済みプロパティとカスタム プロパティがあります。 定義済みのプロパティは、複数のデータ ソースに共通のプロパティです。 カスタム プロパティは、各データ ソースの固有のプロパティです。  
  
### <a name="working-with-field-properties"></a>フィールド プロパティの操作  
 拡張フィールド プロパティは、レポート レイアウトにドラッグすることのできるアイテムとして [レポート データ] ウィンドウには表示されません。 代わりに、プロパティの親フィールドをレポートにドラッグして、既定のプロパティを変更し、`Value`を使用するプロパティ。 たとえば、MDX クエリ デザイナーで、メタデータ ペインからクエリ ペインにレベルをドロップすることによって **Calendar Year/Month Level 01** というフィールド名を作成した場合、カスタムの拡張プロパティ **Long Name** を式の中で参照するには、次の構文を使用します。  
  
 `=Fields!Calendar_Year_Month_Level_01("Long Name")`  
  
 メタデータ ペインでフィールドにカーソルを合わせると、拡張フィールド プロパティの名前がツールヒントに表示されます。 基になるデータを探索に使用できるクエリ デザイナーの詳細については、次を参照してください。 [SAP NetWeaver BI Query Designer User Interface](sap-netweaver-bi-query-designer-user-interface.md)します。  
  
> [!NOTE]  
>  拡張フィールド プロパティに対応する値が存在するのは、レポートを実行して対応するデータセットのデータを取得する際に、データ ソースによって値が提供された場合のみです。 参照できます`Field`以下に示す構文を使用して任意の式からプロパティ値。 ただし、これらのフィールドはこのデータ プロバイダーに固有であり、レポート定義言語には含まれないため、これらの値に加えた変更はレポート定義には保存されません。  
  
 定義済みの拡張プロパティを式の中で参照するには、次のいずれかの構文を使用します。  
  
-   *Fields!FieldName.PropertyName*  
  
-   *Fields!FieldName("PropertyName")*  
  
 カスタム拡張プロパティを式の中で参照するには、次の構文を使用します。  
  
-   *Fields!FieldName("PropertyName")*  
  
  
  
### <a name="predefined-field-properties"></a>定義済みフィールド プロパティ  
 次の表に、 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] データ ソースで使用できる定義済みフィールド プロパティの一覧を示します。  
  
|**プロパティ**|**型**|**説明/有効値**|  
|------------------|--------------|---------------------------------------|  
|`Value`|`Object`|フィールドのデータ値を指定します。|  
|`IsMissing`|`Boolean`|フィールドが結果データセットに存在するかどうかを示します。|  
|`FormattedValue`|`String`|主要データの書式設定した値を返します。|  
|`BackgroundColor`|`String`|データベースで定義されたフィールドの背景色を返します。|  
|`Color`|`String`|データベースで定義されたアイテムの前景色を返します。|  
|`Key`|`Object`|レベルのキーを返します。|  
|`LevelNumber`|`Integer`|親子階層の場合は、レベル番号またはディメンション番号を返します。|  
|`ParentUniqueName`|`String`|親子階層の場合は、親レベルの完全修飾名を返します。|  
|`UniqueName`|`String`|レベルの完全修飾名を返します。 たとえば、`UniqueName`従業員の値は *[0D_Company]. [10D_Department]。[11]*.|  
  
 フィールドおよびフィールド プロパティを式で使用する方法について詳しくは、「[式で使用される組み込みコレクション &#40;レポート ビルダーおよび SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)」をご覧ください。  
  
  
  
##  <a name="Remarks"></a> 解説  
 このデータ プロバイダーでは使用できないレポート配信モードもあります。 このデータ処理拡張機能では、データ ドリブン サブスクリプションを使ったレポートの配信はサポートされません。 詳細については、「[サブスクライバー データに対して外部データ ソースを使用する (データ ドリブン サブスクリプション)](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)」を参照してください。  
  
 詳しくは、「 [Using SQL Server 2008 Reporting Services with SAP NetWeaver Business Intelligence (SAP NetWeaver Business Intelligence で SQL Server 2008 Reporting Services を使用する)](http://go.microsoft.com/fwlink/?LinkId=167352)」をご覧ください。  
  
  
  
##  <a name="HowTo"></a> 操作方法に関するトピック  
 データ接続、データ ソース、およびデータセットを操作する手順について説明します。  
  
 [データ接続またはデータ ソース追加および確認&#40;レポート ビルダーおよび SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [データセットへのフィルターの追加 (レポート ビルダーおよび SSRS)](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
  
##  <a name="Related"></a> 関連項目  
 次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義し、カスタマイズし、使用する方法が説明されています。  
  
 [レポートにデータを追加&#40;レポート ビルダーおよび SSRS&#41;](report-datasets-ssrs.md)  
 レポートのデータへのアクセスの概要について説明します。  
  
 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 データ接続とデータ ソースについて説明します。  
  
 [レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 埋め込みデータセットと共有データセットについて説明します。  
  
 [データセット フィールド コレクション (レポート ビルダーおよび SSRS)](dataset-fields-collection-report-builder-and-ssrs.md)  
 クエリによって生成されるデータセット フィールド コレクションについて説明します。  
  
 [Reporting Services でサポートされるデータ ソース&#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
 各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。  
  
 
  
## <a name="see-also"></a>参照  
 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
