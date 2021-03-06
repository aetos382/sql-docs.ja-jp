---
title: Members 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ae4326e00ba98075a86079157484c5963d0147d
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37994714"
---
# <a name="members-element-xmla"></a>Members 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  コレクションを含む[メンバー](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)親に含まれる要素[CrossProduct](../../../analysis-services/xmla/xml-elements-properties/crossproduct-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CrossProduct>  
   <Members Hierarchy="string">  
      <Member>...</Member>  
   </Members>  
   ...  
</CrossProduct>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CrossProduct](../../../analysis-services/xmla/xml-elements-properties/crossproduct-element-xmla.md)|  
|子要素|[Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|Hieararchy|必要な**文字列**属性。 含まれている、メンバー、階層の名前、**メンバー**要素が属しています。|  
  
## <a name="remarks"></a>コメント  
 クライアント アプリケーションを設定した場合、 **AxisFormat**プロパティを*ClusterFormat*、各軸のメンバーには、各クラスターが順序付けされたセットの間のクロス積を表すクラスターに分けられます各階層のメンバー。 各**軸**要素は、1 つ以上の**CrossProduct**要素。 すべて**CrossProduct**要素が含まれています、**メンバー**軸上の各階層の要素。 **メンバー**要素がさらに、1 つ**メンバー**クロス積に含まれる指定された階層の各メンバーの要素。  
  
## <a name="example"></a>例  
 次の例の構造を示しています、**メンバー**要素をクライアントが指定したときに*ClusterFormat*の**AxisFormat** XMLA プロパティ、次の軸のメンバー。  
  
||||||  
|-|-|-|-|-|  
|**Time** 階層|1999|1999|2000|2001|  
|**Category** 階層|Actual|Budget|Budget|Budget|  
|Clusters|クラスター 1|クラスター 1|クラスター 1|Cluster 2|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <CrossProduct Size = "4">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
      <CrossProduct Size = "1">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[2001]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>参照
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
