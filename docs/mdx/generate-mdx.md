---
title: 生成 (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 222479dd03263f61a603e30202f2abf54307b0bc
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740891"
---
# <a name="generate-mdx"></a>Generate (MDX)


  あるセットを別のセットの各メンバーに適用し、その結果セットを和集合で結合します。 または、セットに対して文字列式を評価し、作成された連結文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set expression syntax  
Generate( Set_Expression1 ,  Set_Expression2 [ , ALL ]  )  
  
String expression syntax  
Generate( Set_Expression1 ,  String_Expression [ ,Delimiter ]  )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression1*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Set_Expression2*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *String_Expression*  
 有効な文字列式です。通常は、指定されたセット内の各組の現在のメンバーの名前 (CurrentMember.Name) です。  
  
 *区切り記号*  
 文字列式として表された有効な区切り記号です。  
  
## <a name="remarks"></a>コメント  
 2 番目のセットが指定されている場合、**生成**関数が 2 番目のセット内の組を 1 番目のセット内の各組に適用することによって生成されるセットを返します *、* し、和集合で設定し、その結果を結合します。 場合**すべて**を指定すると、関数は、結果セット内の重複部分を保持します。  
  
 文字列式が指定されている場合、**生成**関数は、最初のセット内の各組に対して指定された文字列式を評価することによって生成される文字列を返します *、* し、結果を連結します。 必要に応じて、結果の連結文字列内の各文字列を区切ることもできます。  
  
## <a name="examples"></a>使用例  
  
### <a name="set"></a>オン  
 次の例では、[Date].[Calendar Year].[Calendar Year].MEMBERS というセットには 4 つのメンバーがあるため、クエリは Internet Sales Amount メジャーを含むセットを 4 回返します。  
  
```  
SELECT   
GENERATE( [Date].[Calendar Year].[Calendar Year].MEMBERS  
, {[Measures].[Internet Sales Amount]}, ALL)  
ON 0  
FROM [Adventure Works]  
```  
  
 ALL を削除すると、クエリが変更され、Internet Sales Amount が 1 回だけ返されるようになります。  
  
```  
SELECT   
GENERATE( [Date].[Calendar Year].[Calendar Year].MEMBERS  
, {[Measures].[Internet Sales Amount]})  
ON 0  
FROM [Adventure Works]  
```  
  
 最も一般的な実用**生成**はセット評価する、複雑なメンバーのセットに対して TopCount などの式。 次のクエリでは、行の Calendar Year ごとに上位 10 個の製品を表示します。  
  
```  
SELECT   
{[Measures].[Internet Sales Amount]}  
ON 0,  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS  
, TOPCOUNT(  
[Date].[Calendar Year].CURRENTMEMBER  
*  
[Product].[Product].[Product].MEMBERS  
,10, [Measures].[Internet Sales Amount]))  
ON 1  
FROM [Adventure Works]  
```  
  
 別の上位 10 個が表示されていることと、各年に注意してください。 の使用**生成**は、この結果を取得する唯一の方法です。 次の例に示すように、Calendar Year と上位 10 個の製品のセットをクロス結合しただけの場合は、全期間の上位 10 個の製品が、年ごとに繰り返して表示されます。  
  
```  
SELECT   
{[Measures].[Internet Sales Amount]}  
ON 0,  
[Date].[Calendar Year].[Calendar Year].MEMBERS  
*   
TOPCOUNT(  
[Product].[Product].[Product].MEMBERS  
,10, [Measures].[Internet Sales Amount])  
ON 1  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>String  
 次の例は、の使用を示しています。**生成**文字列を返します。  
  
```  
WITH   
MEMBER MEASURES.GENERATESTRINGDEMO AS  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS,  
[Date].[Calendar Year].CURRENTMEMBER.NAME)  
MEMBER MEASURES.GENERATEDELIMITEDSTRINGDEMO AS  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS,  
[Date].[Calendar Year].CURRENTMEMBER.NAME, " AND ")  
SELECT   
{MEASURES.GENERATESTRINGDEMO, MEASURES.GENERATEDELIMITEDSTRINGDEMO}  
ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  この形式の**生成**関数場合に利用でき、計算のデバッグように、セット内のすべてのメンバーの名前を表示する文字列を返すことができます。 一連の厳密な MDX 表記よりも読みやすくする可能性がある、 [SetToStr &#40;MDX&#41; ](../mdx/settostr-mdx.md)関数が返される。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
