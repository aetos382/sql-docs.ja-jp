---
title: AttributeHierarchyOptimizedState 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AttributeHierarchyOptimizedState Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeHierarchyOptimizedState
helpviewer_keywords:
- AttributeHierarchyOptimizedState element
ms.assetid: d87148c8-2011-45ae-94c3-851f48babc5f
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 59b2036773b516d3ea79cda06c51502a9d096cec
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247242"
---
# <a name="attributehierarchyoptimizedstate-element-assl"></a>AttributeHierarchyOptimizedState 要素 (ASSL)
  属性階層に適用される最適化のレベルを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute> <!-- or CubeAttribute -->  
   ...  
   <AttributeHierarchyOptimizedState>...  
   </AttributeHierarchyOptimizedState>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*FullyOptimized*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeAttribute](../data-type/cubeattribute-data-type-assl.md)、 [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*FullyOptimized*|インスタンスによって、クエリのパフォーマンスを向上させるために属性階層のインデックスが作成されます。|  
|*NotOptimized*|追加のインデックスは作成されません。|  
  
 許容された値に対応する列挙`AttributeHierarchyOptimizedState`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.OptimizationType>します。 AMO オブジェクト モデルで `AttributeHierarchyOptimizedState` の親に対応する要素は、<xref:Microsoft.AnalysisServices.CubeAttribute> および <xref:Microsoft.AnalysisServices.DimensionAttribute> です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
