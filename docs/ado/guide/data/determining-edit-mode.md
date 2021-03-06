---
title: 編集モードを決定する |Microsoft ドキュメント
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
- editing data [ADO], edit mode
- ADO, editing data
ms.assetid: 4c7e010d-08cd-4e22-9b32-23c36f02f88c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5971234a7e758318acaac80b830d312327e14e8
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270351"
---
# <a name="determining-edit-mode"></a>編集モードの決定
ADO では、現在のレコードに関連付けられている編集バッファーを保持します。 **EditMode**プロパティは、このバッファーの変更が加えられたかどうかや、新しいレコードが作成されたかどうかを示します。 使用して**EditMode**現在のレコードの編集状態を確認します。 編集のプロセスが中断された場合は、保留中の変更をテストして使用する必要があるかどうかを判断、**更新**または**ただし**メソッドです。  
  
 **EditMode**のいずれかを返します、 **EditModeEnum**定数は、次の表に記載されています。  
  
|定数|説明|  
|--------------|-----------------|  
|**adEditNone**|進行中の編集操作がないことを示します。|  
|**adEditInProgress**|現在のレコード内のデータが変更されたが保存されませんを示します。|  
|**adEditAdd**|示します、 **AddNew**メソッドが呼び出されて、れ、コピー バッファーの現在のレコードが新しいレコードがデータベースに保存されていないでします。|  
|**adEditDelete**|現在のレコードが削除されたことを示します。|  
  
 **EditMode**現在のレコードがある場合にのみ、有効な値を返すことができます。 **EditMode**場合に、エラーが返されます**BOF**または**EOF**は**True**または現在のレコードが削除された場合。
