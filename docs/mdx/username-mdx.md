---
title: "UserName (MDX) |Microsoft ドキュメント"
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
- UserName
dev_langs:
- kbMDX
helpviewer_keywords:
- UserName function
ms.assetid: ecae549b-5c5e-4483-84e6-b713cd297d7e
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e9d9dbf069eab4da9c06e1a387baba47a90c24c5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="username-mdx"></a>UserName (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在の接続のドメイン名とユーザー名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
UserName [ ( ) ]  
```  
  
## <a name="remarks"></a>解説  
 返される値は、次の形式の文字列です。  
  
 *ドメイン名 \ ユーザー名*  
  
## <a name="example"></a>例  
 次の例では、クエリを実行しているユーザーのユーザー名を返しています。  
  
```  
WITH MEMBER Measures.x AS UserName  
SELECT Measures.x ON COLUMNS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
