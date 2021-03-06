---
title: ストレージの割り当て |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- column-wise binding [ODBC]
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLBindCol function
- storing data [ODBC]
- result sets [ODBC], storage
- SQL Server Native Client ODBC driver, data storage
- row-wise binding
- binding result sets [SQL Server Native Client]
- array binding
ms.assetid: 11c81955-5300-495f-925f-9256f2587b58
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc3ce031d7f59395ec54abe1c21276e9b4be9054
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426352"
---
# <a name="assigning-storage"></a>ストレージの割り当て
  アプリケーションでは、SQL ステートメントの実行前後に、結果用のストレージを割り当てることができます。 アプリケーションで最初に SQL ステートメントを準備または実行すると、結果のストレージを割り当てる前に、結果セットに関する情報を取得できます。 たとえば、結果セットが不明であれば、アプリケーションでは、列にストレージを割り当てる前に、列数を取得する必要があります。  
  
 ストレージ データの列に関連付けるにアプリケーションを呼び出す[SQLBindCol](../native-client-odbc-api/sqlbindcol.md)を渡します。  
  
-   データの変換先のデータ型。  
  
-   データの出力バッファーのアドレス。  
  
     アプリケーションではこのバッファーを割り当てる必要があります。このバッファーは、変換後の形式でデータを保持するのに十分な大きさを確保する必要があります。  
  
-   出力バッファーの長さ。  
  
     この値は、返されるデータが C の固定幅データ (整数、実数、日付構造体など) の場合は無視されます。  
  
-   使用できるデータのバイト数を返すストレージ バッファーのアドレス。  
  
 また、アプリケーションは、結果セットの列をプログラム変数の配列にバインドして、結果セットの行をブロック単位でフェッチする機能をサポートすることもできます。 配列のバインドの 2 つの異なる種類あります。  
  
-   列方向のバインドは、各列を変数の独自の配列にバインドすると終了します。  
  
     呼び出すことによって、列方向のバインドが指定されて[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)で*属性*SQL_ATTR_ROW_BIND_TYPE に、 *ValuePtr* SQL_BIND_BY_COLUMN に設定します。 すべての配列には、同じ数の要素を保持する必要があります。  
  
-   行方向のバインドは、SQL ステートメント内のすべてのパラメーターを 1 単位として、パラメーターの各変数を保持する構造体の配列にバインドすると終了します。  
  
     呼び出すことによって、行方向のバインドが指定されて**SQLSetStmtAttr**で*属性*SQL_ATTR_ROW_BIND_TYPE に、 *ValuePtr*いる構造体のサイズに設定、列の結果を受け取る変数に設定します。  
  
 また、アプリケーションでは、SQL_ATTR_ROW_ARRAY_SIZE を列または行の配列内の要素数に設定し、SQL_ATTR_ROW_STATUS_PTR と SQL_ATTR_ROWS_FETCHED_PTR も設定します。  
  
## <a name="see-also"></a>参照  
 [結果の処理&#40;ODBC&#41;](processing-results-odbc.md)  
  
  
