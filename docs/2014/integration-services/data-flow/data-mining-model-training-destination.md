---
title: データ マイニング モデル トレーニング変換先 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingmodeltrainingdest.f1
helpviewer_keywords:
- destinations [Integration Services], Data Mining Model Training
- Data Mining Model Training destination
- mining models [Analysis Services], training
- training mining models
ms.assetid: 6bc8cbe2-46af-4f7b-93d6-86779313c9d7
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2bb23745ab0858cb598fd668d5f066f0e247d817
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171013"
---
# <a name="data-mining-model-training-destination"></a>データ マイニング モデル トレーニング変換先
  データ マイニング モデル トレーニング変換先は、変換先が受け取るデータをデータ マイニング モデル アルゴリズムに渡すことにより、データ マイニング モデルのトレーニングを行います。 複数のデータ マイニング モデルが同じデータ マイニング構造に基づいて構築されている場合は、1 つの変換先を使用してトレーニングできます。 詳細については、「 [マイニング構造列](../../analysis-services/data-mining/mining-structure-columns.md) 」と「 [マイニング モデル列](../../analysis-services/data-mining/mining-model-columns.md)」を参照してください。  
  
## <a name="configuration-of-the-data-mining-model-training-destination"></a>データ マイニング モデル トレーニング変換先の構成  
 対象になる構造とその構造に基づいて構築されているモデルのケース レベル列で、コンテンツの種類が KEY TIME または KEY SEQUENCE の列がある場合、入力データをその列で並べ替える必要があります。 たとえば、Microsoft タイム シリーズ アルゴリズムを使用して構築されたモデルでは、コンテンツの種類に KEY TIME が使用されます。 入力データが並べ替えられていない場合、そのモデルの処理が失敗する場合があります。 データを並べ替える必要がある場合、データ フロー内で事前に並べ替え変換を使用してデータを並べ替えることができます。 コンテンツの種類が KEY である列には、この要件は適用されません。 詳細については、「[コンテンツの種類 (データ マイニング)](../../analysis-services/data-mining/content-types-data-mining.md)」と「[並べ替え変換](transformations/sort-transformation.md)」を参照してください。  
  
> [!NOTE]  
>  データ マイニング モデル トレーニング変換先への入力は、並べ替えられている必要があります。 データを並べ替えるため、データ フロー内のデータ マイニング モデル トレーニング変換先の上流に、並べ替え変換を含めることができます。 詳細については、「 [Sort Transformation](transformations/sort-transformation.md)」を参照してください。  
  
 この変換先は 1 つの入力をとりますが、出力はありません。  
  
 データ マイニング モデル トレーニング変換先を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに接続するには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーを使用します。 詳しくは、「 [Analysis Services 接続マネージャー](../connection-manager/analysis-services-connection-manager.md)」をご覧ください。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[データ マイニング モデル トレーニング エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [データ マイニング モデル トレーニング エディター&#40;接続 タブ&#41;](../data-mining-model-training-editor-connection-tab.md)  
  
-   [データ マイニング モデル トレーニング エディター&#40;列 タブ&#41;](../data-mining-model-training-editor-columns-tab.md)  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [Common Properties](../common-properties.md)  
  
-   [データ マイニング モデル トレーニング変換先のカスタム プロパティ](data-mining-model-training-destination-custom-properties.md)  
  
 データ フロー コンポーネントのプロパティの設定方法については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
  
