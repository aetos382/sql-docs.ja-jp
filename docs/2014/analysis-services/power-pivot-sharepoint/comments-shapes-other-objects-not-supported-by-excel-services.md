---
title: '次の機能は、Excel Services でサポートされていないと表示されないか、一部しか表示可能性があります: コメント、図形、またはその他のオブジェクト |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
caps.latest.revision: 4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1bee0273ba256ea6861b4259d48e377528c5e4eb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192425"
---
# <a name="the-following-features-are-not-supported-by-excel-services-and-may-not-display-or-may-display-only-partially-comments-shapes-or-other-objects"></a>次の機能は Excel Services でサポートされておらず、表示されないか、一部しか表示されないことがあります: コメント、図形、またはその他のオブジェクト
  このエラーは、PowerPivot フィールドの一覧から PowerPivot ブックにスライサーを追加すると発生します。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|適用対象|PowerPivot for SharePoint|  
|製品バージョン|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|Excel Web Access では、PowerPivot フィールドの一覧からブックに追加されたスライサーの位置指定および書式設定の制御に使用される図形オブジェクトを表示することができません。|  
|メッセージ テキスト|次の機能は Excel Services でサポートされておらず、表示されないか、一部しか表示されないことがあります。<br /><br /> コメント、図形、またはその他のオブジェクト<br /><br /> 外部データのクエリなど、一部の機能では、Microsoft Excel でのみ更新できるキャッシュ データが表示されます。|  
  
## <a name="explanation"></a>説明  
 Excel Web Access をクリックすると、PowerPivot ブックを開くには、ブラウザーでこのエラーが表示されます、**詳細**メッセージは、ボタン**意図したとおり、サポートされていない機能このブックが表示されない場合があります**します。  
  
 このエラーは、Excel の非表示の図形オブジェクトによって制御されるレイアウトを持つスライサーが PowerPivot ブックにある場合に発生します。 図形オブジェクトは、水平配置と垂直配置におけるスライサーの書式設定および位置指定を制御します。  
  
 Excel Services では図形オブジェクトを表示できませんが、このオブジェクトは非表示であるので、表示できないことは問題ではありません。  
  
## <a name="user-action"></a>ユーザーの操作  
 このエラーは無視してかまいません。 **[OK]** をクリックして、エラー メッセージを閉じ、ブックとスライサーの使用を問題なく続けることができます。  
  
  
