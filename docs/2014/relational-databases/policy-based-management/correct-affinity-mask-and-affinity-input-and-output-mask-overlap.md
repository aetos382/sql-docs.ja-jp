---
title: Mask の重複の正しい Affinity Mask と Affinity 入出力 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 14dbd2e0f3815e500d5742822f7ca8157408c917
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37324202"
---
# <a name="correct-affinity-mask-and-affinity-input-output-mask-overlap"></a>正しい Affinity Mask オプションと関係マスクの重複の入出力
  このルールでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに、affinity mask オプションと affinity I/O mask オプションの両方が割り当てられたプロセッサが 1 つ以上あるかどうかを確認します。 複数のプロセッサが搭載されたコンピューターでは、affinity mask オプションと affinity I/O mask オプションを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用される CPU を指定します。 affinity mask と affinity I/O mask の両方で CPU を有効にすると、プロセッサが過剰に使用されるため、パフォーマンスが低下する可能性があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 affinity mask オプションと affinity I/O mask オプションのいずれかを指定している場合は、両方を指定する必要がありますが、有効にするのは一度に 1 つの CPU だけにしてください。  
  
 affinity mask オプションと affinity I/O mask オプションの両方で同じ CPU を有効にしないようにしてください。 各 CPU に対応するビットは、次のいずれかの状態に設定します。  
  
-   affinity mask オプションと affinity I/O mask オプションの両方で 0  
  
-   affinity mask オプションでは 0、affinity I/O mask オプションでは 1  
  
-   affinity mask オプションでは 1、affinity I/O mask オプションでは 0  
  
## <a name="for-more-information"></a>詳細情報  
 [affinity mask サーバー構成オプション](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)  
  
 [affinity Input-Output mask サーバー構成オプション](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)  
  
 [affinity64 mask サーバー構成オプション](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md)  
  
 [affinity64 Input-Output mask サーバー構成オプション](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
