---
title: ユーザーを切断する Analysis Services サーバーとセッション |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 99072a36fe65679dbf81aa0ba3f4efdb3b487533
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34014349"
---
# <a name="disconnect-users-and-sessions-on-analysis-services-server"></a>Analysis Services サーバー上のユーザーとセッションの切断
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の管理者は、ワークロード管理の一環としてユーザー操作を終了できます。 ユーザー操作を終了するには、セッションと接続を取り消します。 セッションは、クエリの実行時に自動的に作成される場合 (暗黙的) と、管理者が作成時に名前を付ける場合 (明示的) があります。 接続は、クエリを実行できる開かれたパイプのようなものです。 セッションと接続は両方とも、アクティブなときに終了できます。 たとえば、処理に時間がかかりすぎる場合や、実行中のコマンドが正しく記述されているかどうかについて疑問が生じた場合、管理者はセッションの処理を終了できます。  
  
## <a name="ending-sessions-and-connections"></a>セッションと接続の終了  
 セッションおよび接続の管理には、動的管理ビュー (DMV) および XMLA を使用できます。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、Analysis Services インスタンスに接続します。  
  
2.  現在実行中のすべてのセッション、接続、およびコマンドのリストを取得するには、次のいずれかの DMV クエリを MDX クエリ ウィンドウに貼り付けます。  
  
     `Select * from $System.Discover_Sessions`  
  
     `Select * from $System.Discover_Connections`  
  
     `Select * from $System.Discover_Commands`  
  
3.  F5 キーを押してクエリを実行します。  
  
     DMV クエリは、セッションと接続の情報を、読み取りやコピーが容易な表形式の結果セットとして返します。  
  
 クエリ ウィンドウを開いた状態にします。 次の手順では、切断するセッションの SPID をコピーするために、このページに戻ります。  
  
 セッションを終了するために、XMLA クエリ ウィンドウをもう 1 つ開きます。  
  
1.  次の構文を MDX クエリ ウィンドウに貼り付けます。ConnectionID、SessionID、または SPID プレースホルダーは、前の手順からコピーした有効な値に置き換えてください。  
  
    ```  
    <Cancel xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  
       <ConnectionID>111</ConnectionID>  
       <SessionID>222</SessionID>  
       <SPID>333</SPID>  
  
    <CancelAssociated>1</CancelAssociated>  
    </Cancel>  
  
    ```  
  
2.  F5 キーを押してキャンセル コマンドを実行します。  
  
 接続を終了すると、すべてのセッションと SPID が取り消され、ホスト セッションが閉じられます。  
  
 セッションを終了すると、そのセッションの一部として実行されているすべてのコマンド (SPID) が停止します。  
  
 SPID を終了すると、特定のコマンドが取り消されます。  
  
 まれに、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で接続に関連付けられているすべてのセッションおよび SPID を追跡できない場合 (HTTP シナリオで複数のセッションが開かれている場合など) は、接続を閉じることができません。  
  
 このトピックで参照された XMLA の詳細については、[「Execute メソッド (XMLA)」](../../analysis-services/xmla/xml-elements-methods-execute.md) および [「Cancel 要素 (XMLA)」](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) を参照してください。  
  
## <a name="see-also"></a>参照  
 [管理接続およびセッション (&) #40 です。XMLA & #41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [BeginSession 要素 & #40 です。XMLA & #41;](../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)   
 [EndSession 要素 & #40 です。XMLA & #41;](../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Session 要素 & #40 です。XMLA & #41;](../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)  
  
  
