---
title: "ポイント (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Point
- Point_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Point (geometry Data Type)
ms.assetid: 7a2e593a-4d4c-4214-b0c5-02d1ac46bc66
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e153b3bbaf18e6c4b69171e56f2fdae6965396a7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="point-geometry-data-type"></a>Point (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

構築、 **geometry**インスタンスを表す、**ポイント**からその X と Y 値、および SRID のインスタンス。
  
## <a name="syntax"></a>構文  
  
```  
  
Point ( X, Y, SRID )  
```  
  
## <a name="arguments"></a>引数  
 *X*  
 **Float**の X 座標を表す式、**ポイント**生成されています。  
  
 *Y*  
 **Float**の Y 座標を表す式、**ポイント**生成されています。  
  
 *SRID*  
 **Int** 、空間を表す式の ID (SRID) を参照、 **geometry**インスタンスを取得します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
## <a name="remarks"></a>解説  
  
## <a name="examples"></a>使用例  
 次の例で`Point()`を作成する、`geometry`インスタンス。  
  
```  
DECLARE @g geometry;   
SET @g = geometry::Point(1, 10, 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [拡張された静的なジオメトリ メソッド](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

