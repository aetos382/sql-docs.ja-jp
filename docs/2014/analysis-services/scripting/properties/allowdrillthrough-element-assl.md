---
title: AllowDrillThrough 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AllowDrillThrough Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AllowDrillThrough
helpviewer_keywords:
- AllowDrillThrough element
ms.assetid: 53c9e4a3-a376-447d-a13f-80d845cc9789
caps.latest.revision: 51
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f98b16569c3a7f4ab136be291d7bfd45698b5b11
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178869"
---
# <a name="allowdrillthrough-element-assl"></a>AllowDrillThrough 要素 (ASSL)
  親要素に対してドリルスルーが許可されているかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningModel> <!-- or MiningModelPermission -->  
<!-- or MiningStructurePermission -->   ...  
   <AllowDrillThrough>...</AllowDrillThrough>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|`False`|  
|Cardinality|0-1:省略可能な要素で、出現する場合は 1 回だけの出現が可能です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningModel 要素](../objects/miningmodel-element-assl.md)、 [MiningModelPermission](../objects/miningmodelpermission-element-assl.md)、 [MiningStructurePermission](../objects/miningstructurepermission-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`AllowDrillThrough`分析管理オブジェクト (AMO) オブジェクト モデルは、 <xref:Microsoft.AnalysisServices.MiningModel>、 <xref:Microsoft.AnalysisServices.MiningModelPermission>、および<xref:Microsoft.AnalysisServices.MiningStructurePermission>します。  
  
## <a name="drillthrough-on-mining-structures"></a>マイニング構造でのドリルスルー  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]を定義できます`AllowDrillthrough`マイニング構造とマイニング モデルのアクセス許可。 この権限をロールに割り当てると、そのロールのメンバーはデータ マイニング モデルにクエリを実行し、モデルに含まれていない構造列を返すことができます。 たとえば、顧客キー、顧客の収入、および顧客が購入した製品の列のみを使用するモデルを作成します。 モデルでドリルスルーを有効にすると、ユーザーは、顧客の電子メールや名前など、マイニング構造の他の列の情報を返すことができます。  
  
 したがって、機密データを保護するために、列をマイニング構造に追加する場合は注意が必要です。 また、構造には必要な場合にだけ `AllowDrillthrough` 権限を付与してください。  
  
 構造列をドリルスルーするには、次のいずれかの形のクエリを使用します。  
  
 `SELECT * FROM <structure>.CASES`  
  
 または  
  
 `SELECT StructureColumn('<structure-column-name>') FROM <model>.CASES`  
  
## <a name="see-also"></a>参照  
 [Role 要素&#40;ASSL&#41;](../objects/role-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
