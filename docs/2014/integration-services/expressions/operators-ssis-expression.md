---
title: 演算子 (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SSIS, operators
- SQL Server Integration Services, operators
- operators [Integration Services]
- expressions [Integration Services], operators
ms.assetid: 33df3a3d-1f5c-429b-a3b9-52b7d8689089
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 779597ab830df7cf89ad3d830c41402b43a91768
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320692"
---
# <a name="operators-ssis-expression"></a>演算子 (SSIS 式)
  このセクションでは、式の言語が提供する演算子、および式エバリュエーターが使用する演算子の優先順位と結合性について説明します。  
  
 次の表に、演算子に関するこのセクションのトピックの一覧を示します。  
  
|演算子|説明|  
|--------------|-----------------|  
|[キャスト&#40;SSIS 式&#41;](cast-ssis-expression.md)|式をあるデータ型から別のデータ型に変換します。|  
|[&#40;&#41;&#40;かっこ&#41; &#40;SSIS 式&#41;](parentheses-ssis-expression.md)|式の評価順序を特定します。|  
|[+&#40;追加&#41; &#40;SSIS&#41;](add-ssis.md)|2 つの数値式を加算します。|  
|[+&#40;連結&#41; &#40;SSIS 式&#41;](concatenate-ssis-expression.md)|2 つの式を連結します。|  
|[-&#40;減算&#41; &#40;SSIS 式&#41;](subtract-ssis-expression.md)|最初の数値式から 2 番目の数値式を減算します。|  
|[-&#40;否定&#41; &#40;SSIS 式&#41;](negate-ssis-expression.md)|数値式を負数化します。|  
|[&#42;&#40;乗算&#41; &#40;SSIS 式&#41;](multiply-ssis-expression.md)|2 つの数値式を乗算します。|  
|[分割&#40;SSIS 式&#41;](divide-ssis-expression.md)|最初の数値式を 2 番目の数値式で除算します。|  
|[&#40;剰余&#41; &#40;SSIS 式&#41;](modulo-ssis-expression.md)|最初の数値式を 2 番目の数値式で割った剰余を整数値で返します。|  
|[&#124;&#124;&#40;論理 OR&#41; &#40;SSIS 式&#41;](logical-or-ssis-expression.md)|論理 OR 演算を実行します。|  
|[& &&#40;論理 AND&#41; &#40;SSIS 式&#41;](logical-and-ssis-expression.md)|論理 AND 演算を実行します。|  
|[!&#40;論理 Not&#41; &#40;SSIS 式&#41;](logical-not-ssis-expression.md)|ブール型のオペランドを否定します。|  
|[&#124; (ビット演算子包括的 OR) (SSIS 式)](bitwise-inclusive-or-ssis-expression.md)|2 つの整数値の OR 演算をビット単位で実行します。|  
|[^&#40;ビットごとの排他的 OR&#41; &#40;SSIS 式&#41;](bitwise-exclusive-or-ssis-expression.md)|2 つの整数値の排他的 OR 演算をビット単位で実行します。|  
|[&&#40;ビットごとの AND&#41; &#40;SSIS 式&#41;](bitwise-and-ssis-expression.md)|2 つの整数値の AND 演算をビット単位で実行します。|  
|[~&#40;ビット演算子 Not&#41; &#40;SSIS 式&#41;](bitwise-not-ssis-expression.md)|整数の否定のビット演算を実行します。|  
|[== &#40;等しい&#41; &#40;SSIS 式&#41;](equal-ssis-expression.md)|2 つの式が等しいかどうかを判別するための比較を実行します。|  
|[\!= &#40;等しくない&#41; &#40;SSIS 式&#41;](unequal-ssis-expression.md)|2 つの式が等しくないかどうかを判別するための比較を実行します。|  
|[&#62; &#40;より大きい&#41; &#40;SSIS 式&#41;](greater-than-ssis-expression.md)|最初の式が 2 番目の式より大きいかどうかを判別するための比較を実行します。|  
|[&#60;&#40;未満&#41; &#40;SSIS 式&#41;](less-than-ssis-expression.md)|最初の式が 2 番目の式未満かどうかを判別するための比較を実行します。|  
|[&#62;=&#40;より大きいまたは等しい&#41; &#40;SSIS 式&#41;](greater-than-or-equal-to-ssis-expression.md)|最初の式が 2 番目の式以上かどうかを判別するための比較を実行します。|  
|[&#60;=&#40;に等しいまたはそれよりも小さい&#41; &#40;SSIS 式&#41;](less-than-or-equal-to-ssis-expression.md)|最初の式が 2 番目の式以下かどうかを判別するための比較を実行します。|  
|[?: &#40;です。条件付き&#41; &#40;です。SSIS 式&#41;](conditional-ssis-expression.md)|ブール式の評価に基づいて 2 つの式のうちのいずれかの式を返します。|  
  
 優先順位の階層内における各演算子の配置の詳細については、「 [演算子の優先順位と結合規則](operator-precedence-and-associativity.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [関数&#40;SSIS 式&#41;](functions-ssis-expression.md)   
 [Integration Services 式の詳細の例](examples-of-advanced-integration-services-expressions.md)   
 [Integration Services &#40;SSIS&#41; 式](integration-services-ssis-expressions.md)  
  
  
