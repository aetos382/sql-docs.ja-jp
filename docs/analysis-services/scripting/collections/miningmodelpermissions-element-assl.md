---
title: "MiningModelPermissions 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MiningModelPermissions Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MiningModelPermissions
helpviewer_keywords:
- MiningModelPermissions element
ms.assetid: 6cbcf029-9627-4839-9fc5-15e58e1ba0c3
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: be60e2640a774e4decc036e7205172e3e140fc5b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="miningmodelpermissions-element-assl"></a>MiningModelPermissions 要素 (ASSL)
  権限のコレクションが含まれています、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningModel>  
   ...  
   <MiningModelPermissions>  
      <MiningModelPermission xsi:type="Permission">...</MiningModelPermission>  
   </MiningModelPermissions>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|子要素|[MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md)型の[権限](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.MiningModelPermissionCollection>します。  
  
## <a name="see-also"></a>参照  
 [Permission データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [コレクション & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  