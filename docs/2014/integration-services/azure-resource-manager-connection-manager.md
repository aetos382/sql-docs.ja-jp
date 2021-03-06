---
title: Azure Resource Manager 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPARMCM.F1
- SQL11.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: a2380258-0418-4a8c-a731-5071a44ddf1e
caps.latest.revision: 2
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ddde8d5e677dd2cf480ca523c97cfd8e04bf67ab
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169273"
---
# <a name="azure-resource-manager-connection-manager"></a>Azure Resource Manager 接続マネージャー
**Azure Resource Manager 接続マネージャー**により、SSIS パッケージは[サービス プリンシパル](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal)を使って Azure リソースを管理できます。

**Azure Resource Manager 接続マネージャー**を作成して構成するには、以下の手順のようにします。

1. **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[AzureResourceManager]** を選び、**[追加]** をクリックします。
2. **[Azure Resource Manager Connection Manager Editor]\(Azure Resource Manager 接続マネージャー エディター\)** ダイアログ ボックスで、サービス プリンシパルの **[Application ID]\(アプリケーション ID\)**、**[Application Key]\(アプリケーション キー\)**、**[Tenant ID]\(テナント ID\)** を指定します。 これらのプロパティについて詳しくは、[こちら](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal)の記事をご覧ください。
3. **[OK]** をクリックしてダイアログ ボックスを閉じます。
4. 作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。
