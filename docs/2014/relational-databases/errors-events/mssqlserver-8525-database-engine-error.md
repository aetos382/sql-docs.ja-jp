---
title: MSSQLSERVER_8525 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "8525"
helpviewer_keywords:
- 8525 (Database Engine error)
ms.assetid: 297867c1-691e-4d6b-a3be-a7575015ecfa
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: adf88cf5e9982c3b02516cd69c186c2ac449f7cf
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425341"
---
# <a name="mssqlserver8525"></a>MSSQLSERVER_8525
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|8525|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名||  
|メッセージ テキスト|分散トランザクションが完了しました。 このセッションを新規トランザクションまたは NULL トランザクションのいずれかに参加させます。|  
  
## <a name="explanation"></a>説明  
 分散トランザクション コーディネーターを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用するプログラミング モデルでは、分散トランザクションに対してアプリケーションを明示的に参加させたり参加を解除したりする必要があります。  
  
 このエラーは、次の 4 つの条件が揃った場合に発生します。  
  
-   アプリケーションが分散トランザクションに参加している。  
  
-   トランザクションが、何かの理由でコミットまたはロールバックされた状態で終了した。  
  
-   ユーザー アプリケーションが、分散トランザクションへの参加を明示的に解除されていないか、新しい分散トランザクションに明示的に参加していない。  
  
-   既存の分散トランザクションへの参加の解除でも新しい分散トランザクションへの参加でもないトランザクション操作、たとえば、クエリの実行やローカル トランザクションの開始を、アプリケーションで試行している。  
  
 ローカル トランザクションを作成する操作をアプリケーションで実行している場合はエラー状態 1 が使用され、バインドされたセッションへの参加をアプリケーションで試みている場合はエラー状態 2 が使用されます。  
  
## <a name="user-action"></a>ユーザーの操作  
 アプリケーションは、分散トランザクションに参加した後、その分散トランザクションへの参加を明示的に解除するか、別の分散トランザクションに参加する必要があります。 これにより、前のトランザクションへの参加が暗黙的に解除されます。 分散トランザクションへの参加やその解除を行うための正確な構文については、アプリケーションのプログラミング インターフェイス マニュアルを参照してください。  
  
  
