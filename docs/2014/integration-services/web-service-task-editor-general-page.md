---
title: Web サービス タスク エディター ([全般] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.general.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
caps.latest.revision: 34
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9d68fdf156caf460ee6130df7ab746fcbd13fec0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37331862"
---
# <a name="web-service-task-editor-general-page"></a>[Web サービス タスク エディター] ([全般] ページ)
  **[Web サービス タスク エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、HTTP 接続マネージャーの指定、Web サービス タスクで使用する WSDL (Web サービス記述言語) ファイルの場所の指定、Web サービス タスクの記述、WSDL ファイルのダウンロードなどの操作を実行できます。  
  
 このタスクの詳細については、「 [Web サービス タスク](control-flow/web-service-task.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[HTTPConnection]**  
 接続マネージャーを一覧から選択するか、[\<**新しい接続…**>] をクリックして新しい接続マネージャーを作成します。  
  
> [!IMPORTANT]  
>  HTTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。 Windows 認証はサポートされていません。  
  
 **関連項目:**  [HTTP 接続マネージャー](connection-manager/http-connection-manager.md), 、[[HTTP 接続マネージャー エディター] ([サーバー] ページ)](../../2014/integration-services/http-connection-manager-editor-server-page.md)  
  
 **[WSDLFile]**  
 コンピューターのローカルにある WSDL ファイルの完全修飾パスを入力するか、参照ボタン ( **[...]** ) をクリックしてファイルを指定します。  
  
 WSDL ファイルを既に手動でコンピューターにダウンロードしている場合は、そのファイルを選択します。 ただし、WSDL ファイルをまだダウンロードしていない場合は、次の手順に従います。  
  
-   ファイル名拡張子が ".wsdl" の空のファイルを作成します。  
  
-   **[WSDLFile]** オプションで、この空のファイルを選択します。  
  
-   値を設定**OverwriteWSDLFile**に`True`を実際の WSDL ファイルで上書きできる空のファイルを有効にします。  
  
-   **[WSDL のダウンロード]** をクリックして実際の WSDL ファイルをダウンロードし、空のファイルを上書きします。  
  
    > [!NOTE]  
    >  **[WSDL のダウンロード]** オプションは、 **[WSDLFile]** ボックスに既存のローカル ファイルの名前を指定するまで有効になりません。  
  
 **[OverwriteWSDLFile]**  
 Web サービス タスクの WSDL ファイルを上書きできるかどうかを示します。  
  
 使用して WSDL ファイルをダウンロードするかどうか、 **WSDL のダウンロード**ボタン、この値に設定`True`します。  
  
 **名前**  
 Web サービス タスクの一意な名前を指定します。 この名前は、タスク アイコンのラベルとして使用されます。  
  
> [!NOTE]  
>  タスク名はパッケージ内で一意である必要があります。  
  
 **[説明]**  
 Web サービス タスクの説明を入力します。  
  
 **[WSDL のダウンロード]**  
 WSDL ファイルをダウンロードします。  
  
 このボタンは、 **[WSDLFile]** ボックスに既存のローカル ファイルの名前を指定するまで有効になりません。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Web サービス タスク エディター &#40;[入力] ページ&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Web サービス タスク エディター&#40;ページの出力&#41;](../../2014/integration-services/web-service-task-editor-output-page.md)   
 [[式] ページ](expressions/expressions-page.md)  
  
  
