---
title: MDDataSet データ型 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 986fade6d9db3d6170d47181ac960d15febdf260
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34573924"
---
# <a name="mddataset-data-type-xmla"></a>MDDataSet データ型 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  によって返される多次元データを表す派生データ型を定義、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
 **Namespace** urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}-分析: mddataset  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <!-- The following elements extend Resultset -->  
   <!-- Optional schema elements -->  
   <OlapInfo>...</OlapInfo>  
   <Axes>...</Axes>  
   <CellData>...</CellData>  
</root>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[結果セット](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[軸](../../../analysis-services/xmla/xml-elements-properties/axes-element-xmla.md)、 [CellData](../../../analysis-services/xmla/xml-elements-properties/celldata-element-xmla.md)、 [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>コメント  
 **MDDataSet**データ型は、OLAP 指向行セット (またはデータセット) XML で OLAP データを表すために必要です。 この行セットの内容は、の値によって異なることができます、**コンテンツ**と**形式**で提供されるプロパティ、[プロパティ](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)のコレクション、 **実行**メソッドです。 詳細については、**コンテンツ**と**形式**プロパティを参照してください[サポートされる XMLA プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)です。  
  
 OLE DB for OLAP データセットの構造に関する基本的な情報については、XML for Analysis 1.1 仕様の「OLE DB への MDDataSet データ型のマッピング」を参照してください。 完全 XML スキーマ定義言語 (XSD) サンプルについては、 **MDDataSet**データ型、XML for Analysis 1.1 仕様の「付録 d: MDDataSet Example」を参照してください。  
  
## <a name="see-also"></a>参照
 [XML データ型&#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
