---
title: 列のデータ型を設定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 34e2d508-7b64-4503-a4f0-c6c6ad5f8a44
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c720f212a51ad9191e4f0bcd727dcee21f71e85e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="set-the-data-type-of-a-column"></a>列のデータ型の設定 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  モデルにデータをインポートするか、データを貼り付けると、モデル デザイナーによってデータ型の検出と適用が自動的に行われます。 データをモデルに追加したら、列のデータ型を手動で変更してデータの格納方法を変更できます。 代わりに、データの格納方法を変更せずに表示形式だけを変更することもできます。  
  
### <a name="to-change-the-data-type-or-display-format-for-a-column"></a>列のデータ型または表示形式を変更するには  
  
1.  モデル デザイナーで、データ型または表示形式を変更する列を選択します。  
  
2.  列の **[プロパティ]** ウィンドウで、次のいずれかの操作を行います。  
  
    -   **[データ形式]** プロパティで別のデータ形式を選択します。  
  
    -   **[データ型]** プロパティで別のデータ型を選択します。  
  
## <a name="considerations-when-changing-data-types"></a>データ型を変更するときの注意事項  
 列のデータ型を変更したり、データ変換を選択したりするときに、以下のいずれかのエラーが発生する場合があります。  
  
-   データ型を変更できませんでした  
  
-   列のデータ型を変更できませんでした  
  
 これらのエラーは、そのデータ型が [データ型] ボックスにオプションとして表示される場合でも発生する可能性があります。 ここでは、これらのエラーの原因と修正方法について説明します。  
  
### <a name="understanding-automatically-determined-data-types"></a>自動的に決定されたデータ型について  
 データをモデルに追加すると、モデル デザイナーによってデータ列がチェックされ、各列に格納されているデータ型が調べられます。 その列のデータが一貫している場合は、最も有効桁数の大きいデータ型が列に割り当てられます。  
  
 ただし、各列で 1 つのデータ型しか使用できない Excel または別のソースからデータを追加した場合は、列内のすべての値に対応できるデータ型がモデル デザイナーによって割り当てられます。 そのため、整数、長整数、通貨など、データ型の異なる数値が同じ列に含まれている場合、モデル デザイナーは decimal データ型を使用します。 また、同じ列に数値と文字列が混在している場合は、文字列データ型を使用します。 モデル デザイナーには、Excel で使用できる標準データ型のようなデータ型は用意されていません。  
  
 したがって、列に数値とテキスト値の両方が含まれている場合は、その列を数値データ型に変換することはできません。  
  
 Business Intelligence Semantic Model で使用できるデータ型は次のとおりです。  
  
-   **テキスト**  
  
-   **10 進数**  
  
-   **整数**  
  
-   **Currency**  
  
-   **TRUE/FALSE**  
  
-   **日付**  
  
 インポートしたデータのデータ型が間違っていた場合や、目的のデータ型と違っていた場合は、次の選択肢があります。  
  
-   データを再インポートします。 これを選択した場合は、データ ソースへの既存の接続を開いて列を再インポートします。 データ ソースの種類によっては、インポート中にフィルターを適用して、問題のある値を削除できる場合があります。  
  
-   計算列に DAX 数式を作成して、目的のデータ型の新しい値を作成します。 たとえば、TRUNC 関数を使用して小数点数を整数に変換したり、情報関数と論理関数を組み合わせて値をテストして変換したりすることができます。  
  
### <a name="understanding-data-conversion"></a>データ変換について  
 データ変換オプションを選択するとエラーが発生する場合は、選択した変換を列の現在のデータ型がサポートしていないことが考えられます。 すべてのデータ型ですべての変換を使用できるわけではありません。 たとえば、列をブール型に変更できるのは、列の現在のデータ型が数値 (整数または小数) またはテキストの場合だけです。 したがって、列のデータに適したデータ型を選択する必要があります。  
  
 適切なデータ型を選択した後、モデル デザイナーによって、有効桁数の損失や切り捨ての可能性など、データの変更についての警告が表示されます。 [OK] をクリックして受け入れ、データを新しいデータ型に変更します。  
  
 そのデータ型がサポートされていても、新しいデータ型の範囲でサポートされていない値が見つかった場合は、モデル デザイナーによって別のエラーが表示されます。この場合は、続行する前にデータ値を修正する必要があります。  
  
 Business intelligence semantic model で使用されるデータ型の詳細については、暗黙的に変換、およびさまざまなデータ型ではどのように式で使用するを参照してください[データ型はサポートされて](../../analysis-services/tabular-models/data-types-supported-ssas-tabular.md)です。  
  
## <a name="see-also"></a>参照  
 [サポートされているデータ型](../../analysis-services/tabular-models/data-types-supported-ssas-tabular.md)  
  
  