---
title: SQLXMLOLEDB プロバイダー (SQLXML 4.0) の使用 |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXMLOLEDB Provider, samples
- ClientSideXML property
ms.assetid: fbcefac5-29c9-478b-b0e0-d510b593f446
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 9bb4e182370670198f1bc7ed9d757adc36da9bde
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39534262"
---
# <a name="using-the-sqlxmloledb-provider-sqlxml-40"></a>SQLXMLOLEDB プロバイダーの使用 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  ここでは、SQLXMLOLEDB プロバイダー固有のプロパティの使用法を示す ADO サンプル アプリケーションを紹介します。  
  
## <a name="application-requirements-for-sqlxmloledb-40-provider"></a>SQLXMLOLEDB 4.0 プロバイダーのアプリケーション要件  
 SQLXMLOLEDB 4.0 を使用する実際のサンプルを作成するには、次の作業が必要です。  
  
1.  Microsoft Visual Basic の .exe アプリケーションを作成し、次のいずれかの参照を追加します。  
  
    -   Microsoft ActiveX データ オブジェクト 2.6 ライブラリ  
  
    -   Microsoft ActiveX データ オブジェクト 2.7 ライブラリ  
  
    -   Microsoft ActiveX Data Objects 2.8 Library  
  
2.  SQLXML 4.0 と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を配置し、インストールします。  
  
     詳細についてを参照してください[SQLXML 4.0 のプログラミング概念](../../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)と[SQL Server Native Client をインストールする](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SQL クエリの実行&#40;SQLXMLOLEDB プロバイダー&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-sql-queries-sqlxmloledb-provider.md)  
 SQL クエリを実行する ClientSideXML および xml ルート プロパティの使用方法を示します。  
  
 [SQL クエリを含むテンプレートの実行&#40;SQLXMLOLEDB プロバイダー&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md)  
 ClientSideXML プロパティの使用方法を示します。  
  
 [XPath クエリの実行&#40;SQLXMLOLEDB プロバイダー&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-sqlxmloledb-provider.md)  
 ClientSideXML、ベース パス、およびマッピング スキーマのプロパティの使用方法を示します。  
  
 [XPath クエリの名前空間を持つ実行&#40;SQLXMLOLEDB プロバイダー&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md)  
 名前空間の修飾子が付けられたスキーマに対してクエリを実行する方法を示します。  
  
 [XPath クエリを含むテンプレートの実行&#40;SQLXMLOLEDB プロバイダー&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-xpath-queries-sqlxmloledb-provider.md)  
 ClientSideXML、ベース パス、およびマッピング スキーマのプロパティを使用して SQL クエリでテンプレートを実行する方法を示しています。  
  
 [XSL 変換の適用&#40;SQLXMLOLEDB プロバイダー&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/applying-an-xsl-transformation-sqlxmloledb-provider.md)  
 XSL 変換の適用で ClientSideXML と xsl プロパティの使用方法を示します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client のシステム要件](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md)  
  
  
