---
title: メタデータを使用する方法ですか。 | Microsoft Docs
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
- result sets [ODBC], metadata
- metadata [ODBC]
ms.assetid: 70fb976c-9342-4edd-b066-1140696fd0fa
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c4779c5e60b97a389ebf686678c9a989fb933cb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910797"
---
# <a name="how-is-metadata-used"></a>メタデータを使用する方法ですか。
アプリケーションは、ほとんどの結果セット操作にメタデータを必要とします。 たとえば、列のデータ型を使用して、列にバインドされている変数の種類を判断します。 その列のデータを表示するのに必要がある領域の量を決定するのに、文字型の列のバイト長を使用します。 アプリケーションが列のメタデータを判断する方法は、アプリケーションの種類によって異なります。  
  
 垂直方向のアプリケーションでは、定義済みのテーブルを操作して、それらのテーブルで定義済みの操作を実行します。 アプリケーションが作成して、アプリケーションの開発者によって制御される前にこのようなアプリケーションの結果セットのメタデータが定義されているため、アプリケーションにハードコーディングできます。 たとえば、データ ソース内で受注 ID 列が 4 バイト integer 型で定義されている場合、アプリケーションは常に 4 バイト integer をこの列にバインドできます。 メタデータがアプリケーション内でハードコーディングされている場合、アプリケーションが使用するテーブルへの変更は、通常、アプリケーション コードに対する変更になります。 これは、このような変更は通常、アプリケーションの新しいリリースの一環として行われるため、問題ではことはほとんどありません。  
  
 垂直方向のアプリケーションと同様にカスタム アプリケーションは一般に定義済みのテーブルを操作して、それらのテーブルで定義済みの操作を実行します。 たとえば、アプリケーションは; 次の 3 つの異なるデータ ソース間でデータを転送する書き込む可能性があります。データを転送するには、アプリケーションに書き込まれると通常呼ばれます。 したがって、カスタム アプリケーションでは、ハード コーディングされたメタデータが存在する傾向がもできます。  
  
 汎用アプリケーション、特にアドホック クエリをサポートして、作成する結果セットのメタデータを知ることはほぼありません。 関数を使用して実行時にメタデータを検出する必要がありますので、 **SQLNumResultCols**、 **SQLDescribeCol**、および**SQLColAttribute**で説明される、次のセクション「 [SQLDescribeCol と SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)です。  
  
 その種類に関係なく、すべてのアプリケーションでは、カタログ関数によって返される結果セットのメタデータをハード コーディングことができます。 これらの結果セットは、このマニュアルのリファレンスのセクションで定義されます。
