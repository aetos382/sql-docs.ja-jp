---
title: トレース (SQL Server Profiler) を一時停止 |Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: profiler
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- pausing traces
- temporarily stopping traces
- traces [SQL Server], pausing
- stopping traces
ms.assetid: 432b9b0c-b5e7-47f3-a71b-310fb3bf2445
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c58d67783fa415936c74c26167517ca7b1933788
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38031550"
---
# <a name="pause-a-trace-sql-server-profiler"></a>トレースの一時停止 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  トレースを一時停止すると、トレースを再開するまで、それ以上のイベント データはキャプチャされません。  
  
 トレースを一時停止すると、トレースを再開するまで、それ以上のイベント データはキャプチャされません。 トレースを再開すると、トレース操作が再開されます。 キャプチャを再開しても、それ以前にキャプチャしたデータが失われることはありません。 トレースを再開すると、その時点から、データのキャプチャが再開されます。 トレースを一時停止している間は、名前、イベント、列、およびフィルターを変更することができます。 ただし、トレース データの送信先またはサーバー接続は変更できません。  
  
### <a name="to-pause-a-trace"></a>トレースを一時停止するには  
  
1.  実行中のトレースを含んでいるウィンドウを選択します。  
  
2.  **[ファイル]** メニューの **[トレースの一時停止]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
