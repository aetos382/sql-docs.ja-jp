---
title: '手順 1: サーバー プログラム (RDS チュートリアル) を指定する |Microsoft ドキュメント'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], specifying server program
ms.assetid: d8bb35b1-c02a-4231-8d55-016e56e53b95
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 68468c97d870f103260c8a5ee1b7914c2ecc378a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274561"
---
# <a name="step-1-specify-a-server-program-rds-tutorial"></a>手順 1: サーバー プログラム (RDS チュートリアル) を指定します。
最も一般的な場合に、使用、 [.rds ですDataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)オブジェクト[CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md)既定のサーバー プログラムを指定するメソッド[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)、または独自のカスタム サーバー プログラム (ビジネス オブジェクト)。 サーバーのプログラムが、サーバーと、サーバーのプログラムへの参照でインスタンス化または*プロキシ*が返されます。  
  
 このチュートリアルでは、既定のサーバー プログラムを使用します。  
  
```  
Sub RDSTutorial1()  
   Dim DS as New RDS.DataSpace  
   Dim DF as Object  
   Set DF = DS.("RDSServer.DataFactory", "http://yourServer")  
...  
```  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="see-also"></a>参照  
 [手順 2: 呼び出すサーバー プログラム (RDS チュートリアル)](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)   
 [RDS のチュートリアル (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
