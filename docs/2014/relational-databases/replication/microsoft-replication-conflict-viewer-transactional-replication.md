---
title: Microsoft レプリケーション競合表示モジュール (トランザクション レプリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.cvqueued.f1
ms.assetid: eec59d8e-cadb-4623-a31f-9f42ec09c97f
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a098bdec4b7ad5e7f213d4cb34f93a7b624b9c7e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296532"
---
# <a name="microsoft-replication-conflict-viewer-transactional-replication"></a>Microsoft レプリケーション競合表示モジュール (トランザクション レプリケーション)
  レプリケーション競合表示モジュールを使用すると、ピア ツー ピア トランザクション レプリケーション、およびキュー更新サブスクリプションを使用するトランザクション レプリケーションの同期中に発生した競合を表示できます。 詳細については、「[トランザクション パブリケーションのデータの競合の表示 &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)」を参照してください。  
  
> [!NOTE]  
>  レプリケーション競合表示モジュールでは、マージ レプリケーションおよびトランザクション レプリケーションで発生した競合が表示されます。 トランザクション レプリケーションの場合は、レプリケーション競合表示モジュールを使用して競合データを表示することはできますが、競合に対して別の解決策を選択することはできません。  
  
## <a name="options"></a>および  
 レプリケーション競合表示モジュールは 2 つのセクションに分かれています。 ダイアログ ボックスの上側のセクションには、選択されたテーブルの競合の一覧が表示されます。 競合の一覧の項目をクリックすると、競合の詳細がダイアログ ボックスの下側のセクションに表示されます。  
  
 下側のセクションの競合データは、2 つの対応する列 (**[競合で優先されたデータ]** と **[競合で優先されなかったデータ]**) に表示されます。 更新されたデータと削除されたデータの間で競合が発生した場合、競合で削除された側にデータが表示されない場合があります。 この場合、レプリケーション競合表示モジュールでは、その行が 1 か所では削除され別の箇所では更新されたことを示すメッセージが列の 1 つに表示されます。 また、提案された解決策についても示されます。  
  
 **[データベース]**  
 競合があるパブリケーションを含むデータベースを選択します。  
  
 **パブリケーション**  
 競合があるテーブルを含むパブリケーションを選択します。  
  
 **テーブル**  
 競合を含むテーブルを選択します。  
  
 **[フィルターの定義]**  
 **[フィルターの定義]** ダイアログ ボックスが表示されます。  
  
 **[フィルターの適用または削除]**  
 **[フィルターの定義]** ダイアログ ボックスで定義されたフィルターを適用または削除します。  
  
 **[すべて選択]**  
 グリッドに一覧表示されたすべての競合を選択します。  
  
 **[すべて選択解除]**  
 グリッドに一覧表示されたすべての競合の選択を解除します。  
  
 **[削除]**  
 選択された競合をビューアーから削除し、関連するメタデータをレプリケーション システム テーブルから削除します。  
  
 **[すべての列を表示]**  
 テーブルのすべての列を表示します。  
  
 **[最初の 5 列および競合データが含まれている列を表示]**  
 最初の 5 列および競合データが含まれている列を表示します。 これは、テーブルに多数の列があり、競合を解決するのに最も関連する列のみを表示する場合に便利です。 主キーや名前フィールドなど、行を識別するフィールドはテーブルの最初の列にある場合が多いため、このビューでは最初の 5 列が必ず表示されます。  
  
 **列情報の表示** (**[...]**)  
 列の情報である **[テーブル名]**、 **[列名]**、 **[データ型]**、および **[列の値]** を表示します。  
  
 **[競合の詳細をログに記録]**  
 このボックスをオンにすると、競合の詳細がファイルに記録されます。 ファイルの場所を指定するには、 **[表示]** メニューをポイントし、 **[オプション]** をクリックします。 値を入力するか、参照ボタン (**[...]**) をクリックして適切なファイルに移動します。 **[OK]** をクリックして、 **[オプション]** ダイアログ ボックスを終了します。  
  
## <a name="see-also"></a>参照  
 [ピア ツー ピア レプリケーションにおける競合検出](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [トランザクション パブリケーションのデータの競合の表示 &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
  
