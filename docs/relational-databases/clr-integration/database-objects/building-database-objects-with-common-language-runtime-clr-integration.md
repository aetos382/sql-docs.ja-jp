---
title: "共通言語ランタイム (CLR) 統合によるデータベース オブジェクトの構築 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- database objects [CLR integration], building
- common language runtime [SQL Server], building database objects
- managed code [SQL Server], database objects
- building database objects [CLR integration]
- .NET Framework routines [SQL Server]
ms.assetid: ce34132c-bfa3-447b-9131-b6e17c672efe
caps.latest.revision: "48"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 51fd445775e428d259a53176e3aaafdb2d1e47a6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="building-database-objects-with-common-language-runtime-clr-integration"></a>共通言語ランタイム (CLR) 統合を使用したデータベース オブジェクトの構築
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]使用してデータベース オブジェクトを構築することができます、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET Framework 共通言語ランタイム (CLR) と統合します。 マネージ コード内の実行を[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 「CLR ルーチン」と呼びます CLR ルーチンには、次のものがあります。  
  
-   スカラー UDF (ユーザー定義スカラー値関数)  
  
-   ユーザー定義 TVF (テーブル値関数)  
  
-   UDP (ユーザー定義プロシージャ)  
  
-   ユーザー定義トリガー  
  
 CLR ルーチンは、マネージ コード内ではそれぞれ同じ構造になります。 CLR ルーチンは、クラスの public static ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET では shared) メソッドにマップされます。 ルーチン以外に、.NET Framework を使用して UDT (ユーザー定義型) やユーザー定義集計関数を定義することもできます。 UDT とユーザー定義集計は、.NET Framework クラス全体にマップされます。  
  
 各種類の .NET Framework ルーチンには [!INCLUDE[tsql](../../../includes/tsql-md.md)] 宣言があり、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で同等の [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用できる任意の場所で使用できます。 たとえば、スカラー UDF は任意のスカラー式で使用できます。 また、TVF は任意の FROM 句で使用できます。 プロシージャは、EXEC ステートメントやクライアント アプリケーションから呼び出すことができます。  
  
> [!NOTE]  
>  効果的であるとクエリ オプティマイザーで判断された場合は、共通言語ランタイムでの CLR オブジェクト (ユーザー定義関数、ユーザー定義型、またはトリガー) の実行を複数のスレッドで行うことができます (並列プラン)。 ただし、ユーザー定義関数がデータにアクセスする場合は、直列プランで実行されます。 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] よりも前のサーバー バージョンで実行したときに、ユーザー定義関数に LOB パラメーターが含まれていたり、ユーザー定義関数から値が返される場合も、直列プランで実行する必要があります。  
  
 次の表は、このセクションで説明されているトピックを一覧表示します。  
  
 [CLR 統合の概要](../../../relational-databases/clr-integration/database-objects/getting-started-with-clr-integration.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と CLR との統合を使用したオブジェクトのコンパイルに必要なライブラリと名前空間の概要について説明します。 また、例として "Hello World" CLR ストアド プロシージャを紹介します。  
  
 [サポートされている .NET Framework ライブラリ](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)  
 CLR 統合でサポートされる .NET Framework ライブラリに関する情報を提供します。  
  
 [CLR 統合プログラミング モデルの制限事項](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)  
 CLR 統合プログラミング モデルの制限事項に関する情報を提供します。  
  
 [.NET Framework での SQL Server データ型](../../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型と、.NET Framework での同等のデータ型の概要について説明します。  
  
 [CLR 統合のカスタム属性の概要](http://msdn.microsoft.com/library/ecf5c097-0972-48e2-a9c0-b695b7dd2820)  
 CLR 統合のカスタム属性に関する情報を提供します。  
  
 [CLR ユーザー定義関数](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)  
 テーブル値関数、スカラー関数、ユーザー定義集計関数など、さまざまな種類の CLR 関数の実装方法と使用方法について説明します。  
  
 [CLR ユーザー定義型](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 CLR ユーザー定義型の実装方法と使用方法について説明します。  
  
 [CLR ストアド プロシージャ](http://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)  
 CLR ストアド プロシージャの実装方法と使用方法について説明します。  
  
 [CLR トリガー](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)  
 CLR トリガーの実装方法と使用方法について説明します。  
  
## <a name="see-also"></a>参照  
 [共通言語ランタイム &#40;です。CLR &#41;統合の概要](../../../relational-databases/clr-integration/common-language-runtime-integration-overview.md)  
  
  