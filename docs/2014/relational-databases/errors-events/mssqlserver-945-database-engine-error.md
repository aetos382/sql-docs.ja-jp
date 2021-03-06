---
title: MSSQLSERVER_945 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 78b25b97d22b13a380c7528c3d38aa4d4b2be4de
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416471"
---
# <a name="mssqlserver945"></a>MSSQLSERVER_945
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|945|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DB_IS_SHUTDOWN|  
|メッセージ テキスト|ファイルにアクセスできないか、メモリまたはディスク領域が不足しているので、データベース '%.*ls' を開けません。  詳細については、SQL Server エラー ログを確認してください。|  
  
## <a name="explanation"></a>説明  
 ファイルなどのリソースが存在しないため、データベースにアクセスできませんでした。  
  
## <a name="user-action"></a>ユーザーの操作  
 エラー ログを参照し、メモリ、ディスク領域、または権限のエラーに関する追加情報を確認してください。 影響を受けたデータベースの .mdf ファイルと .ndf ファイルの場所を確認し、[!INCLUDE[ssDE](../../includes/ssde-md.md)]で使用するアカウントにこれらのファイルへのアクセス権が与えられていることを確認します。 問題を解決した後、データベースを再起動します。この操作を行うには、ALTER DATABASE を使用して、データベースを ONLINE に設定します。  
  
  
