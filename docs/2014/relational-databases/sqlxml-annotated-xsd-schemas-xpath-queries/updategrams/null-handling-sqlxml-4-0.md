---
title: NULL の取り扱い (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fb61234696e419bc203822985f8966a81975e476
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172119"
---
# <a name="null-handling-sqlxml-40"></a>NULL の取り扱い (SQLXML 4.0)
  XML 構文では、NULL は "存在しない" ことを表します。 たとえば、属性または要素値が NULL の場合、その属性または要素は XML ドキュメントに存在しません。[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML では、`updg:nullvalue` 属性を使用して、要素または属性値に NULL を指定できます。  
  
 たとえば、次のアップデート グラムにより、**タイトル**値へのアクセスを**ContactID** 64 が null の場合、し、更新、**タイトル**値を"Mr." この連絡先にします。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync updg:nullvalue="IsNULL"  >  
    <updg:before>  
       <Person.Contact ContactID="64" Title="IsNULL" />  
    </updg:before>  
    <updg:after>  
       <Person.Contact ContactID="64" Title="Mr." />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 パラメーターをアップデートグラムに渡すときには、パラメーター値として NULL を指定できます。 これを行うには、`nullvalue` ブロックに `<updg:header>` 属性を指定します。 例については、次を参照してください。[アップデート グラムにパラメーターを渡す&#40;SQLXML 4.0&#41;](passing-parameters-to-updategrams-sqlxml-4-0.md)します。  
  
## <a name="see-also"></a>参照  
 [アップデート グラムのセキュリティに関する考慮事項&#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
