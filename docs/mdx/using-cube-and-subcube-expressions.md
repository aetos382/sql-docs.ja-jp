---
title: キューブ式とサブキューブ式を使用して |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f13d92c114783646bbeab9451c3d212ff01b8f8c
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743381"
---
# <a name="using-cube-and-subcube-expressions"></a>キューブ式とサブキューブ式の使用


  多次元式 (MDX) ステートメントでは、キューブまたはサブキューブのデータを定義、操作、または取得するために、キューブ式やサブキューブ式を使用します。  
  
## <a name="cube-expressions"></a>キューブ式  
 キューブ式には、キューブ識別子または CURRENTCUBE キーワードが含まれているため、単純式のみを指定できます。 多くの MDX ステートメントでは、キューブ識別子を使用する代わりに、現在のキューブ コンテキストを識別するために CURRENTCUBE キーワードを使用します。  
  
 キューブ識別子は*Cube_Name* MDX ステートメントの説明については BNF 表記でします。  
  
 キューブ式は複数の場所で使用できます。 MDX の SELECT ステートメントでは、キューブ式は、データの取得元のキューブを指定します。 次のクエリの例では、式 [Adventure Works] はその名前のキューブを参照しています。  
  
 `SELECT [Measures].[Internet Sales Amount] ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 CREATE MEMBER ステートメントでは、キューブ式は、作成中の計算されるメンバーが表示されるキューブを指定します。 次の例のステートメントでは、Adventure Works キューブの Measures ディメンションに、計算されるメジャーを作成します。  
  
 `CREATE MEMBER [Adventure Works].[Measures].[Test] AS 1`  
  
 MDX スクリプト内で CREATE MEMBER ステートメントを使用する場合は、キューブの名前を CURRENTCUBE キーワードに置き換えることができます。これは、計算されるメンバーが作成されるキューブが、MDX スクリプトが属するキューブと常に同じになるためです。次に例を示します。  
  
 `CREATE MEMBER CURRENTCUBE.[Measures].[Test] AS 1;`  
  
 これにより、キューブの名前がハードコーディングされなくなるため、計算されるメンバーの定義をキューブ間で簡単にコピーして貼り付けることができるようになります。  
  
## <a name="subcube-expressions"></a>サブキューブ式  
 サブキューブ式には、サブキューブ識別子、またはサブキューブを返す MDX ステートメントを含めることができます。 サブキューブ式にサブキューブ識別子が含まれている場合、これは単純式になります。 サブキューブを返す MDX ステートメントが含まれている場合は、複合ステートメントになります。 たとえば、次の例に示すように、MDX の SELECT ステートメントは、サブキューブを返すので、サブキューブ式が許可されている場所で使用できます。  
  
 `SELECT [Measures].MEMBERS ON COLUMNS,`  
  
 `[Date].[Calendar Year].MEMBERS ON ROWS`  
  
 `FROM`  
  
 `(SELECT [Measures].[Internet Sales Amount] ON COLUMNS,`  
  
 `[Date].[Calendar Year].&[2004] ON ROWS`  
  
 `FROM [Adventure Works])`  
  
 このように FROM 句内で使用する SELECT ステートメントは、サブセレクトとも呼ばれます。  
  
 サブキューブ式が使用される別の一般的なシナリオとして、MDX スクリプトで、スコープを指定した割り当てを実行する場合があります。 次の例では、SCOPE ステートメントを使用して、[Measures].[Internet Sales Amount] で構成されるサブキューブに割り当てを制限します。  
  
 `SCOPE([Measures].[Internet Sales Amount]);`  
  
 `This=1;`  
  
 `END SCOPE;`  
  
 サブキューブ識別子は*Subcube_Name*です。 形式で表されます。  
  
## <a name="see-also"></a>参照  
 [MDX の基本的なクエリ&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-query-the-basic-query.md)   
 [MDX でのサブキューブの構築&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/building-subcubes-in-mdx-mdx.md)   
 [CREATE SUBCUBE ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-create-subcube.md)   
 [式&#40;MDX&#41;](../mdx/expressions-mdx.md)   
 [SCOPE ステートメント&#40;MDX&#41;](../mdx/mdx-scripting-scope.md)  
  
  
