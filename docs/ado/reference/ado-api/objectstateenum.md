---
title: ObjectStateEnum |Microsoft ドキュメント
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
- ObjectStateEnum
helpviewer_keywords:
- ObjectStateEnum enumeration [ADO]
ms.assetid: 32746558-097b-4749-989e-519aadf7e3f4
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 46030a27b9a2567f023c2c0d7946536703c91195
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279983"
---
# <a name="objectstateenum"></a>ObjectStateEnum
オブジェクトがオープンかクローズは、コマンドを実行するか、データを取得するデータ ソースに接続するかどうかを指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adStateClosed**|0|オブジェクトが閉じられたことを示します。|  
|**adStateOpen**|1|オブジェクトが開かれていることを示します。|  
|**adStateConnecting**|2|オブジェクトが接続することを示します。|  
|**adStateExecuting**|4|オブジェクトが、コマンドを実行することを示します。|  
|**adStateFetching**|8|オブジェクトの行が取得されていることを示します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.ObjectState.CLOSED|  
|AdoEnums.ObjectState.OPEN|  
|AdoEnums.ObjectState.CONNECTING|  
|AdoEnums.ObjectState.EXECUTING|  
|AdoEnums.ObjectState.FETCHING|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[State プロパティ (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)|[State プロパティ (ADO)](../../../ado/reference/ado-api/state-property-ado.md)|
