---
title: ResumeService メソッド (SqlService クラス) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ResumeService Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ResumeService method
ms.assetid: 0b0a5f08-b95e-4626-bf81-309da7a0aacd
caps.latest.revision: 34
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 49d3185f45e7c324581c15183bc5016297137c81
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="resumeservice-method-sqlservice-class"></a>ResumeService メソッド (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  サービスを再開状態にする動作を試行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.ResumeService()  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 Uint32 値は 0 の場合、 **ResumeService**要求が承認された要求はサポートされていない場合は 1、エラーを示すその他の任意の数。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [開始して、サービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
