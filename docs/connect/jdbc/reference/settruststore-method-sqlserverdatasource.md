---
title: setTrustStore メソッド (SQLServerDataSource) |Microsoft Docs
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
- setTrustStore Method (SQLServerDataSource)
apilocation:
- setTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: bab5485d-4547-426c-adbe-44e2b5702d1d
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf5d6034fbf2e9ce9d1c1b58909146dbcf56f0c6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38042282"
---
# <a name="settruststore-method-sqlserverdatasource"></a>setTrustStore メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  証明書の trustStore ファイルへのパス (ファイル名を含む) を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setTrustStore(java.lang.String trustStore)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *trustStore*  
  
 証明書の trustStore ファイルへのパス (ファイル名を含む) を表す **String** です。  
  
## <a name="remarks"></a>Remarks  
 trustStore プロパティが指定されていないか null に設定されている場合、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] は、信頼マネージャー ファクトリの検索ルールに従って、使用する証明書ストアを決定します。 既定の SunX509 TrustManagerFactory では、次の場所で、この順序に従ってトラスト マテリアルの検索が行われます。  
  
-   1. Java 仮想マシン (JVM) システム プロパティの "javax.net.ssl.trustStore" で指定されたファイル  
  
-   2. "\<java ホーム >/ライブラリ/セキュリティ/jssecacerts"ファイル。  
  
-   3. "\<java ホーム >/ライブラリ/セキュリティ/cacerts"ファイル。  
  
 詳細については、Sun Microsystems の Web サイトにある SunX509 TrustManager Interface に関するドキュメントを参照してください。  
  
 trustStore プロパティが文字列または空の文字列 "" に設定されている場合、ドライバーはその値を使用して trustStore ファイルを検索し、サーバーの SSL 証明書を検証します。  
  
 trustStorePassword プロパティは trustStore プロパティと共に指定でき、その値を trustStore ファイルを開くために使用します。 詳細については、「[setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
