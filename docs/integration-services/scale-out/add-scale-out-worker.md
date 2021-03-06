---
title: SSIS Scale Out Manager による Scale Out Worker の追加 | Microsoft Docs
description: この記事では、Scale Out Manager を使用して、既存の Scale Out 環境に SSIS Scale Out Worker を追加する方法について説明します。
ms.custom: performance
ms.date: 12/19/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: f4f9f055cefe4e3212066ea06868e88e399eaf36
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35335906"
---
# <a name="add-a-scale-out-worker-with-scale-out-manager"></a>Scale Out Manager による Scale Out Worker の追加

Integration Services Scale Out Manager を使用すると、既存の Scale Out 環境に Scale Out Worker を追加するプロセスが簡単になります。 

次の手順に従って、Scale Out トポロジに Scale Out Worker を追加します。

## <a name="1-install-scale-out-worker"></a>1.Scale Out Worker をインストールする
SQL Server のインストール ウィザードの **[機能の選択]** ページで、[統合サービス] と [スケール アウト ワーカー] を選択します。 
![Worker 機能の選択](media/feature-select-worker.PNG)

**[Integration Services Scale Out の構成 - ワーカーノード]** ページで、**[次へ]** をクリックして、この時点での構成を省略し、**[Scale Out Manager]** を使用してインストール後に構成することができます。

インストール ウィザードを最後まで実行します。

## <a name="2-open-the-firewall-on-the-scale-out-master-computer"></a>2.Scale Out Master コンピューターでファイアウォールを開く
Scale Out Master コンピューターの Windows ファイアウォールで、Scale Out Master のインストール時に指定したポート (既定では 8391) と SQL Server のポート (既定では 1433) を開きます。

## <a name="3-add-a-scale-out-worker-with-scale-out-manager"></a>3.Scale Out Manager による Scale Out Worker の追加
SQL Server Management Studio を管理者として実行し、Scale Out Master の SQL Server インスタンスに接続します。

オブジェクト エクスプローラーで、**[SSISDB]** を右クリックして、**[スケール アウトの管理]** を選択します。 

![スケール アウトの管理](media/manage-scale-out.PNG)

**[Scale Out Manager]** ダイアログ ボックスで、**[ワーカー マネージャー]** に切り替えます。 **[+]** を選択し、**[ワーカーの接続]** ダイアログ ボックスの指示に従います。 

## <a name="next-steps"></a>次の手順
詳細については、[Scale Out Manager](integration-services-ssis-scale-out-manager.md) に関するページを参照してください。