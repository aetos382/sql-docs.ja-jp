---
title: '[新しいユーザー ロール] (Management Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: tools
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.newrole.f1
ms.assetid: 9f76a235-0b58-479c-8e5b-50588091b71c
caps.latest.revision: 26
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: fe31fbe487fbbe1688e9c633482bb5891ea0fa85
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082344"
---
# <a name="new-user-role-management-studio"></a>[新しいユーザー ロール]\(Management Studio)
  このページを使用すると、アイテムレベルのロールの定義を作成できます。 アイテムレベルのロールの定義とは、レポート サーバーによって管理されるフォルダー、レポート、モデル、リソース、および共有データ ソースに関連してユーザーが実行できるタスクを列挙する、名前付きの一連のタスクです。 アイテムレベルのロールの定義の一例として、事前定義された閲覧者ロールがあります。閲覧者ロールは、レポートのエンド ユーザーがフォルダー間の移動やレポートの表示に必要とする操作の種類を識別します。  
  
 ロールの定義の数は、それほど多くありません。 ほとんどの組織では、少数のロールの定義しか必要としません。 ただし、事前定義されたロールの定義が不十分な場合は、既存のロールの定義を変更したり、新しいロールの定義を作成したりできます。  
  
> [!NOTE]  
>  ロールの定義は、ネイティブ モードで実行されているレポート サーバーでのみ使用されます。 レポート サーバーが SharePoint 統合モード用に構成されている場合、このページは使用できません。  
  
## <a name="options"></a>[変数]  
 **名前**  
 ロールの定義名を入力します。 ロールの定義名は、レポート サーバーの名前空間内で一意である必要があります。 名前には、少なくとも 1 つの英数字が含まれている必要があります。 また、スペースおよびいくつかの記号を含めることもできます。 名前を指定するときに使用できない記号は次のとおりです。  
  
 ; ? : \@ & = + , $ / * < >  
  
 " /  
  
 **[説明]**  
 ロールの使用方法やロールがサポートする内容を列挙する説明を入力します。  
  
 **タスク**  
 このロールで実行できるタスクを選択します。 新しいタスクを作成したり、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]によってサポートされている既存のタスクを変更したりすることはできません。 アイテムレベルのロールの定義には、アイテムレベルのタスクのみを使用できます。  
  
 **タスクの説明**  
 タスクでサポートされる操作または権限を列挙する、タスクの説明を表示します。  
  
## <a name="see-also"></a>参照  
 [Management Studio のレポート サーバーの F1 ヘルプ](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [ロールの定義](../../reporting-services/security/role-definitions.md)  
  
  
