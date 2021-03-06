---
title: グローバル設定 (テスト担当者) (SybaseToSQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 6f0b9cea-5a24-4e42-8bbf-c4516b00da23
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: cff28dcfed7c8afe35ecbc2b4241cb89de537dea
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34778928"
---
# <a name="global-settings-tester-sybasetosql"></a>グローバル設定 (テスト担当者) (SybaseToSQL)
テスト担当者のページを使用して、**グローバル設定**SSMA テスターの設定を指定 ダイアログ ボックス。  
  
テスト担当者の設定にアクセスする、**ツール**メニューの [**グローバル設定**、] をクリック**Tester**左側のウィンドウの下部にあります。  
  
## <a name="options"></a>および  
**テストが容易なオブジェクトの分析**  
この設定では、テスト可能なオブジェクトの分析を実行するかどうかを指定します。 選択**はい**SSMA Tester を分析し、依存オブジェクトを自動的にチェックする場合。 既定のオプション セットが**はい**です。  
  
次のオプションは、この設定に使用されます。  
  
1.  はい  
  
2.  いいえ  
  
**補助テーブルの保存モード**  
この設定は、テスト_ケースの実行中に作成された内部の補助テーブルを保存する方法を指定します。 この特定の設定には、次のオプションを設定できます。  
  
1.  常に削除します。  
  
2.  常に保存します。  
  
3.  テーブルの比較が失敗した場合の保存します。  
  
4.  テーブルの比較が失敗したかどうかの質問します。  
  
既定のオプション セット:**をいつでも削除**です。  
  
**データのロールバックを実行します。**  
この設定では、各テスト・ケースの実行後に、ロールバック操作を実行するかどうかを指定します。 既定のオプション セットが**いいえ**です。  
  
次のオプションは、この設定に使用されます。  
  
1.  はい  
  
2.  いいえ  
  
**最初のエラーの後にテストの実行を停止します。**  
実行中にエラーが発生した場合、この設定は現在実行中のテスト ケースを停止するかどうかを指定します。 既定のオプション セットが**はい**です。  
  
次のオプションは、この設定に使用されます。  
  
1.  はい  
  
2.  いいえ  
  
## <a name="see-also"></a>参照  
[テスト_ケース準備を完了&#40;SybaseToSQL&#41;](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md)  
  
