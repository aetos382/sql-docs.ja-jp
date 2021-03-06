---
title: 'タスク 4: 照合アクティビティを Excel ファイルからの結果のエクスポート |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 644454c4-3c5a-469a-90ec-e51dc7fb99fc
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 13fcd1b697be6ad7aeebd933da1059955dc0649f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37179000"
---
# <a name="task-4-exporting-the-results-from-matching-activity-to-an-excel-file"></a>タスク 4: 照合アクティビティから Excel ファイルに結果をエクスポートする
  ここでは、照合アクティビティから Excel ファイルに結果をエクスポートします。  
  
1.  **エクスポート**] ページで、[ **Excel ファイル**の**変換先の型**します。  
  
2.  選択**サバイバーシップの結果**オプション。 サバイバーシップ プロセスで DQS によってに基づいて各クラスターに保持するレコードが、**サバイバーシップ ルール**を選択します。  
  
3.  クリックして**参照**出力ファイルを保存するフォルダーに移動します。  
  
4.  型**Cleansed and Matched Suppliers.xls**名とクリック**オープン**します。  
  
5.  確認します**ピボット レコード**が選択されている、**サバイバーシップ ルール**します。 このオプションを選択すると、各クラスターのピボット レコードがクラスターからの出力に選択されます。 サバイバーシップ ルールの他のオプションは次のとおりです。  
  
    1.  **最も完全なレコード:** で保持するレコードが設定されたフィールドの数が 1 つ。  
  
    2.  **最長のレコード:** で保持するレコードのソース フィールド内の語句の最大数です。  
  
    3.  **最も完全で最長のレコード:** で保持するレコードは、設定されたフィールドの最大数のものであり、語句の数が、各フィールド。  
  
     ![結果の照合 ページからエクスポート](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "照合 ページからの結果のエクスポート")  
  
6.  クリックして**エクスポート**結果を Excel ファイルにエクスポートします。  
  
7.  クリックして**閉じます**を閉じる、**一致するエクスポート** ダイアログ ボックス。  
  
8.  クリックして**完了**照合アクティビティを終了します。  
  
9. 開く、 **Cleansed and Matched Suppliers.xlsx**ファイルを開き、重複項目 (SupplierID) が表示されないことを確認します。  
  
 これで、仕入先データは重複項目を削除するためにクレンジングおよび照合されました。  
  
## <a name="next-step"></a>次の手順  
 [レッスン 4: MDS に仕入先データを格納する](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)  
  
  
