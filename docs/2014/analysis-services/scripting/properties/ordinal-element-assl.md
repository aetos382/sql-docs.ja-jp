---
title: Ordinal 要素 (ASSL) |Microsoft Docs
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
- Ordinal Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Ordinal
helpviewer_keywords:
- Ordinal element
ms.assetid: 64e68ad5-439c-4c1d-9df4-ee90c56761b4
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 91119d5eb5107dd691141c03a24cef7140999094
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37195942"
---
# <a name="ordinal-element-assl"></a>Ordinal 要素 (ASSL)
  キーおよび翻訳などコレクション内でバインドする序数を示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeBinding> <!-- or CubeAttributeBinding -->  
   ...  
   <Ordinal>...</Ordinal>  
   ...  
</AttributeBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Integer|  
|既定値|`0`|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeBinding](../data-type/binding-data-type-assl.md)、 [CubeAttributeBinding](../data-type/cubeattributebinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `AttributeBinding` `CubeAttributeBinding`いる要素、[型](type-element-binding-assl.md)プロパティがいずれかに*キー*または*翻訳*のコレクションにさらにバインドされている属性にバインドできますソース ビューのデータの列。 `Ordinal` 要素の値によって、そのコレクション内で、`AttributeBinding` または `CubeAttributeBinding` が参照する列が決まります。  
  
 親に対応する要素`Ordinal`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.AttributeBinding>と<xref:Microsoft.AnalysisServices.CubeAttributeBinding>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
