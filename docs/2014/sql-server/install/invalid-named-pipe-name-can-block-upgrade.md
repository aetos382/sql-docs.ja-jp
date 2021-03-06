---
title: 無効な名前付きパイプ名によってアップグレードがブロック |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- invalid named pipes [SQL Server]
- named pipes
ms.assetid: 58c2199c-4fdf-4d43-ac1c-842703344b75
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d5a0b27ab1362a15730692b7bc41849ba4724bfd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297782"
---
# <a name="invalid-named-pipe-name-can-block-upgrade"></a>無効な名前付きパイプ名によってアップグレードがブロックされる
  アップグレードは、名前付きパイプのプロトコルの構成が正しくない場合は失敗します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 アップグレード中に、セットアップ プログラムの起動、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]インスタンス共有メモリ サポートと、ローカル接続のみを受け入れる名前付きパイプします。 文字列で始まる必要がありますが、サーバーで指定したパイプ名が空白でない場合は、"\\\\. \pipe\\"を有効にします。 パイプ名が有効でない場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]が起動せず、セットアップは失敗します。  
  
## <a name="corrective-action"></a>修正措置  
 使用して、  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネットワーク ユーティリティ**有効なパイプ名を指定し、セットアップを実行します。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
