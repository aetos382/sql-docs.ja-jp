---
title: SQLSetConnectOption (Access ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLSetConnectOption
- SQLSetConnectOption function [ODBC], Access Driver
ms.assetid: 58399bc4-d0b1-4eaa-a474-c92b2d5855ea
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 952bfe683dabbcedeb771c0e7f1787f7a0e6f7bb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32905017"
---
# <a name="sqlsetconnectoption-access-driver"></a>SQLSetConnectOption (Access ドライバー)
> [!NOTE]  
>  このトピックでは、アクセス ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
|fOption|解説|  
|-------------|-------------|  
|SQL_ACCESS_MODE|SQL_ACCESS_MODE fOption は、SQL_MODE_READ_ONLY または SQL_MODE_READ_WRITE のいずれかに設定することができます。 ただし、SQL_ACCESS_MODE が SQL_MODE_READ_ONLY に設定されている場合、ドライバーは更新を禁止できません。|  
|SQL_AUTOCOMMIT|Microsoft Access ドライバーを使用すると場合、は、Microsoft Access ドライバーには、トランザクション [1] がサポートされているために、sql_autocommit_on の状態または SQL_AUTOCOMMIT_OFF のいずれかに SQL_AUTOCOMMIT オプションを設定することがあります。|  
|SQL_CURRENT_QUALIFIER|サポートされています。|  
|SQL_LOGIN_TIMEOUT|サポートされていません。|  
|SQL_OPT_TRACE|サポートされています。|  
|SQL_OPT_TRACEFILE|サポートされています。|  
|SQL_PACKET_SIZE|サポートされていません。|  
|SQL_QUIET_MODE|サポートされていません。|  
|SQL_TRANSLATE_DLL|サポートされていません。|  
|SQL_TRANSLATION_OPTION|サポートされていません。|  
|SQL_TXN_ISOLATION|SQL_TXN_ISOLATION は SQL_TXN_READ_COMMITTED では常にします。|  
  
 [Microsoft Access ドライバーでは、1] は、アトミック トランザクションはサポートされていません。 値が書き込まれる時間と、トランザクションはコミット時間の間、有限の遅延が存在する Microsoft Access ドライバーを使用してトランザクションをコミットするときにディスクにします。 この遅延は、Microsoft Jet エンジンに特有の遅延によって決定されます。 ページのタイムアウトはできません、最小値よりも小さい PageTimeout オプションを設定したその値を下回る場合でもです。 その結果、あるデータをコミットするという保証はありません、安定した遅延の間に変更を行うためです。
