---
title: ストアド プロシージャ (ODBC) を呼び出す |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 37ce27067c4ad30e38b6d3c168b8f676815b693d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411301"
---
# <a name="call-stored-procedures-odbc"></a>ストアド プロシージャの呼び出し (ODBC)
  SQL ステートメントで ODBC CALL エスケープ句を使用してストアド プロシージャを呼び出すと、Microsoft® SQL Server™ ドライバーは、リモート ストアド プロシージャ コール (RPC) メカニズムを使用して、プロシージャを SQL Server に送信します。 RPC 要求は、SQL Server でのステートメント解析やパラメーター処理の多くを省略するため、Transact-SQL の EXECUTE ステートメントを使用するよりも高速です。  
  
 この機能を示すサンプル アプリケーションを参照してください。[プロセスのリターン コードと出力パラメーター &#40;ODBC&#41;](running-stored-procedures-process-return-codes-and-output-parameters.md)します。  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>プロシージャを RPC として実行するには  
  
1.  ODBC CALL エスケープ シーケンスを使用する SQL ステートメントを作成します。 このステートメントでは、各入力、入出力、出力パラメーター、およびプロシージャの戻り値 (存在する場合) に対してパラメーター マーカーを使用します。  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  呼び出す[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) 、それぞれの入力入出力、出力パラメーター、およびプロシージャの戻り値 (ある場合)。  
  
3.  使用してステートメントを実行[SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399)します。  
  
> [!NOTE]  
>  アプリケーションでプロシージャの送信に (ODBC CALL エスケープ シーケンスではなく) Transact-SQL の EXECUTE 構文を使用した場合、プロシージャ コールは、SQL Server ODBC ドライバーから SQL Server に、RPC ではなく SQL ステートメントとして渡されます。 また、Transact-SQL の EXECUTE ステートメントを使用した場合、出力パラメーターは返されません。  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャの操作方法に関するトピックを実行している&#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)   
 [ストアド プロシージャ呼び出しのバッチ化](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [ストアド プロシージャの実行](../native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [ストアド プロシージャを呼び出す](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [手順](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  
