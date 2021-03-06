---
title: テーブルのプロパティ ダイアログ ボックス (SSAS) の編集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.edittablepropdb.f1
ms.assetid: 8d913e83-7246-44cc-8fc7-31729023c0d8
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cd8e464967dbe4b2546f51889f2a2da49d81e4df
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249592"
---
# <a name="edit-table-properties-dialog-box-ssas"></a>[テーブルのプロパティの編集] ダイアログ ボックス (SSAS)
  **[テーブルのプロパティの編集]** ダイアログ ボックスを使用すると、テーブルのインポート ウィザードを使用してモデル デザイナーにインポートされたテーブルのプロパティを表示して変更を加えることができます。 このダイアログ ボックスにアクセスするには、モデル デザイナーでテーブルを選択し、 **[テーブル]** メニュー、 **[テーブルのプロパティ]** の順にクリックします。  
  
## <a name="uielement-list"></a>UI 要素の一覧  
 このダイアログ ボックスのオプションは、最初にデータをインポートしたときに一覧からテーブルを選択したか SQL クエリを使用したかによって異なります。  
  
## <a name="table-preview-mode"></a>テーブルのプレビュー モード  
 **テーブル名**  
 モデル内のデータ テーブルの名前が表示されます。  
  
> [!NOTE]  
>  ここで名前を編集することはできません。 テーブル名は、モデル デザイナーの下部にあるテーブル タブを右クリックして変更できます。  
  
 **[接続名]**  
 現在使用している接続の名前が表示されます。  
  
 **ソース名**  
 データの取得先のテーブルが表示されます。変更することもできます。  
  
 現在のテーブルと異なる列を持つテーブルにソースを変更すると、列が異なることを示す警告メッセージが表示されます。 現在のテーブルに含める列を選択し、 **[保存]** をクリックします。 テーブルの左側にあるチェック ボックスをオンにすると、テーブル全体を置換できます。  
  
> [!NOTE]  
>  テーブルのデータ ソースを変更すると、事実上、現在のテーブルの内容が、新しいソース テーブルの内容で置換されます。  
  
 **列名**  
 |||  
|-|-|  
|**Source**|選択したソース テーブルの列名で現在の列名を置換します。|  
|**[モデル]**|モデル内に存在する現在の列名を使用します。|  
  
 **プレビューを更新します。**  
 クリックすると、現在選択しているソース テーブルのデータ列が表示されます。  
  
 **を切り替える**  
 |||  
|-|-|  
|**テーブルのプレビュー**|選択しているテーブルと限定された数行分のデータをプレビューします。|  
|**クエリ エディター**|選択しているデータ ソースに対するクエリを表示します。 このオプションは、すべてのデータ ソースで使用できるとは限りません。|  
  
 **列ヘッダーのチェック ボックス**  
 列をデータ インポートの対象にする場合は、チェック ボックスをオンにします。 列をデータ インポートの対象から除外する場合は、チェック ボックスをオフにします。  
  
 **列ヘッダーの矢印ボタンをクリックします。**  
 列のデータをフィルター処理します。  
  
 **行フィルターのクリア**  
 適用されているフィルターをすべて削除します。  
  
 **[OK]**  
 クリックすると、列の置換も含めて、加えたすべての変更が適用されます。  
  
## <a name="query-design-mode"></a>クエリ デザイン モード  
 **テーブル名**  
 モデル内のデータ テーブルの名前が表示されます。  
  
> [!NOTE]  
>  ここでは名前を編集できませんが、デザイナーの下部にあるテーブル タブを右クリックすると、テーブル名を変更できます。  
  
 **[接続名]**  
 現在使用している接続の名前が表示されます。  
  
 **を切り替える**  
 |||  
|-|-|  
|**テーブルのプレビュー**|選択しているテーブルと数行分のデータをプレビューします。|  
|**クエリ エディター**|選択しているデータ ソースに対して発行されるクエリを表示します。|  
  
 **Sql ステートメント**  
 行を取得するために、現在のデータ ソースに対して発行された SQL ステートメントが表示されます。 既定では、すべての行が取得されますが、フィルターをデザインするか、SQL ステートメントを手動で編集することによって、行のサブセットを取得することもできます。  
  
 **[検証]**  
 クリックすると、選択しているデータ ソースとプロバイダーについて、ステートメントの構文が正しいかどうかが検証されます。  
  
 **デザイン**  
 クリックすると、ビジュアル クエリ デザイナーが開き、クエリ ステートメントを作成できます。 デザイナーの使用方法の詳細については、デザイナーで F1 キーを押してください。  
  
 **[OK]**  
 クリックすると、列の置換も含めて、加えたすべての変更が適用されます。  
  
## <a name="see-also"></a>参照  
 [テーブルと列&#40;SSAS 表形式&#41;](tabular-models/tables-and-columns-ssas-tabular.md)  
  
  
