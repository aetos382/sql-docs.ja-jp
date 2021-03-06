---
title: MDX (MDX) でのセル計算の構築 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- calculated cells [MDX]
- queries [MDX], cell calculations
- cells [MDX]
- MDX [Analysis Services], calculations
- calculation subcubes [MDX]
- calculated values [MDX]
- Multidimensional Expressions [Analysis Services], cell calculations
ms.assetid: 068aea63-d419-4791-a960-3d74e76f808e
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9b0a689858d4012f360e7f3893cfa844f3ecbdcf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161353"
---
# <a name="building-cell-calculations-in-mdx-mdx"></a>MDX でのセル計算の作成 (MDX)
  多次元式 (MDX) では、計算されるメンバー、カスタム ロールアップ、およびカスタム メンバーなど、計算値を生成するための多数のツールを使用できます。 しかし、これらの機能を使用して特定のセル セットや、さらには単一セルに影響を与えるのは困難です。  
  
 セルに対して個別に計算値を生成するには、MDX の計算されるセル機能を使用する必要があります。 計算されるセルを使用すると、 *計算サブキューブ*と呼ばれる特定のセル スライスを定義し、計算サブキューブ内のすべてのセルに個別に式を適用できます。  
  
 計算されるセルでは、KPI で使用されるゴールシーク数式や推測分析の式などの複雑な機能を使用できます。 このレベルの機能は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のパス順序機能を利用しています。そのため、パス順序のうち特定のパスに計算式を適用し、計算されるセルに再帰的なパスを行うことができます。 パス順序の詳細については、「[パス順序と解決順序の概要 (MDX)](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)」を参照してください。  
  
 計算されるセルは、作成の有効範囲の点で、名前付きセットと計算されるメンバーの両方に似ています。計算されるセルは、セッションまたは 1 回のクエリの有効期限に合わせて一時的に作成することも、キューブの一部としてグローバルに使用可能にすることもできます。  
  
-   **クエリ スコープ** MDX クエリの一部として定義する、計算されるセルを作成する場合 (つまり、スコープをそのクエリに限定する場合) は、WITH キーワードを使用します。 その計算されるセルは、MDX の SELECT ステートメントの中で使用できます。 このアプローチを使用して、計算されるセルを使用して作成、`WITH`キーワードは、SELECT ステートメントの影響を及ぼすことがなく変更できます。  
  
     WITH キーワードを使用して計算されるメンバーを作成する方法の詳細については、「[クエリ スコープのセル計算の作成 (MDX)](../../multidimensional-models-olap-logical-cube-objects/calculations.md)」を参照してください。  
  
-   **セッション スコープ** クエリのコンテキストよりも広いスコープを設定して計算されるセルを作成する場合 (つまり、スコープを MDX セッションの有効期間全体とする場合) は、CREATE CELL CALCULATION または ALTER CUBE ステートメントのいずれかを使用します。  
  
     CREATE CELL CALCULATION または ALTER CUBE ステートメントを使用してセッションでの計算されるセルを作成する方法の詳細については、「 [セッション スコープの計算されるセルの作成](mdx-cell-calculations-session-scoped-calculated-cells.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ALTER CUBE ステートメント&#40;MDX&#41;](/sql/mdx/mdx-data-definition-alter-cube)   
 [CREATE CELL CALCULATION ステートメント&#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-cell-calculation)   
 [クエリ スコープのセル計算の作成&#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md)   
 [MDX クエリの基礎&#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
