---
title: ADORecordConstruction インターフェイス |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction
helpviewer_keywords:
- ADORecordConstruction interface [ADO]
ms.assetid: 52a5429e-5829-455e-be3b-31f05cbecf2d
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cadacd2dae2b21ea03187721eaee79aac848432f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275631"
---
# <a name="adorecordconstruction-interface"></a>ADORecordConstruction インターフェイス
**ADORecordConstruction**インターフェイスは、ADO を構築するために使用**レコード**オブジェクトを OLE DB から**行**C/C++ アプリケーション内のオブジェクト。  
  
 このインターフェイスは、次のプロパティをサポートします。  
  
## <a name="properties"></a>[プロパティ]  
  
|||  
|-|-|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|書き込み専用です。<br />OLE DB のコンテナーを設定**行**この ADO 上のオブジェクト**レコード**オブジェクト。|  
|[行](../../../ado/reference/ado-api/row-property-ado.md)|読み取り/書き込みです。<br />OLE DB を取得/設定**行**オブジェクトから/この ADO に**レコード**オブジェクト。|  
  
## <a name="methods"></a>メソッド  
 [なし] :  
  
## <a name="events"></a>イベント  
 [なし] :  
  
## <a name="remarks"></a>コメント  
 指定された OLE DB**行**オブジェクト (`pRow`)、ADO の構築**レコード**オブジェクト (`adoR`)、次の 3 つの基本的な操作を額。  
  
1.  ADO を作成する**レコード**オブジェクト。  
  
    ```  
    _RecordPtr adoR;  
    adoRs.CreateInstance(__uuidof(_Record));  
    ```  
  
2.  クエリ、 **IADORecordConstruction**インターフェイスを**レコード**オブジェクト。  
  
    ```  
    adoRecordConstructionPtr adoRConstruct=NULL;  
    adoR->QueryInterface(__uuidof(ADORecordConstruction),  
                        (void**)&adoRConstruct);  
    ```  
  
3.  呼び出す、 **IADORecordConstruction::put_Row**プロパティを設定するメソッド、OLE DB**行**、ADO 上のオブジェクト**レコード**オブジェクト。  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRow->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRConstruct->put_Row(pUnk);  
    ```  
  
 結果として得られる**adoR**オブジェクトは、ADO を表します**レコード**、OLE DB から構築されたオブジェクト**行**オブジェクト。  
  
 ADO**レコード**OLE DB のコンテナーからオブジェクトを作成することができますも**行**オブジェクト。  
  
## <a name="requirements"></a>要件  
 **バージョン:** ADO 2.0 以降  
  
 **ライブラリ:** msado15.dll  
  
 **UUID:** 00000567-0000-0010-8000-00AA006D2EA4
