---
title: クライアント側とサーバー側の XML 書式設定 (SQLXML 4.0) のアーキテクチャ |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], XML formatting architecture
- SQLOLEDB provider
- client-side XML formatting
- data providers [SQLXML], XML formatting architecture
- SQLNCLI, XML
- server-side XML formatting
- SQL Server Native Client, XML
- SQLXMLOLEDB Provider, XML formatting architecture
ms.assetid: 52440d9e-89fd-4c15-a008-a1ea99f41387
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 35fdd4d3407b31b00e1685f49f86b560b305b464
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39540122"
---
# <a name="architecture-of-client-side-and-server-side-xml-formatting-sqlxml-40"></a>クライアント側とサーバー側の XML 書式設定のアーキテクチャ (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  次の図は、サーバー側の XML 書式設定のアーキテクチャです。  
  
 ![サーバー側での XML 書式設定のアーキテクチャです。](../../../relational-databases/sqlxml/formatting/media/serversidexml.gif "サーバー側でのアーキテクチャの XML 書式設定します。")  
  
 この例では、クライアント側で指定されたコマンドがサーバーに送信されます。 サーバーでは XML ドキュメントが生成され、それがクライアントに返されます。 この場合、サーバーがのインスタンスを持つ[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 サーバー側の XML 書式設定では、SQLXMLOLEDB プロバイダーまたは SQLOLEDB プロバイダーのいずれかを使用できます。  SQLXMLOLEDB プロバイダーでは Sqlxml4.dll が使用されますが、これは SQLXML 4.0 に含まれています。 SQLOLEDB プロバイダーを使用する場合、既定では Sqlxmlx.dll により SQLXML の機能が提供されます。この dll は [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows または Microsoft Data Access Components (MDAC) 2.6 以降に含まれています。 SQLOLEDB で Sqlxml4.dll を使用するには、SQLOLEDB 接続オブジェクトで SQLXML Version プロパティを"SQLXML.4.0"を設定する必要があります。 いずれの場合も、サーバーでは XML ドキュメントが生成され、それがクライアントに送信されます。  
  
> [!NOTE]  
>  XPath クエリとアップデートグラムはクライアントで解析されます。 SQLXML 4.0 の XPath テンプレートまたはアップデートグラム機能を使用するには、Sqlxml4.dll を使用します。  
  
 次の図は、クライアント側の XML 書式設定のアーキテクチャです。  
  
 ![クライアント側での XML 書式設定のアーキテクチャです。](../../../relational-databases/sqlxml/formatting/media/clientsidexml.gif "クライアント側でのアーキテクチャの XML 書式設定します。")  
  
 この例では、クライアントで SQLXMLOLEDB プロバイダーが使用されます。 接続文字列に SQLOLEDB にデータ プロバイダーのプロパティを設定する必要があります。 SQLXML 4.0 ではこの値だけが許容されます。クライアントで実行されたコマンドがサーバーに送信されます。 サーバーで生成された行セットがクライアントに送信されます。 クライアントでは、行セットから XML ドキュメントの書式が設定されます。  
  
 SQLXML 4.0 では、データ プロバイダーとして [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) または SQLOLEDB プロバイダーを使用できます。 これらのプロバイダーでは、どのデータ ソースにもアクセスできます。 クエリで単一の行セットが返される限り、XML 変換はクライアント側で適用できます。  
  
  
