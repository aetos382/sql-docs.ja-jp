---
title: Analysis Services の DMX クエリ デザイナーのユーザー インターフェイス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "10012"
- sql12.rtp.rptdesigner.dataview.asquerydesigner.f1
helpviewer_keywords:
- Analysis Services [DMX]
- DMX [Analysis Services], user interface
- query designers [DMX]
ms.assetid: 5fd726a4-aed7-4e6c-9404-ccb2db66cf26
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d8b4d662cb54e827f8810695c4945f2eee25d327
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37286708"
---
# <a name="analysis-services-dmx-query-designer-user-interface"></a>Analysis Services の DMX クエリ デザイナーのユーザー インターフェイス
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] にはグラフィカル クエリ デザイナーが用意されており、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ ソースに対するデータ マイニング式 (DMX) クエリおよび多次元式 (MDX) クエリの作成に使用できます。 このトピックでは、DMX クエリ デザイナーについて説明します。 MDX クエリ デザイナーの詳細については、次を参照してください。 [Analysis Services MDX クエリ デザイナーのユーザー インターフェイス](analysis-services-mdx-query-designer-user-interface.md)します。  
  
 DMX のグラフィカル クエリ デザイナーには、デザイン モード、クエリ モード、結果モードという 3 つのモードがあります。 モードを切り替えるには、クエリ デザイン ペインで右クリックして、モードを選択します。 すべてのモードにはメタデータ ペインが表示され、選択したキューブからメンバーをドラッグすることによって DMX クエリを作成できます。レポートの処理時には、このクエリに基づいてデータが取得され、データセットに格納されます。  
  
## <a name="graphical-dmx-query-designer-toolbar"></a>グラフィカル DMX クエリ デザイナーのツール バー  
 クエリ デザイナーのツール バーにある各種のボタンを使用すると、グラフィカル インターフェイスを使用した DMX クエリをデザインできます。 次の表は、これらのボタンとその機能を示しています。  
  
|ボタン|説明|  
|------------|-----------------|  
|**[テキストとして編集]**|この種類のデータ ソースでは無効です。|  
|**[インポート]**|ファイル システムのレポート定義 (.rdl) ファイルから既存のクエリをインポートします。 詳細については、「 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)と呼ばれます。|  
|![MDX クエリ ビューに変更](../../analysis-services/media/rsqdicon-commandtypemdx.gif "MDX クエリのビューへの変更")|MDX クエリ デザイナーのモードに切り替えます。|  
|![DMX クエリ言語ビューへの変更](../media/rsqdicon-commandtypedmx.gif "DMX クエリ言語ビューへの変更")|DMX クエリ デザイナーのモードに切り替えます。|  
|![結果データの更新](../../analysis-services/media/rsqdicon-refresh.gif "結果データの更新")|データ ソースからメタデータを更新します。|  
|![削除](../../analysis-services/media/rsqdicon-delete.gif "削除")|データ ペインで選択した列をクエリから削除します。|  
|![[クエリ パラメーター] ダイアログ ボックスのアイコン](../../analysis-services/media/iconqueryparameter.gif "[クエリ パラメーター] ダイアログ ボックスのアイコン")|**[クエリ パラメーター]** ダイアログ ボックスを表示します。 変数に既定値を割り当てた場合、レポート デザイナーで [レイアウト] ビューに切り替えたときに、対応するレポート パラメーターが作成されます。|  
|![クエリを実行する](../../analysis-services/media/rsqdicon-run.gif "クエリを実行する")|クエリを準備します。|  
|![デザイン モードに切り替える](../../analysis-services/media/rsqdicon-designmode.gif "デザイン モードに切り替える")|デザイン モードとクエリ モードを切り替えます。 結果ビューに切り替えるには、デザイン ペインを右クリックして **[結果]** を選択します。|  
  
