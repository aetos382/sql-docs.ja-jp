---
title: Microsoft Drivers for PHP for SQL Server のディザスター リカバリー、高可用性のサポート |Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 73a80821-d345-4fea-b076-f4aabeb4af3e
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d75a0c4285bddc8d3c237be35a51f1904de6d60
ms.sourcegitcommit: f9d4f9c1815cff1689a68debdccff5e7ff97ccaf
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2018
ms.locfileid: "39367694"
---
# <a name="support-for-high-availability-disaster-recovery"></a>高可用性、障害復旧のサポート
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックでは、高可用性とディザスター リカバリーを実現する [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]向けの [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] のサポート (バージョン 3.0 で追加) について説明します。  [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]は [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] で新たにサポートされました。 [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] オンライン ブックを参照してください。  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] のバージョン 3.0 では、接続プロパティを使用して、(高可用性、障害回復) 可用性グループ (AG) の可用性グループ リスナーを指定できます。 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] アプリケーションを AlwaysOn データベースに接続しているときにフェールオーバーが発生した場合、元の接続は切断され、アプリケーションではフェールオーバー後に処理を続行するために新しい接続を開く必要があります。  
  
可用性グループ リスナーに接続しておらず、ホスト名に複数の IP アドレスが関連付けられている場合、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] では DNS エントリに関連付けられているすべての IP アドレスが順次繰り返し処理されます。 DNS サーバーが最初に返した IP アドレスがネットワーク インターフェイス カード (NIC) にバインドされていない場合、この処理に時間がかかる可能性があります。 可用性グループ リスナーに接続している場合、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] では同時にすべての IP アドレスとの間で接続の確立が試行されます。接続試行が成功した場合、ドライバーでは未解決の試行がすべて破棄されます。  
  
> [!NOTE]  
> 接続タイムアウト値を大きくし、接続再試行ロジックを実装することにより、アプリケーションが可用性グループに接続する確立が高まります。 また、可用性グループのフェールオーバーにより接続が失敗する可能性があるため、接続再試行ロジックを実装して、再接続されるまで、失敗した接続の再接続を試行する必要があります。  
  
## <a name="connecting-with-multisubnetfailover"></a>MultiSubnetFailover を使用した接続  
**MultiSubnetFailover** 接続プロパティを指定すると、アプリケーションが可用性グループまたはフェールオーバー クラスター インスタンスに配置され、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] ではすべての IP アドレスに対して接続を試行することで、プライマリ [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] インスタンス上のデータベースに接続が試行されます。 接続に対して **MultiSubnetFailover=true** を指定した場合、クライアントにより、オペレーティング システムの既定の TCP 再送信間隔より短い間隔で TCP 接続が再試行されます。 これにより、AlwaysOn 可用性グループまたは AlwaysOn フェールオーバー クラスター インスタンスのフェールオーバー後、再接続されるまでの時間を短縮することができます。単一サブネットとマルチサブネットの可用性グループ インスタンスおよびフェールオーバー クラスター インスタンスに適用することができます。  
  
SQL Server 2012 可用性グループ リスナーまたは SQL Server 2012 フェールオーバー クラスター インスタンスに接続するときには、必ず **MultiSubnetFailover=True** を指定してください。 **MultiSubnetFailover** を指定することで、SQL Server 2012 のすべての可用性グループおよびフェールオーバー クラスター インスタンスに対して高速フェールオーバーが有効化され、単一サブネットおよびマルチサブネットの AlwaysOn トポロジにおけるフェールオーバー時間が大幅に短縮されます。 マルチサブネット フェールオーバーの際には、クライアントは複数の接続を並列で試行します。 サブネット フェールオーバー中、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] では TCP 接続が積極的に再試行されます。  
  
接続文字列キーワードの詳細については[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]を参照してください[接続オプション](../../connect/php/connection-options.md)します。  
  
可用性グループ リスナーまたはフェールオーバー クラスター インスタンス以外に接続するときに **MultiSubnetFailover=true** を指定すると、パフォーマンスが低下する可能性があるため、このような指定はサポートされていません。  
  
可用性グループ内のサーバーに接続する際には、次のガイドラインに従います。  
  
-   単一サブネットまたはマルチサブネットに接続する場合に **MultiSubnetFailover** 接続プロパティを使用すると、パフォーマンスを向上させることができます。  
  
