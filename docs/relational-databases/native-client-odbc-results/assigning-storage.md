---
title: ストレージを割り当てます。マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 6780493f4c73462881ddb90393f5a571c1d673c6
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39540852"
---
# <a name="assigning-storage"></a>ストレージの割り当て
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  アプリケーションでは、SQL ステートメントの実行前後に、結果用のストレージを割り当てることができます。 アプリケーションで最初に SQL ステートメントを準備または実行すると、結果のストレージを割り当てる前に、結果セットに関する情報を取得できます。 たとえば、結果セットが不明であれば、アプリケーションでは、列にストレージを割り当てる前に、列数を取得する必要があります。  
  
 アプリケーションの呼び出しにデータの列の記憶領域を関連付けるには、 [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)し、それを渡します。  
  
-   データの変換先のデータ型。  
  
-   データの出力バッファーのアドレス。  
  
     アプリケーションではこのバッファーを割り当てる必要があります。このバッファーは、変換後の形式でデータを保持するのに十分な大きさを確保する必要があります。  
  
-   出力バッファーの長さ。  
  
     この値は、返されるデータが C の固定幅データ (整数、実数、日付構造体など) の場合は無視されます。  
  
-   使用できるデータのバイト数を返すストレージ バッファーのアドレス。  
  
 また、アプリケーションは、結果セットの列をプログラム変数の配列にバインドして、結果セットの行をブロック単位でフェッチする機能をサポートすることもできます。 配列バインディングの 2 つのさまざまな種類があります。  
  
-   列方向のバインドは、各列を変数の独自の配列にバインドすると終了します。  
  
     呼び出すことによって列方向のバインドが指定されている[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)と*属性*SQL_ATTR_ROW_BIND_TYPE を設定し、 *ValuePtr* SQL_BIND_BY_COLUMN に設定します。 すべての配列には、同じ数の要素を保持する必要があります。  
  
-   行方向のバインドは、SQL ステートメント内のすべてのパラメーターを 1 単位として、パラメーターの各変数を保持する構造体の配列にバインドすると終了します。  
  
     呼び出すことにより行方向のバインドが指定されている**SQLSetStmtAttr**と*属性*SQL_ATTR_ROW_BIND_TYPE を設定し、 *ValuePtr*保留されている構造体のサイズを設定、結果を受信する変数は、列を設定します。  
  
 また、アプリケーションでは、SQL_ATTR_ROW_ARRAY_SIZE を列または行の配列内の要素数に設定し、SQL_ATTR_ROW_STATUS_PTR と SQL_ATTR_ROWS_FETCHED_PTR も設定します。  
  
## <a name="see-also"></a>参照  
 [結果の処理&#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