## <a name="graphical-dmx-query-designer-in-design-mode"></a>グラフィカル DMX クエリ デザイナー (デザイン モード)  
 有効なキューブはないが、有効なマイニング モデルはある [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ ソースを使用するデータセットを編集する場合、グラフィカル クエリ デザイナーはデザイン モードで開きます。 次の図は、デザイン モードで表示される各ペインの名称を示しています。  
  
 ![Analysis Services DMX クエリ デザイナー、デザイン ビュー](../media/rsqd-dsawas-dmx-designmode.gif "Analysis Services DMX クエリ デザイナー、デザイン ビュー")  
  
 次の表に各ペインの機能を示します。  
  
|ペイン|機能|  
|----------|--------------|  
|クエリ デザイン ペイン|DMX クエリを作成するには、 **[マイニング モデル]** ダイアログ ボックスおよび **[入力テーブルの選択]** ダイアログ ボックスを使用します。|  
|グリッド ペイン|グリッドの各行について、 **[ソース]** ボックスの一覧から関数または式を選択し、DMX クエリで使用するフィールド、グループ、条件 (または引数) などを選択します。 選択した情報に基づいて生成された DMX クエリ テキストを表示するには、ツール バーの **[デザイン モード]** ボタンをクリックします。|  
  
 DMX クエリを実行して、結果ペインに結果を表示するには、クエリ デザイン ペインを右クリックし、 **[結果]** をクリックします。  
  
## <a name="graphical-dmx-query-designer-in-query-mode"></a>グラフィカル DMX クエリ デザイナー (クエリ モード)  
 グラフィカル クエリ デザイナーをクエリ モードに切り替えるには、ツール バーの **[デザイン モード]** ボタンをクリックするか、クエリ デザイン画面を右クリックして、ショートカット メニューで **[クエリ]** をクリックします。 このモードを使用すると、DMX テキストを直接クエリ ペインに入力できます。  
  
 次の図は、クエリ モードで表示される各ペインの名称を示しています。  
  
 ![Analysis Services DMX クエリ デザイナー、クエリ ビュー](../media/rsqd-dsawas-dmx-querymode.gif "Analysis Services DMX クエリ デザイナー、クエリ ビュー")  
  
 次の表に各ペインの機能を示します。  
  
|ペイン|機能|  
|----------|--------------|  
|クエリ デザイン ペイン|DMX クエリを作成するには、 **[マイニング モデル]** ダイアログ ボックスおよび **[入力テーブルの選択]** ダイアログ ボックスを使用します。|  
|クエリ ペイン|DMX クエリ テキストをペイン内で直接表示または編集します。 **デザイン** モードに戻ると、DMX クエリ テキストに対して行った変更は失われます。|  
  
 DMX クエリを実行して、結果ペインに結果を表示するには、クエリ デザイン ペインを右クリックし、 **[結果]** をクリックします。  
  
## <a name="graphical-dmx-query-designer-in-result-mode"></a>グラフィカル DMX クエリ デザイナー (結果モード)  
 結果モードを表示するには、クエリ デザイン画面を右クリックし、ショートカット メニューで **[結果]** をクリックします。 結果モードに切り替えると、DMX クエリが自動的に実行されます。  
  
 次の図は、結果モードのクエリ デザイナーを示しています。  
  
 ![Analysis Services DMX クエリ デザイナー、結果ビュー](../media/rsqd-dsawas-dmx-resultmode.gif "Analysis Services DMX クエリ デザイナー、結果ビュー")  
  
 デザイン モードまたはクエリ モードに戻るには、結果ペインを右クリックし、 **[デザイン]** または **[クエリ]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [Analysis Services の MDX クエリ デザイナーでパラメーターを定義&#40;レポート ビルダーおよび SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md)   
 [共有データセットまたは埋め込みデータセットの作成 &#40;レポート ビルダーおよび SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Analysis Services 接続の種類の DMX のため&#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md)   
 [データ マイニング モデル &#40;DMX&#41; からデータを取得する &#40;SSRS&#41;](retrieve-data-from-a-data-mining-model-dmx-ssrs.md)   
 [RSReportDesigner 構成ファイル](../report-server/rsreportdesigner-configuration-file.md)   
 [Analysis Services の MDX のための接続の種類&#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md)   
 [Analysis Services 接続の種類の DMX のため&#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md)  
  
  
