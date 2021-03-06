---
title: STUFF (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STUFF
- STUFF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting characters
- STUFF function
- length characters
- removing characters
- replacing characters
- characters [SQL Server], replacing
- inserting data
ms.assetid: abb0afa9-44f6-42a2-a871-5f471dfb222b
caps.latest.revision: 40
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 2d532a6ad289f352cf8210f1b0edefc3947d143c
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39458806"
---
# <a name="stuff-transact-sql"></a>STUFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  STUFF 関数は、文字列を別の文字列に挿入します。 まず、1 番目の文字列の指定された開始位置から指定された長さの文字を削除し、次に、2 番目の文字列を 1 番目の文字列の指定された開始位置に挿入します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
STUFF ( character_expression , start , length , replaceWith_expression )  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 文字データの[式](../../t-sql/language-elements/expressions-transact-sql.md)です。 *character_expression* には、文字データまたはバイナリ データの定数、変数、または列を使用できます。  
  
 *start*  
 削除と挿入を開始する位置を整数で指定します。 *start* が負の値またはゼロの場合は、null 文字列が返されます。 *start* が最初の *character_expression* よりも長い場合は、null 文字列が返されます。 *start* には **bigint** 型を使用できます。  
  
 *length*  
 削除する文字数を整数で指定します。 *length* が負の値の場合は、null 文字列が返されます。 *length* が最初の *character_expression* よりも長い場合、最後の *character_expression* の末尾の文字まで削除が実行されます。  *length* がゼロの場合、文字列の先頭の文字の前に挿入が実行されます。 *length* には **bigint** 型を使用できます。

 *replaceWith_expression*  
 文字データの[式](../../t-sql/language-elements/expressions-transact-sql.md)です。 *character_expression* には、文字データまたはバイナリ データの定数、変数、または列を使用できます。 この式は、*character_expression* の *start* から始まる *length* 文字を置き換えます。 `NULL` に *replaceWith_expression* を指定すると、何も挿入されず、文字が削除されます。   
  
## <a name="return-types"></a>戻り値の型  
 *character_expression* が、サポートされている文字データ型のいずれかの場合は、文字データが返されます。 *character_expression* が、サポートされているバイナリ データ型のいずれかの場合は、バイナリ データが返されます。  
  
## <a name="remarks"></a>Remarks  
 開始位置または長さが負の場合、または開始位置が 1 番目の文字列の長さを超える場合は NULL 文字列が返されます。 開始位置が 0 の場合は、NULL 値が返されます。 削除する長さが 1 番目の文字列より長い場合は、1 番目の文字列の最初の文字まで削除されます。  

結果値が、戻り値の型でサポートされている最大値より大きい場合は、エラーが発生します。  
  
## <a name="supplementary-characters-surrogate-pairs"></a>補助文字 (サロゲート ペア)  
 SC の照合順序を使用する場合、*character_expression* と *replaceWith_expression* の両方にサロゲート ペアを含めることができます。 length パラメーターでは、*character_expression* 内の各サロゲートは 1 文字としてカウントされます。  
  
## <a name="examples"></a>使用例  
 次の例では、最初の文字列 (`abcdef`) の位置 `2` (`b`) から 3 文字を削除し、その位置に 2 番目に指定した文字列を挿入して生成される文字列を返します。  
  
```  
SELECT STUFF('abcdef', 2, 3, 'ijklmn');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------   
aijklmnef   
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [文字列関数 &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