-   可用性グループに接続するには、接続文字列でサーバーとして、可用性グループの可用性グループ リスナーを指定します。  
  
-   64 個を超える数の IP アドレスが構成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] インスタンスに接続すると、接続エラーが発生します。  
  
-   **MultiSubnetFailover** 接続プロパティを使用するアプリケーションの動作は、認証の種類 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 認証、Kerberos 認証、または Windows 認証) の影響を受けません。  
  
-   **loginTimeout** の値を増やすことで、フェールオーバー時間に対応し、アプリケーションの接続試行回数を減らすことができます。  
  
-   分散トランザクションはサポートされていません。  
  
読み取り専用のルーティングが無効である場合、次の状況では可用性グループのセカンダリ レプリカの場所には接続できません。  
  
- セカンダリ レプリカの場所が、接続を許可するように構成されていない。  
  
- アプリケーションに **ApplicationIntent=ReadWrite** (後述します) が使用されているが、セカンダリ レプリカの場所が読み取り専用アクセスとして構成されている。  
  
プライマリ レプリカが読み取り専用ワークロードを拒否するように構成されているとき、接続文字列に **ApplicationIntent=ReadOnly** が含まれていると、接続は失敗します。  

## <a name="transparent-network-ip-resolution-tnir"></a>透過的なネットワーク IP の解決 (TNIR)

透過的なネットワーク IP 解決 (TNIR) では、既存の MultiSubnetFailover 機能のリビジョンです。 ドライバーの接続シーケンスは、最初の解決のホスト名の IP が応答しないと、ホスト名に関連付けられている複数の ip アドレスがある場合に影響します。 MultiSubnetFailover と共に、次の 4 つの接続シーケンスを提供します。 

- 有効になっている TNIR & MultiSubnetFailover 無効になっている: 1 つの IP が試行された後に並列ですべての ip アドレス
- TNIR で有効になっている & MultiSubnetFailover を有効にしますすべての ip アドレスが並列で試行されます。
- TNIR 無効 & MultiSubnetFailover 無効: すべての ip アドレスが試行された 1 つずつ
- TNIR 無効 & MultiSubnetFailover を有効にします。 すべての ip アドレスは、並列で試行します。

既定では、TNIR が有効になり、MultiSubnetFailover が既定で無効になっています。

これは、両方の TNIR および MultiSubnetFailover PDO_SQLSRV ドライバーを使用して有効にする例を示します。

```
<?php
$serverName = "yourservername";
$username = "yourusername";
$password = "yourpassword";
$connectionString = "sqlsrv:Server=$serverName; TransparentNetworkIPResolution=Enabled; MultiSubnetFailover=yes";
try {
    $conn = new PDO($connectionString, $username, $password, array(PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION));
    // your code 
    // more of your code
    // when done, close the connection
    unset($conn);
} catch(PDOException $e) {
    print_r($e->errorInfo);
}
?>
```

## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>データベース ミラーリングの使用からマルチサブネット クラスターの使用へのアップグレード  
接続文字列に **MultiSubnetFailover** および **Failover_Partner** の接続キーワードが存在する場合、接続エラーが発生します。 また、**MultiSubnetFailover** が使用されているとき、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] から、データベース ミラーリング ペアに属していることを示すフェールオーバー パートナー応答が返された場合にも、エラーが発生します。  
  
現在、データベース ミラーリングを使用している [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] アプリケーションをマルチサブネットのシナリオにアップグレードする場合、**Failover_Partner** 接続プロパティを削除して **MultiSubnetFailover** に置き換え、それを **Yes** に設定し、接続文字列内のサーバー名を可用性グループ リスナーの名前に置き換えます。 接続文字列で **Failover_Partner** および **MultiSubnetFailover=true** が使用されている場合、ドライバーでエラーが発生します。 ただし、接続文字列に **Failover_Partner** と **MultiSubnetFailover=false** (または **ApplicationIntent=ReadWrite**) が使用されている場合、アプリケーションではデータベース ミラーリングが使用されます。  
  
AG のプライマリ データベースでデータベース ミラーリングが使用されている場合、および可用性グループ リスナーではなく、プライマリ データベースに接続する接続文字列内で **MultiSubnetFailover=true** が使用されている場合、ドライバーではエラーが返されます。  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="see-also"></a>参照  
[サーバーへの接続](../../connect/php/connecting-to-the-server.md)  
  
