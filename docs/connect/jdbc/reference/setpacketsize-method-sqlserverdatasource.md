---
title: setPacketSize メソッド (SQLServerDataSource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d490edc-a223-4870-a838-784952497e5f
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 08f4f72aae10fc154b7362a83e870d85b9fb42e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32844607"
---
# <a name="setpacketsize-method-sqlserverdatasource"></a>setPacketSize メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  通信するために使用される現在のネットワーク パケット サイズを設定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]、バイト単位で指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setPacketSize(int packetSize)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *packetSize*  
  
 **Int**ネットワーク パケット サイズを含む値です。  
  
## <a name="remarks"></a>解説  
 このプロパティの値の許容範囲は、[-1 | 0 | 512..32767] です。 このプロパティが許容範囲外の値に設定されている場合は、例外が発生します。  
  
 SSL (Secure Sockets Layer) 暗号化を使用して接続しているときに、アプリケーションで packetSize プロパティを設定する場合があります。 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]サーバーとパケット サイズをネゴシエートします。 Encrypt プロパティ設定されている場合"**true**"ネゴシエートされたパケットのサイズが、Java 仮想マシン (JVM) の既定のセキュリティ プロバイダーの SSL レコード サイズよりも大きいと、ドライバーは、エラーが発生し、接続を終了します。  
  
 また、SSL 暗号化を要求せずにアプリケーションで packetSize プロパティを設定する場合もあります。 この場合、クライアントによる SSL 暗号化のサポートをサーバーで必要としているときは、JVM における既定のセキュリティ プロバイダーの SSL レコード サイズが、ドライバーによってチェックされます。 packetSize プロパティが JVM における既定のセキュリティ プロバイダーの SSL レコード サイズを超えるときは、ドライバーでエラーが発生して接続が終了します。  
  
 SSL の使用に関する詳細については、次を参照してください。 [SSL 暗号化を使用して](../../../connect/jdbc/using-ssl-encryption.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
