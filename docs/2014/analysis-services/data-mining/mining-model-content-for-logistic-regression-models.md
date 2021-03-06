---
title: ロジスティック回帰モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- mining model content, logistic regression models
- regression algorithms [Analysis Services]
ms.assetid: 69cc0b86-e8bc-4d6c-903e-85724f5c0396
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6af2d4d2e3f5007cbe0721fe734073e7306b95a3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328938"
---
# <a name="mining-model-content-for-logistic-regression-models-analysis-services---data-mining"></a>ロジスティック回帰モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)
  このトピックでは、Microsoft ロジスティック回帰アルゴリズムを使用するモデルに固有のマイニング モデル コンテンツについて説明します。 すべてのモデルの種類に共通の統計および構造を解釈する方法の説明、およびマイニング モデル コンテンツに関連する用語の一般的な定義については、「[マイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-analysis-services-data-mining.md)」を参照してください。  
  
## <a name="understanding-the-structure-of-a-logistic-regression-model"></a>ロジスティック回帰モデルの構造について  
 ロジスティック回帰モデルは、Microsoft ニューラル ネットワーク アルゴリズムで、非表示ノードを取り除くようモデルを制約するパラメーターを使用して作成されます。 そのため、ロジスティック回帰モデルの全体的な構造は、ニューラル ネットワークの全体的な構造とほぼ同じです。各モデルには、モデルとそのメタデータを表す 1 つの親ノードと、モデルで使用される入力に関する説明的な統計情報を提供する特殊なマージナル統計ノード (NODE_TYPE = 24) があります。  
  
 また、モデルには、予測可能な属性ごとにサブネットワーク (NODE_TYPE = 17) が含まれます。 ニューラル ネットワーク モデルの場合と同様、各サブネットワークには常に 2 つの分岐があります。1 つは入力層の分岐で、もう 1 つは、ネットワークの非表示層 (NODE_TYPE = 19) と出力層 (NODE_TYPE = 20) を含む分岐です。 複数の属性が予測のみとして指定されている場合、同じサブネットワークがそれらの属性で使用されることがあります。 入力でもある予測可能な属性を同じサブネットワークに含めることはできません。  
  
 ただし、ロジスティック回帰モデルでは、非表示層を表すノードは空であり、子はありません。 したがって、モデルには、個々の出力 (NODE_TYPE = 23) と個々の入力 (NODE_TYPE = 21) を表すノードが含まれますが、個々の非表示ノードは含まれません。  
  
 ![ロジスティック回帰モデルのコンテンツの構造](../media/skt-modelcontentstructure-logregc.gif "ロジスティック回帰モデルのコンテンツの構造")  
  
 既定では、ロジスティック回帰モデルは **Microsoft ニューラル ネットワーク ビューアー**に表示されます。 このカスタム ビューアーを使用して、入力属性およびその値をフィルター処理したり、出力への影響をグラフィカルに表示したりできます。 このビューアーのツールヒントには、入力値と出力値の各ペアに関連付けられている確率とリフトが示されます。 詳細については、「 [Microsoft ニューラル ネットワーク ビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-neural-network-viewer.md)」を参照してください。  
  
 入力およびサブネットワークの構造を参照したり、詳細な統計情報を表示したりするには、Microsoft 汎用コンテンツ ツリー ビューアーを使用します。 任意のノードをクリックして展開すると、子ノードを表示できます。ノードに含まれている重みやその他の統計情報を表示することもできます。  
  
## <a name="model-content-for-a-logistic-regression-model"></a>ロジスティック回帰モデルのモデル コンテンツ  
 ここでは、マイニング モデル コンテンツの列のうち、ロジスティック回帰に関連する列についてのみ詳細と例を紹介します。 このモデル コンテンツはニューラル ネットワーク モデルのものとほぼ同じなので、便宜上、この表にも、ニューラル ネットワーク モデルに当てはまる説明が記載されている場合があります。  
  
 ここに記載されていないスキーマ行セットの汎用の列 (MODEL_CATALOG や MODEL_NAME など) の詳細や、マイニング モデルの用語の説明については、「[マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-analysis-services-data-mining.md)」を参照してください。  
  
 MODEL_CATALOG  
 モデルが格納されているデータベースの名前。  
  
 MODEL_NAME  
 モデルの名前。  
  
 ATTRIBUTE_NAME  
 このノードに対応する属性の名前。  
  
