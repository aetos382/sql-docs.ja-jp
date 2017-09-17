---
title: "StayInSync プロパティ |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset20::StayInSync
- Recordset20::put_StayInSync
- Recordset20::PutStayInSync
- Recordset20::get_StayInSync
- Recordset20::GetStayInSync
helpviewer_keywords:
- StayInSync property
ms.assetid: 502d69b5-dc9a-455d-b115-a03bd39a552b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3951725cd3463af5cc4348cdb7803fe760345854
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="stayinsync-property"></a>StayInSync プロパティ
階層構造内に示します[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトかどうか、基になる子レコードへの参照 (つまり、*章*)、親の行の位置が変わったときに変更します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**ブール**値。 既定値は **True**です。 場合**True**、章に更新されます親**レコード セット**場合、オブジェクトの変更行位置; **False**チャプターは引き続き前のチャプター内のデータを参照してください場合でも、親**Recordset**オブジェクトには、行の位置が変更されました。  
  
## <a name="remarks"></a>解説  
 このプロパティでサポートされているなど、階層のレコード セットに適用されます、 [Microsoft Data Shaping Service for OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)、親に設定する必要があります**Recordset** 、子の前に**レコード セット**を取得します。 このプロパティは、階層レコード セットの移動を簡略化します。  
  
## <a name="applies-to"></a>適用対象  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [StayInSync プロパティの例 (VB)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [Microsoft データ シェイプ OLE DB (ADO サービス プロバイダー) 用サービス](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)