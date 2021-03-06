---
title: ReportItems コレクションの参照 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: edc0c75f-0530-4e6d-85aa-3385301bfd00
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: c0878c78af38a8d8b4d6b5d1c6f17a0188b5a50b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37264468"
---
# <a name="reportitems-collection-references-report-builder-and-ssrs"></a>ReportItems コレクションの参照 (レポート ビルダーおよび SSRS)
  組み込みコレクション `ReportItems` は、データ領域の行などのレポート アイテムのテキスト ボックスや、レポート デザイン画面上のテキスト ボックスのセットです。 `ReportItems`ページ ヘッダー、ページ フッター、またはレポート本文の現在のスコープ内にあるテキスト ボックスがコレクションに含まれています。 このコレクションは、レポート プロセッサおよびレポート レンダラーによって実行時に決定されます。 ユーザーがレポートのページを表示する際には、レポート プロセッサによってレポート データとレポート アイテムのレイアウト要素が連続的に結合されますが、これに伴って現在のスコープが変化します。 使用することができます、`ReportItems`各ページの最初と最後の項目を表示する辞書形式のページのヘッダーを生成する組み込みのコレクション。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-the-reportitems-value-property"></a>ReportItems の Value プロパティの使用  
 内のアイテム、`ReportItems`コレクションがある 1 つのプロパティ: 値。 `ReportItems` アイテムの値を使用すると、レポート内の別のフィールドのデータを表示または計算できます。 現在のテキスト ボックスの値にアクセスするには、 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] に組み込まれたグローバルの Me.Value を使用するか、単なる Value を使用します。 First 関数や集計関数などのレポート関数では、完全修飾された構文を使用してください。  
  
 以下に例を示します。  
  
-   テキスト ボックスで次の式を使用すると、`Textbox1` という名前の `ReportItem` テキスト ボックスの値が表示されます。  
  
     `=ReportItems!Textbox1.Value`  
  
-   この式では、内に配置する`ReportItem`が > 0 の値テキスト ボックスの Color プロパティに黒で、テキストが表示されます。 それ以外の場合、値が赤で表示されます。  
  
     `=IIF(Me.Value > 0,"Black","Red")`  
  
-   ページ ヘッダーまたはページ フッターのテキスト ボックスで次の式を使用すると、表示レポートのページごとに、 `LastName`という名前のテキスト ボックスの最初の値が表示されます。  
  
     `=First(ReportItems("LastName").Value)`  
  
## <a name="dictionary-style-page-header-expressions"></a>辞書形式のページ ヘッダー式  
 そのページ上の最初の顧客と最後の顧客を表示するページ ヘッダーを作成することができます。 ページ ヘッダーのテキスト ボックスでは、式の中で組み込みコレクション `ReportItems` を 1 回しか参照できないため、最初の顧客名用 (`=First(ReportItems!textboxLastName.Value`) と最後の顧客名用 (`=Last(ReportItems!textboxLastName.Value`) に 2 つのテキスト ボックスをページ ヘッダーに追加する必要があります。  
  
 ページ ヘッダー セクションやページ フッター セクションでは、`ReportItems` コレクションのメンバーとして使用できるのは、現在のページのテキスト ボックスのみです。 たとえば、 `ReportItems!textboxLastName.Value` が、複数ページにわたるデータ領域の最初のページにしか表示されないテキスト ボックスを参照している場合、最初のページでは値が表示されますが、その他すべてのページでは **#Error** と表示され、式が記述したとおりに評価できなかったことを示します。  
  
## <a name="scope-for-the-reportitems-collection"></a>ReportItems コレクションのスコープ  
 レポートが処理されると、レポート本文内またはデータ領域内の各テキスト ボックスは、そのデータセット、データ領域、およびグループの関連付けのコンテキストで評価されます。 参照のスコープ、`ReportItems`コレクションは、現在のスコープまたは現在のスコープより上位の場所。  
  
 たとえば、親グループの行の中にあるテキスト ボックスには、子グループの行の中にあるテキスト ボックスの名前を参照する式を含めることができません。 このような式は、子行のテキスト ボックスがスコープ外にあるため、レポート内の値に解決されません。 詳細については、「 [集計関数リファレンス (レポート ビルダーおよび SSRS)](report-builder-functions-aggregate-functions-reference.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [式内で組み込みコレクション&#40;レポート ビルダーおよび SSRS&#41;](built-in-collections-in-expressions-report-builder.md)   
 [式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Reporting Services の改ページ &#40;レポート ビルダーおよび SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [フィルター、グループ、およびデータの並べ替え&#40;レポート ビルダーおよび SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
