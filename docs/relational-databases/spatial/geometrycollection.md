---
title: GeometryCollection | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
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
- GeomCollection geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 4445c0d9-a66b-4d7c-88e4-a66fa6f7d9fd
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: b456a13f03c547c15258f002fb78df9c9759511e
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39552012"
---
# <a name="geometrycollection"></a>GeometryCollection
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **GeometryCollection** は、ゼロ以上の **geometry** インスタンスまたは **geography** インスタンスからなるコレクションです。 **GeometryCollection** は空にすることができます。  
  
## <a name="geometrycollection-instances"></a>GeometryCollection インスタンス  
  
### <a name="accepted-instances"></a>許容されるインスタンス  
 **GeometryCollection** インスタンスが許容されるためには、空の **GeometryCollection** インスタンスであるか、 **GeometryCollection** インスタンスを構成するすべてのインスタンスが許容されるインスタンスである必要があります。 次の例に、許容されるインスタンスを示します。  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
 次の例では、 `System.FormatException` GeometryCollection **インスタンス内の** LinesString **インスタンスが許容されないため、** がスローされます。  
  
```  
DECLARE @g geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1), POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
### <a name="valid-instances"></a>有効なインスタンス  
 **GeometryCollection** インスタンスを構成するすべてのインスタンスが有効である場合、 **GeometryCollection** インスタンスは有効です。 次の例に、3 つの有効な **GeometryCollection** インスタンスと 1 つの無効な インスタンスを示します。  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g4 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, 1 -5, -5 5, -5 -1, -1 -1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` は、 **GeometryCollection** 内の **Polygon** インスタンスが有効ではないため、有効ではありません。  
  
 受け取られる有効なインスタンスについては、 [Point](../../relational-databases/spatial/point.md)、 [MultiPoint](../../relational-databases/spatial/multipoint.md)、 [LineString](../../relational-databases/spatial/linestring.md)、 [MultiLineString](../../relational-databases/spatial/multilinestring.md)、 [Polygon](../../relational-databases/spatial/polygon.md)、 [MultiPolygon](../../relational-databases/spatial/multipolygon.md)を参照してください。  
  
## <a name="examples"></a>使用例  
 `geometry``GeometryCollection` を、 `Point` インスタンスと `Polygon` インスタンスを含む SRID 1 の Z 値でインスタンス化する例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION(POINT(3 3 1), POLYGON((0 0 2, 1 10 3, 1 0 4, 0 0 2)))', 1);  
```  
  
## <a name="see-also"></a>参照  
 [空間データ &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
