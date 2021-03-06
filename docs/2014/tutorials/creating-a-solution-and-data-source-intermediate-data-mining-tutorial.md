---
title: ソリューションとデータ ソース (中級者向けデータ マイニング チュートリアル) の作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0488b231-1045-4169-aabb-c1005d86ca30
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 22bfe87f9d0cd09d2d7c7f650d500398b936cde0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37216242"
---
# <a name="creating-a-solution-and-data-source-intermediate-data-mining-tutorial"></a>ソリューションとデータ ソースの作成 (中級者向けデータ マイニング チュートリアル)
  データ マイニングを使用するプロジェクトを最初に作成する必要があります[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、テンプレートを使用して**Analysis Services 多次元およびデータ マイニング プロジェクト**します。 テンプレートを開くと、データ ソース、マイニング構造、マイニング モデル、さらにマイニング構造で多次元データが使用される場合はキューブまで、データ マイニングに必要なすべてのスキーマがデザイナーに読み込まれます。  
  
 プロジェクトを作成すると、ソリューションは配置されるまでローカル ファイルとして保存されます。 ソリューションを展開するときに[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]探し、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]サーバー プロジェクトのプロパティで指定され、新たに作成[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]プロジェクトと同じ名前のデータベース。 既定では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]を使用して、 **localhost**プロジェクトの新しいインスタンス。 名前付きインスタンスを使用している場合、または既定のインスタンスに別の名前を指定した場合は、プロジェクトの配置データベース プロパティを、データ マイニング オブジェクトを作成する場所に変更する必要があります。  
  
 詳細については[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]プロジェクトを参照してください[Analysis Services プロジェクトの作成&#40;SSDT&#41;](../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)します。  
  
### <a name="to-create-a-new-analysis-services-project-for-this-tutorial"></a>このチュートリアル用の新しい Analysis Services プロジェクトを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を開きます。  
  
2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
3.  **[インストールされているテンプレート]** ペインの **[Analysis Services 多次元およびデータ マイニング プロジェクト]** をクリックします。  
  
4.  **[名前]** ボックスに、新しいプロジェクトの名前「 **DM Intermediate**」を入力します。  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored-optional"></a>データ マイニング オブジェクトを格納するインスタンスを変更するには (オプション)  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の**プロジェクト** メニューのをクリックして**プロパティ**です。  
  
2.  **[プロパティ ページ]** ペインの左側で、 **[配置]** をクリックします。  
  
3.  **サーバー名** が **localhost**であることを確認します。 別のインスタンスを使用する場合は、インスタンスの名前を入力します。 名前付きインスタンスを使用している場合[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]コンピューター名と、インスタンス名を入力します。 [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-deployment-properties-for-a-project-optional"></a>プロジェクトの配置プロパティを変更するには (オプション)  
  
1.  ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[プロパティ]** をクリックします。  
  
     または  
  
     [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の**プロジェクト**メニューの **プロパティ**です。  
  
2.  **[プロパティ ページ]** ペインの左側で、 **[配置]** をクリックします。  
  
     **[オプション]** ペインで **[配置モード]** をクリックし、上書きする場合はオプションを **[すべて配置]** に設定し、オブジェクトを更新するかオブジェクトを追加する場合は **[変更のみを配置]** に設定します。  
  
## <a name="creating-a-data-source"></a>データ ソースの作成  
 基本的なデータ マイニング チュートリアルで作成した、*データソース*への接続情報を格納する、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]データベース。 このソリューションでは、同じ手順で [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データ ソースを作成します。  
  
#### <a name="to-create-a-data-source"></a>データ ソースを作成するには  
  
-   [データ ソースを作成する&#40;基本的なデータ マイニング チュートリアル&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
 1 つのデータ ソースで複数のデータ ソース ビューをサポートできます。また、各データ ソース ビューには複数のテーブルを含めることができます。 ただし、データ ソースおよびデータ ソース ビューに配置されるため、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]なテーブルのみ各データ ソース ビューに含める必要があります、ベスト プラクティスとして、作成したデータ マイニング モデルと共にデータベースデータ マイニング モデルまたはモデルのグループごとに必要なのです。  
  
 以降のレッスンでは、それぞれの新しいシナリオをサポートするデータ ソース ビューを追加します。 マーケット バスケットのレッスンとシーケンス クラスターのレッスンのみ、同じデータ ソース ビューを使用します。それ以外は、各シナリオは異なるデータ ソース ビューを使用するため、各レッスンは互いに無関係であり、別々に実行できます。  
  
|シナリオ|データ ソース ビューに含まれているデータ|  
|--------------|-------------------------------------------|  
|[レッスン 2: 予測シナリオの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)|単一のビューとして収集された、各地域での各自転車モデルの月間の売上レポート。|  
|[レッスン 3: マーケット バスケット シナリオの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)|顧客注文の一覧を含むテーブルと、各顧客の購入記録を示す入れ子になったテーブル。|  
|[レッスン 4: シーケンス クラスター シナリオの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)|マーケット バスケット分析に使用したものと同じデータに、品目の購入順序を示す識別子が追加されています。|  
|[レッスン 5: ニューラル ネットワーク モデルとロジスティック回帰モデルの構築&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)|コール センターのいくつかの事前パフォーマンス追跡データを含む単一のテーブル。|  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 2: 予測シナリオの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [データ マイニング プロジェクト](../../2014/analysis-services/data-mining/data-mining-projects.md)   
 [多次元モデルのデータ ソース ビュー](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
