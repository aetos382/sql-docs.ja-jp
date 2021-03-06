---
title: RDS オブジェクト モデルの概要 |Microsoft ドキュメント
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
- RDS objects [ADO], object model summary
- RDS object model [ADO]
ms.assetid: 909f9af7-31db-4eec-ad52-650ce74dac2f
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ecbfaf946dfdd6744ddd6ed5d6d8f9ef654f52a6
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274121"
---
# <a name="rds-object-model-summary"></a>RDS オブジェクト モデルの概要
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
|オブジェクト|説明|  
|------------|-----------------|  
|[RDS.DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)|このオブジェクトには、サーバー プロキシを取得するメソッドが含まれています。 プロキシには、既定またはカスタム サーバー プログラム (ビジネス オブジェクト) があります。 サーバー プログラムは、インターネット、イントラネット、ローカル エリア ネットワークで呼び出すことがまたはまたはローカルのダイナミック リンク ライブラリです。<br /><br /> **DataSpace**オブジェクトにスクリプトを実行しても安全です。|  
|[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|このオブジェクトは、既定のサーバー プログラムを表します。 既定 RDS のデータの取得と更新動作を実行します。<br /><br /> **DataFactory**オブジェクトはスクリプトを実行しても安全ではありません。|  
|[RDS.DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)|このオブジェクトは自動的に呼び出すことができます、 **.rds ですDataSpace**と**RDSServer.DataFactory**オブジェクト。<br /><br /> このオブジェクトを使用して、既定 RDS データの取得や更新プログラムの動作を呼び出します。<br /><br /> このオブジェクトは、返されたアクセスするビジュアル コントロールするための手段も用意されています。 **Recordset**オブジェクト。<br /><br /> **DataControl**オブジェクトにスクリプトを実行しても安全です。|  
  
## <a name="see-also"></a>参照  
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [RDS のシナリオ](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [RDS チュートリアル](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [RDS の使用方法とセキュリティ](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


