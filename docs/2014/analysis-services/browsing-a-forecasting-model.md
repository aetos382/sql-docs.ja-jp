---
title: 予測モデルの参照 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- forecasting [data mining]
- mining models, viewing
- mining model, time series
- time series [data mining]
ms.assetid: ad35a528-1949-4048-8678-3b9760c1c88c
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d23900aac442e72e89daea72fc0c2e07df9bd934
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224632"
---
# <a name="browsing-a-forecasting-model"></a>予測モデルの参照
  使用して予測モデルを開く**参照**では、タイム シリーズ モデル ビューアーに似たの対話型ビューアーにモデルが表示されます[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]します。 ビューアーは、傾向の調査、系列の比較、予測の作成、およびモデルと基になるデータに関する情報の取得に役立ちます。  
  
##  <a name="bkmk_Top"></a> モデルを調査します。  
 **参照**予測モデルのビューアーには、グラフ ビューを時間の経過と共に、傾向を示し、予測を作成することができ、時系列を表す、デシジョン ツリーまたは回帰ツリーとしてモデル ビューが用意されています。  
  
-   [グラフ ビュー](#bkmk_charts)  
  
-   [モデル ビュー](#bkmk_Model)  
  
 予測モデルをテストする、サンプル データ ブックの [予測] タブで、サンプル データを使用してタイム シリーズ モデルを使用して、ビルド、[予測ウィザード&#40;Excel 用データ マイニング アドインで&#41;](forecast-wizard-data-mining-add-ins-for-excel.md) 、で**データ マイニング**リボン、または[予測&#40;Excel 用テーブル分析ツール&#41;](forecast-table-analysis-tools-for-excel.md)で、**分析**リボンです。  
  
###  <a name="bkmk_charts"></a> グラフ  
 **グラフ** タブは、予測値と共に、時間の経過と共に、データ系列における傾向を表示します。 グラフの縦軸は時系列の値を表し、横軸は時間を表します。  
  
##### <a name="explore-the-forecasting-chart"></a>予測チャートの調査  
  
1.  このモデルには複数の時系列が含まれていますが、グラフを見やすくするために、時系列を 1 つだけ表示することも、数個の関連系列だけを表示することもできます。  
  
     ![予測モデルの履歴予測](media/dm13-forecast-chart-historicpredictions.gif "予測モデルの履歴予測")  
  
     チェック ボックスを使用して、北米のみと売上高のみの予測を選択します。  
  
2.  クリックして**予測期間**と数の将来の時刻値を制御する新しい値がグラフに表示する型。  
  
     既定は 5 です。  
  
3.  任意の時点で、過去または将来に表示されるには、その時点の正確な値を表示する行をクリックして、**マイニング凡例**します。  
  
4.  グラフには、履歴データと将来のデータの両方が表示されます。 背景に影の付いた点線に注目します。 これらの値は、モデルに基づいた将来の予測です。  
  
     (モデルの作成に使用した) 履歴データがグラフの左側に表示されます。  
  
5.  選択、**予測の履歴を表示する**時系列の安定性を把握するにはオプションです。  
  
     ![モデルの 1 つの系列の予測](media/dm13-forecast-chart-singleseries.gif "モデル内の 1 つの系列の予測")  
  
     履歴予測は、実際の履歴値と比較される、その時点への系列に基づいて予測された値です。 点線 (予測値) が実線 (実際の値) から大きくかけ離れている場合は、系列の最初の部分で後に続く値が正確に予測されていないことを意味します。 さらに多くのデータが必要になるか、サイクルの変動率を示すだけになる可能性があります。  
  
6.  選択、**偏差の表示**グラフに誤差範囲を表示します。  
  
     誤差範囲により、予測のばらつきを視覚的に評価できます。 予測の品質は、ソース データによって異なりますが、予測期間の数が増えるにつれて、偏差が徐々に大きくなることがわかります。  
  
 **ヒント**  
  
-   表示を切り替える、**マイニング凡例**、任意の時点で、グラフを右クリックします。  
  
     特定の時間範囲を表示するには、グラフをクリックし、グラフ上で時間の選択をドラッグし、再びクリックして選択した範囲を拡大します。  
  
-   現在のグラフのコピーを取得するには、次のようにクリックします。 **Excel にコピー**、Excel のワークシートを順にクリックします。 設定したすべてのオプション (凡例など) を使用して、シートにグラフィックが挿入されます。  
  
     ただし、このグラフィックは静的なので、凡例を編集したり、基になるデータを表示したりすることはできません。使用して、対話的なグラフ ビューが必要な場合、 [Visio のビューアー](viewing-data-mining-models-in-visio-data-mining-add-ins.md)します。  
  
-   クリックして**Abs**絶対と相対曲線を切り替えるビューアーのメニュー バーでします。  
  
     このオプションは、グラフに複数のモデルが含まれている場合に役立ちますが、各モデルのデータのスケールが大きく異なります。  
  
     たとえば、太平洋地域の店舗が新規オープンして売上が低かった場合や、絶対値が使用されている場合、他のモデルはより標準的なスケールで表示されますが、大西洋地域の売上を示す線は平坦になり、実際の変化がわかりにくくなることがあります。  
  
     相対値を使用するようにビューを切り替えると、異なるモデルのスケールを正規化し、違いを変化の割合として表示できます。 変化が各モデルに対して相対的である場合、これらのモデルを大きな歪みがない状態で同じグラフに表示できます。  
  
 [モデルを調査します。](#bkmk_Top)  
  
###  <a name="bkmk_Model"></a> モデル  
 予測モデルはデシジョン ツリーとして表すこともできます。また、系列がほぼ直線状の場合は、回帰モデルとして表すことができます。  
  
 たとえば、このモデルでは、特定の条件に基づく回帰式に違いがあるため、ツリーは、それぞれ回帰式が異なる 2 つの分岐に分かれます。  
  
 ![予測モデルの 1 つの系列をフィルター処理](media/dm13-forecast-model-northamerica.gif "予測モデルの 1 つの系列をフィルター処理")  
  
##### <a name="explore-the-forecasting-model-as-a-tree"></a>予測モデルのツリーとしての調査  
  
1.  をクリックして、**ツリー**ドロップダウンして表示するモデルを選択します。  
  
     予測可能な属性ごとに個別のツリーまたは回帰ノードが表示されます。 たとえば、データにヨーロッパ、北米、および太平洋の売上が含まれている場合は、3 つの異なるモデル (データ系列ごとに 1 つ) が存在します。  
  
2.  ドラッグ、**レベルの表示**ツリーの下位レベルを除外し、最も重要な分割に集中するスライダー。  
  
3.  いくつかのわかりやすい統計を表示するには、各ノードをクリックして、**マイニング凡例**します。  
  
     ノードの上にマウス ポインターを置くと、ツールヒントにも、同様の統計情報に加えて、そのノードを説明する完全な式が表示されます。  
  
4.  情報をコピーする場合、**マイニング凡例**を右クリックし、**マイニング凡例**を選択します**コピー**、Excel ワークシート内をクリックします。 **Excel にコピー**オプションは、コピー、グラフ、統計情報ではありません。  
  
 [モデルを調査します。](#bkmk_Top)  
  
## <a name="see-also"></a>参照  
 [Excel におけるモデルの参照&#40;SQL Server データ マイニング アドイン&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
