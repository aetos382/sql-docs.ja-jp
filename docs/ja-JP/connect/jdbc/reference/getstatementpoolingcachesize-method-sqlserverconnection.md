---
title: getStatementPoolingCacheSize メソッド (SQLServerConnection) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.getStatementPoolingCacheSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d8216c6d918a0333fdc88b3254736bd73f4be0bb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getstatementpoolingcachesize-method-sqlserverconnection"></a>getStatementPoolingCacheSize メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 この接続の準備されたステートメント キャッシュのサイズを返します。 '0' では、キャッシュ有効になっていないことを意味します。

## <a name="syntax"></a>構文  
  
```  
  
public int getStatementPoolingCacheSize()  
```  

## <a name="return-value"></a>戻り値
 **Int**の値を格納している**statementPoolingCacheSize**接続プロパティです。

## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>解説  
 このメソッドは、JDBC ドライバーのバージョン 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  