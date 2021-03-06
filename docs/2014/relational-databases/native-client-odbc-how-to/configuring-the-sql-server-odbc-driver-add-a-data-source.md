---
title: データ ソース (ODBC) の追加 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e8d3c51595caa5a65f5ac175bdf16a4333511b5
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432001"
---
# <a name="add-a-data-source-odbc"></a>データ ソースの追加 (ODBC)
  プログラムで ODBC アドミニストレーターを使用してデータ ソースを追加することができます (を使用して[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md))、またはファイルを作成します。  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>ODBC アドミニストレーターを使用してデータ ソースを追加するには  
  
1.  **コントロール パネルの **、アクセス**管理ツール**し**データ ソース (ODBC)** します。 または、odbcad32.exe を呼び出すことができます。  
  
2.  をクリックして、**ユーザー DSN**、**システム DSN**、または**ファイル DSN**タブをクリックし、をクリックし、**追加**します。  
  
3.  をクリックして**SQL Server**、 をクリックし、**完了**します。  
  
4.  SQL Server への新しいデータ ソースの作成ウィザードの手順に従って実行します。  
  
### <a name="to-add-a-data-source-programmatically"></a>データ ソースをプログラムで追加するには  
  
1.  呼び出す[SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)で 2 番目のパラメーターを ODBC_ADD_DSN または ODBC_ADD_SYS_DSN に設定します。  
  
### <a name="to-add-a-file-data-source"></a>ファイル データ ソースを追加するには  
  
1.  呼び出す[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) SAVEFILE = file_name パラメーター、接続文字列を指定します。 接続が確立されると、ODBC ドライバーによって、SAVEFILE パラメーターが指す場所の接続パラメーターを使用してファイル データ ソースが作成されます。  
  
## <a name="see-also"></a>参照  
 [SQL Server ODBC ドライバーを構成する方法に関するトピック](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
