---
title: アイテム レベルのタスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- item-level tasks [Reporting Services]
ms.assetid: fdeb7bc3-167a-4342-84e3-32e3faa1fa39
caps.latest.revision: 36
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 43da85b3e7435bb3685090ae1f2e80830793b3f8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37150143"
---
# <a name="item-level-tasks"></a>アイテムレベルのタスク
  アイテムレベルのタスクとは、レポート、フォルダー、レポート モデル、リソース、共有データ ソースに関連する権限を集めたものです [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、レポート サーバー サイト全体に適用されるシステムレベル タスクもあります。 詳細については、「 [システムレベルのタスク](tasks-and-permissions-system-level-tasks.md)」を参照してください。 タスクと一般的な権限の詳細については、次を参照してください。[タスクと権限](tasks-and-permissions.md)します。  
  
> [!NOTE]  
>  プログラムでこれらのタスクを使用して処理を実行している場合、アイテムレベルのタスクをサポートしているメソッドを使用する必要があります。 詳細については、「 <xref:ReportService2010.ReportingService2010.ListTasks%2A> および <xref:ReportService2010.ReportingService2010.ListRoles%2A>」を参照してください。  
  
## <a name="permissions-in-item-level-tasks"></a>アイテムレベルのタスクの権限  
 次の表ではアイテムレベルのタスクを一覧表示し、各タスクに含まれる権限および権限が適用されるアイテムを示します。 権限の一覧は、タスクごとに利用できる機能をより詳細に示すためにのみ記載されています。  
  
 共有データセットは、レポートと同じ一連の権限を使用します。 レポート パーツは、リソースと同じ一連の権限を使用します。  
  
|タスク|適用される項目|アクセス許可|  
|----------|---------------------|-----------------|  
|レポートの使用|[レポート]|コンテンツの読み取り<br /><br /> レポート定義の読み込み<br /><br /> プロパティの読み取り|  
|レポートの使用|共有データセット|コンテンツの読み取り<br /><br /> レポート定義の読み込み<br /><br /> プロパティの読み取り|  
|リンク レポートの作成|[レポート]|リンクの作成<br /><br /> プロパティの読み取り|  
|すべてのサブスクリプションを管理|[レポート]|プロパティの読み取り<br /><br /> 任意のサブスクリプションの読み取り<br /><br /> 任意のサブスクリプションの作成<br /><br /> 任意のサブスクリプションの削除<br /><br /> 任意のサブスクリプションの更新|  
|データ ソースの管理|フォルダー|データ ソースの作成|  
|データ ソースの管理|ソリューション エクスプローラー|プロパティの更新<br /><br /> 更新コンテンツの削除<br /><br /> プロパティの読み取り|  
|フォルダーの管理|フォルダー|フォルダーの作成<br /><br /> 更新プロパティの削除<br /><br /> プロパティの読み取り|  
|個別のサブスクリプションを管理|レポート|プロパティの読み取り<br /><br /> サブスクリプションの作成<br /><br /> サブスクリプションの削除<br /><br /> サブスクリプションの読み取り<br /><br /> サブスクリプションの更新|  
|モデルの管理|フォルダー|モデルの作成|  
|モデルの管理|モデル|プロパティの読み取り<br /><br /> コンテンツの読み取り<br /><br /> 更新コンテンツの削除<br /><br /> データ ソースの読み取り<br /><br /> データ ソースの更新<br /><br /> モデル アイテム承認ポリシーの読み取り<br /><br /> モデル アイテム承認ポリシーの更新<br /><br /> 更新プロパティの削除|  
|レポート履歴の管理|[レポート]|プロパティの読み取り<br /><br /> レポート履歴の作成<br /><br /> レポート履歴の削除<br /><br /> 読み取りポリシーの実行<br /><br /> ポリシーの更新<br /><br /> レポート履歴の一覧表示|  
|レポートの管理|フォルダー|レポートの作成<br /><br /> 共有データセットの作成にも適用|  
|レポートの管理|[レポート]|プロパティの読み取り<br /><br /> 更新プロパティの削除<br /><br /> パラメーターの更新<br /><br /> データ ソースの読み取り<br /><br /> データ ソースの更新<br /><br /> レポート定義の読み取り<br /><br /> レポート定義の更新<br /><br /> 読み取りポリシーの実行<br /><br /> ポリシーの更新|  
|レポートの管理|共有データセット|プロパティの読み取り<br /><br /> 更新プロパティの削除<br /><br /> パラメーターの更新<br /><br /> データ ソースの読み取り<br /><br /> データ ソースの更新<br /><br /> レポート定義の読み取り<br /><br /> レポート定義の更新<br /><br /> 読み取りポリシーの実行<br /><br /> ポリシーの更新|  
|リソースの管理|フォルダー|リソースの作成|  
|リソースの管理|リソース|プロパティの更新<br /><br /> 更新コンテンツの削除<br /><br /> プロパティの読み取り|  
|リソースの管理|レポート パーツ|プロパティの更新<br /><br /> 更新コンテンツの削除<br /><br /> プロパティの読み取り|  
|アイテムごとにセキュリティを設定|レポート、リソース、データ ソース、共有データセット、フォルダー|セキュリティ ポリシーの読み取り、セキュリティ ポリシーの更新|  
|データ ソースの表示|データ ソース|コンテンツの読み取り<br /><br /> プロパティの読み取り|  
|フォルダーの表示|フォルダー|プロパティの読み取り<br /><br /> 実行および表示<br /><br /> レポート履歴の一覧表示|  
|モデルの表示|レポート モデル|プロパティの読み取り<br /><br /> コンテンツの読み取り<br /><br /> データ ソースの読み取り|  
|レポートの表示|[レポート]|コンテンツの読み取り<br /><br /> プロパティの読み取り|  
|レポートの表示|共有データセット|コンテンツの読み取り<br /><br /> プロパティの読み取り|  
|リソースの表示|リソース|コンテンツの読み取り<br /><br /> プロパティの読み取り|  
|リソースの表示|レポート パーツ|コンテンツの読み取り<br /><br /> プロパティの読み取り|  
  
## <a name="see-also"></a>参照  
 [ネイティブ モードのレポート サーバーに対する権限の許可](granting-permissions-on-a-native-mode-report-server.md)  
  
  
