---
title: "DrillupLevel (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DRILLUPLEVEL
dev_langs:
- kbMDX
helpviewer_keywords:
- DrillupLevel function
ms.assetid: 63431f79-f3a1-40c4-bf57-2b6bd8991cc3
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a59de1459ecc5953b4612c64603eff958049e3e6
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="drilluplevel-mdx"></a>DrillupLevel (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  セットのメンバーのうち、指定されたレベルの下位に属するメンバーをドリル アップします。  
  
## <a name="syntax"></a>構文  
  
```  
  
DrillupLevel(Set_Expression [ , Level_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **DrillupLevel**指定したセットに含まれるメンバーに基づいて階層的に編成されたメンバーのセット関数を返します。 指定されたセット内のメンバーの順序は保持されます。  
  
 レベル式が指定されている場合、 **DrillupLevel**関数は、指定されたレベルより上位にあるメンバーのみを取得してセットを構築します。 レベル式が指定された、指定されたセット内の指定されたレベルのメンバーが存在しない場合は、指定したセットが返されます。  
  
 レベル式が指定されていない場合、指定されたセット内で参照されている最初のディメンションの最下位レベルより 1 つ上のレベルにあるメンバーだけを取得してセットを構築します。  
  
## <a name="example"></a>例  
 次の例は、最初のセットから Subcategory レベルより上位にあるメンバーのセットを返します。  
  
```  
SELECT DrillUpLevel   
  ({[Product].[Product Categories].[All Products]  
    ,[Product].[Product Categories].[Subcategory].&[32],  
    [Product].[Product Categories].[Product].&[215]},  
  [Product].[Product Categories].[Subcategory]  
    )  
  ON 0  
  FROM [Adventure Works]  
  WHERE [Measures].[Internet Order Quantity]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
