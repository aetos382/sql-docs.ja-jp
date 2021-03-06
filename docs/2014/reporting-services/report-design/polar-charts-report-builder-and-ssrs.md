---
title: 極座標グラフ (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c9402d8f-202a-4cdf-949e-50f5b1d2b885
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: d59ad6ad8059e7261054470c310d8fd82dbd88d3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37208488"
---
# <a name="polar-charts-report-builder-and-ssrs"></a>極座標グラフ (レポート ビルダーおよび SSRS)
  極座標グラフでは、カテゴリ別にグループ化されたポイントのセットとして、360°の円上に系列が表示されます。 値は、円の中心からポイントまでの距離で表されます。 ポイントが中心から遠いほど、その値は大きくなります。 カテゴリのラベルは、グラフの周囲に表示されます。 極座標グラフにデータを追加する方法の詳細については、次を参照してください。[グラフ&#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a>バリエーション  
  
-   **レーダー チャート**: レーダー チャートでは、系列が円形の線または領域で表示されます。 極座標グラフとは異なり、レーダー チャートでは、極座標の観点ではデータが表示されません。  
  
## <a name="data-considerations-for-polar-charts"></a>極座標グラフのデータに関する注意点  
  
-   レーダー チャートは、複数の系列のカテゴリ データを比較する場合に役立ちます。  
  
-   極座標グラフは、極データをグラフ化する際に最もよく使用されます。ここでは、各データ ポイントが角度や距離によって決まります。  
  
-   極座標グラフは、同じグラフ領域内で他の種類のグラフと組み合わせることはできません。  
  
## <a name="example"></a>例  
 次の例では、レーダー チャートの使用方法を示します。 次の表は、チャートのサンプル データを示しています。  
  
|名前|売上|  
|----------|-----------|  
|低木|61|  
|種|78|  
|球根|60|  
|木|38|  
|花|81|  
  
 この例では、名前フィールドがカテゴリ グループ領域に配置されます。 売上フィールドは値領域に配置されます。 売上フィールドをドロップすると、グラフの売上フィールドが自動的に計算されます。 レーダー チャートでは、売上フィールド内の値の数に基づいて、ラベルを配置する場所が計算されます。ここでは、5 つの値が含まれているため、円周上で等間隔に設定された 5 つの点にラベルが配置されます。 売上フィールドに 3 つの値が含まれている場合、円周上で等間隔に設定された 3 つの点にラベルが配置されます。  
  
 次の図は、提示されたデータに基づくレーダー チャートの例を示しています。  
  
 ![レーダー チャート](../media/rs-radarchart.gif "レーダー チャート")  
  
## <a name="see-also"></a>参照  
 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [グラフの書式設定 (レポート ビルダーおよび SSRS)](formatting-a-chart-report-builder-and-ssrs.md)   
 [グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](chart-types-report-builder-and-ssrs.md)   
 [折れ線グラフ &#40;レポート ビルダーおよび SSRS&#41;](line-charts-report-builder-and-ssrs.md)   
 [空にして、Null データ ポイントのグラフで&#40;レポート ビルダーおよび SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