|ノード|コンテンツ|  
|----------|-------------|  
|モデル ルート|空白|  
|マージナル統計|空白|  
|入力層|空白|  
|入力ノード|入力属性名|  
|非表示層|空白|  
|出力層|空白|  
|出力ノード|出力属性名|  
  
 NODE_NAME  
 ノードの名前。 現在、この列には NODE_UNIQUE_NAME と同じ値が格納されていますが、将来のリリースで変更される可能性があります。  
  
 NODE_UNIQUE_NAME  
 ノードの一意の名前。  
  
 モデルに関して名前と ID が表す構造情報の詳細については、「 [ノードの名前と ID の使用](#bkmk_NodeIDs)」のセクションを参照してください。  
  
 NODE_TYPE  
 ロジスティック回帰モデルでは、次のノードの種類が出力されます。  
  
|ノードの種類の ID|説明|  
|------------------|-----------------|  
|1|モデル。|  
|17|サブネットワークのオーガナイザー ノード。|  
|18|入力層のオーガナイザー ノード。|  
|19|非表示層のオーガナイザー ノード。 非表示層は空です。|  
|20|出力層のオーガナイザー ノード。|  
|21|入力属性ノード。|  
|23|出力属性ノード。|  
|24|マージナル統計ノード。|  
  
 NODE_CAPTION  
 ノードに関連付けられたラベルまたはキャプション。 ロジスティック回帰モデルでは常に空白です。  
  
 CHILDREN_CARDINALITY  
 ノードの子の推定数。  
  
|ノード|コンテンツ|  
|----------|-------------|  
|モデル ルート|子ノードの数を示します。1 つ以上のネットワーク、1 つの必須マージナル ノード、および 1 つの必須入力層が含まれます。 たとえば、値が 5 の場合はサブネットワークが 3 つあります。|  
|マージナル統計|常に 0 です。|  
|入力層|モデルで使用された入力属性と値のペアの数を示します。|  
|入力ノード|常に 0 です。|  
|hidden layer|ロジスティック回帰モデルでは常に 0 です。|  
|出力層|出力値の数を示します。|  
|出力ノード|常に 0 です。|  
  
 PARENT_UNIQUE_NAME  
 ノードの親の一意な名前です。 ルート レベルのノードには NULL を返します。  
  
 モデルに関して名前と ID が表す構造情報の詳細については、「 [ノードの名前と ID の使用](#bkmk_NodeIDs)」のセクションを参照してください。  
  
 NODE_DESCRIPTION  
 ノードについてのわかりやすい説明。  
  
|ノード|コンテンツ|  
|----------|-------------|  
|モデル ルート|空白|  
|マージナル統計|空白|  
|入力層|空白|  
|入力ノード|入力属性名|  
|非表示層|空白|  
|出力層|空白|  
|出力ノード|出力属性が連続属性の場合は、出力属性名が含まれます。<br /><br /> 出力属性が不連続属性または分離された属性の場合は、出力属性名と値が含まれます。|  
  
 NODE_RULE  
 ノードに埋め込まれたルールの XML による記述。  
  
|ノード|コンテンツ|  
|----------|-------------|  
|モデル ルート|空白|  
|マージナル統計|空白|  
|入力層|空白|  
|入力ノード|NODE_DESCRIPTION 列と同じ情報が含まれている XML フラグメント。|  
|hidden layer|空白|  
|出力層|空白|  
|出力ノード|NODE_DESCRIPTION 列と同じ情報が含まれている XML フラグメント。|  
  
 MARGINAL_RULE  
 ロジスティック回帰モデルでは常に空白です。  
  
 NODE_PROBABILITY  
 このノードに関連付けられている確率。 ロジスティック回帰モデルでは常に 0 です。  
  
 MARGINAL_PROBABILITY  
 親ノードからノードに到達する確率です。 ロジスティック回帰モデルでは常に 0 です。  
  
 NODE_DISTRIBUTION  
 ノードの統計情報を含む入れ子になったテーブル。 このテーブルの各ノードの種類のコンテンツに関する詳細についてで、NODE_DISTRIBUTION テーブルの理解、セクションを参照してください[ニューラル ネットワーク モデルのマイニング モデル コンテンツ&#40;Analysis Services - データ マイニング&#41;。](mining-model-content-for-neural-network-models-analysis-services-data-mining.md).  
  
 NODE_SUPPORT  
 ロジスティック回帰モデルでは常に 0 です。  
  
> [!NOTE]  
>  この種類のモデルの出力は確率論的でないため、サポート確率は常に 0 です。 このアルゴリズムで意味を持つのは重みだけです。したがって、確率、サポート、および分散は計算されません。  
  
 特定の値に対するトレーニング ケースでのサポートについて情報を得るには、マージナル統計ノードを参照してください。  
  
 MSOLAP_MODEL_COLUMN  
 |ノード|コンテンツ|  
|----------|-------------|  
|モデル ルート|空白|  
|マージナル統計|空白|  
|入力層|空白|  
|入力ノード|入力属性名。|  
|hidden layer|空白|  
|出力層|空白|  
|出力ノード|入力属性名。|  
  
 MSOLAP_NODE_SCORE  
 ロジスティック回帰モデルでは常に 0 です。  
  
 MSOLAP_NODE_SHORT_CAPTION  
 ロジスティック回帰モデルでは常に空白です。  
  
##  <a name="bkmk_NodeIDs"></a> ノードの名前と ID の使用  
 ロジスティック回帰モデルのノードの名前付けでは、モデル内のノード間のリレーションシップに関する追加情報が提供されます。 次の表に、各層のノードに割り当てられる ID の規則を示します。  
  
|ノードの種類|ノード ID の規則|  
|---------------|----------------------------|  
|モデル ルート (1)|00000000000000000.|  
|マージナル統計ノード (24)|10000000000000000|  
|入力層 (18)|30000000000000000|  
|入力ノード (21)|60000000000000000 から開始|  
|サブネットワーク (17)|20000000000000000|  
|非表示層 (19)|40000000000000000|  
|出力層 (20)|50000000000000000|  
|出力ノード (23)|80000000000000000 から開始|  
  
 出力属性が特定の入力層属性にどのように関連付けられているかをこれらの ID によって確認するには、出力ノードの NODE_DISTRIBUTION テーブルを表示します。 NODE_DISTRIBUTION テーブルの各行には、特定の入力属性ノードを指す ID が含まれています。 NODE_DISTRIBUTION テーブルには、その入力と出力のペアの係数も含まれています。  
  
## <a name="see-also"></a>参照  
 [Microsoft ロジスティック回帰アルゴリズム](microsoft-logistic-regression-algorithm.md)   
 [ニューラル ネットワーク モデルのマイニング モデル コンテンツ&#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)   
 [ロジスティック回帰モデルのクエリ例](logistic-regression-model-query-examples.md)   
 [Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス](microsoft-logistic-regression-algorithm-technical-reference.md)  
  
  
