---
title: MultiLineString | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: spatial
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiLineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 95deeefe-d6c5-4a11-b347-379e4486e7b7
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 290ed8a0bfd3bfdb9733ea98d80aeaaf0f34602a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39549682"
---
# <a name="multilinestring"></a>MultiLineString
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **MultiLineString** は、0 個以上の **geometry** または **geographyLineString** インスタンスのコレクションです。  
  
## <a name="multilinestring-instances"></a>MultiLineString インスタンス  
 次の図は、 **MultiLineString** インスタンスの例です。  
  
 ![geometry MultiLineString インスタンスの例](../../relational-databases/spatial/media/multilinestring.gif "geometry MultiLineString インスタンスの例")  
  
 この図は次のことを示しています。  
  
-   図 1 は、2 つの **LineString** 要素の 4 つの終点からなる境界を持つ単純な **MultiLineString** インスタンスです。  
  
-   図 2 の **MultiLineString** インスタンスは、 **LineString** 要素の終点のみで交差しているため単純です。 このインスタンスの境界は、重なっていない 2 つの終点です。  
  
-   図 3 の **MultiLineString** インスタンスは、 **LineString** 要素の内部で交差しているため単純ではありません。 この **MultiLineString** インスタンスの境界は 4 つの終点です。  
  
-   図 4 は、単純でなく、閉じていない **MultiLineString** インスタンスです。  
  
-   図 5 は、単純な、閉じていない **MultiLineString**です。 このインスタンスが閉じていないのは、その **LineStrings** 要素が閉じていないからです。 このインスタンスが単純なのは、内部で交差している **LineStrings** インスタンスがないからです。  
  
-   図 6 は、単純な閉じている **MultiLineString** インスタンスです。 このインスタンスが閉じているのは、そのすべての要素が閉じているからです。 このインスタンスが単純なのは、内部で交差している要素がないからです。  
  
### <a name="accepted-instances"></a>許容されるインスタンス  
 **MultiLineString** インスタンスが許容されるためには、空であるか、許容される **LineString** インスタンスのみで構成されている必要があります。 許容される **LineString** インスタンスの詳細については、「 [LineString](../../relational-databases/spatial/linestring.md)」を参照してください。 次の例に、許容される **MultiLineString** インスタンスを示します。  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
```  
  
 次の例では、2 番目の `System.FormatException` LineString **インスタンスが有効ではないため、** がスローされます。  
  
```  
DECLARE @g geometry = 'MULTILINESTRING((1 1, 3 5),(-5 3))';  
```  
  
### <a name="valid-instances"></a>有効なインスタンス  
 **MultiLineString** インスタンスを有効にするためには、次の条件を満たす必要があります。  
  
1.  **MultiLineString** インスタンスを構成するすべてのインスタンスが、有効な **LineString** インスタンスでなければならない。  
  
2.  **MultiLineString** インスタンスを構成する 2 つの **LineString** インスタンスが内部で互いに重ならない。 **LineString** インスタンスは、有限数の接点のみで、互いにまたは他の **LineString** インスタンスと交差するか接することができます。  
  
 次の例に、3 つの有効な **MultiLineString** インスタンスと 1 つの無効な **MultiLineString** インスタンスを示します。  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` は、2 番目の **LineString** インスタンスが最初の **LineString** インスタンスと内部で重なっているため、有効ではありません。 有限数の接点で接しています。  
  
## <a name="examples"></a>使用例  
 次の例では、2 つの `geometry``MultiLineString` 要素を含む SRID 0 の単純な `LineString` インスタンスを作成しています。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
```  
  
 このインスタンスを別の SRID で作成するには、 `STGeomFromText()` または `STMLineStringFromText()`を使用します。 次の例のように、 `Parse()` を使用して、その後に SRID を変更することもできます。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
SET @g.STSrid = 13;  
```  
  
## <a name="see-also"></a>参照  
 [STLength &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stlength-geometry-data-type.md)   
 [STIsClosed &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md)   
 [MultiLineString](../../relational-databases/spatial/linestring.md)   
 [空間データ &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
