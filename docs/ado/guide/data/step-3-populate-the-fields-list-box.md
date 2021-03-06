---
title: '手順 3: フィールドのリスト ボックス表示 |Microsoft ドキュメント'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 315c32dc-aeb1-4629-b30e-87b44e8f84d1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e88957f03b821ee350a575080bd4f0fd40ce466b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272711"
---
# <a name="step-3-populate-the-fields-list-box"></a>手順 3: フィールドのリスト ボックスを表示します。
フィールド リスト ボックスを設定するには、クリック イベント ハンドラーに次のコードを挿入`lstMain`:  
  
```  
Private Sub lstMain_Click()  
    Dim rec As Record  
    Dim rs As Recordset  
    Set rec = New Record  
    Set rs = New Recordset  
    grs.MoveFirst  
    grs.Move lstMain.ListIndex  
    lstDetails.Clear  
    rec.Open grs  
    Select Case rec.RecordType  
        Case adCollectionRecord:  
            Set rs = rec.GetChildren  
            While Not rs.EOF  
                lstDetails.AddItem rs(0)  
                rs.MoveNext  
            Wend  
        Case adSimpleRecord:  
            recFields rec, lstDetails, txtDetails  
  
        Case adStructDoc:  
    End Select  
  
End Sub  
```  
  
 このコードを宣言し、ローカルのレコードと、レコード セット オブジェクトをインスタンス化`rec`と`rs`、それぞれします。  
  
 選択したリソースに対応する行`lstMain`の現在の行が行われる`grs`です。 詳細リスト ボックスをオフにし、および`rec`の現在の行でが開きます。`grs`ソースとして。  
  
 リソースがコレクションのレコードで指定された[RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md)、ローカルのレコード セット`rs`rec の子で開かれます。`lstDetails`の行から値が入力`rs`です。  
  
 リソースがの場合、単純なレコード`recFields`と呼びます。 詳細については`recFields`、次の手順を参照してください。  
  
 リソースが構造化ドキュメントの場合、コードは実装されません。  
  
## <a name="see-also"></a>参照  
 [インターネット発行シナリオ](../../../ado/guide/data/internet-publishing-scenario.md)   
 [手順 2: メイン リスト ボックスを初期化します。](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)   
 [手順 4: Details テキスト ボックスに値を設定する](../../../ado/guide/data/step-4-populate-the-details-text-box.md)
