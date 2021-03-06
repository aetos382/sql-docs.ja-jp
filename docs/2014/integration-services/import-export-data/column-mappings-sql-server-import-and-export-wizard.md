---
title: 列マッピング (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.columnmapandtransform.f1
ms.assetid: eadc54a6-f936-4ffc-91d7-fbfd2bdcab93
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cb9f39f0eb06bb3a4bd4c2921b23736d1305db3f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281508"
---
# <a name="column-mappings-sql-server-import-and-export-wizard"></a>[列マッピング]\(SQL Server インポートおよびエクスポート ウィザード)
  使用して、**列マッピング**変換パラメーターを編集するためのダイアログ ボックス。  
  
> [!NOTE]  
>  テーブルをコピーするオプションを選択する際に、テーブル内のすべての列をコピーする必要はありません。 選択**\<無視 >** で、**先**をスキップする列の場合は、このダイアログ ボックスの列。  
  
 このウィザードの詳細については、次を参照してください。 [SQL Server インポートおよびエクスポート ウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)します。 ウィザードを正常に実行するために必要なアクセス許可と同様に、ウィザードを開始するためのオプションについては、次を参照してください。 [、SQL Server インポートおよびエクスポート ウィザードを実行](start-the-sql-server-import-and-export-wizard.md)します。  
  
 SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
## <a name="options"></a>および  
 **Source**  
 選択した変換元のテーブル、ビュー、またはクエリを識別します。  
  
 **変換先**  
 選択した変換先のテーブル、ビュー、またはクエリを識別します。  
  
 **変換先テーブル/ファイルの作成**  
 変換先テーブルが存在しない場合、変換先テーブルを作成するかするかどうかを指定します。  
  
 **変換先テーブル/ファイル内の行を削除する**  
 新しいデータを読み込む前に、既存のテーブルからデータを削除するかどうかを指定します。  
  
 **変換先テーブル/ファイルに行を追加する**  
 既存のテーブルに存在するデータに、新しいデータを追加するかどうかを指定します。  
  
 **SQL の編集**  
 既定のステートメントを使用して、**テーブル作成 SQL ステートメント** ダイアログ ボックス、または、目的に応じて変更します。 このステートメントを変更する場合、テーブル マップに関連する変更を行う必要があります。  
  
 **変換先テーブルを削除した後、再作成する**  
 変換先テーブルを上書きします。 このオプションは、ウィザードを使用して変換先テーブルを作成する場合にのみ使用できます。 ウィザードによって作成されたパッケージを保存し、その後パッケージを再び実行すると、変換先テーブルは削除されて、再作成されます。  
  
 **ID 挿入を許可する**  
 変換元データの既存の ID 値を変換先テーブルの ID 列に挿入します。 既定では、変換先の ID 列に対して挿入は許可されません。  
  
 **マッピング**  
 データ ソースの各列が変換先の列にどのようにマップされるかを表示します。  
  
 この一覧には、次の列があります。  
  
 **Source**  
 変換パラメーターを設定する各変換元列を表示します。  
  
 **変換先**  
 コピー操作中に列を無視するかどうかを指定します。 列のサブセットのみをコピーするを選択**\<無視 >** をスキップする列のこの列にします。 列をマップする前に、マップされないすべての列を無視する必要があります。  
  
 **型**  
 列のデータ型を選択します。  
  
 **NULL 値の使用**  
 列が NULL 値を使用するかどうかを指定します。  
  
 **Size**  
 列の文字数を指定します。  
  
 **Precision**  
 桁数を参照して、表示されるデータの有効桁数を指定します。  
  
 **Scale**  
 桁数を参照して、表示されるデータの小数点以下桁数を指定します。  
  
  
