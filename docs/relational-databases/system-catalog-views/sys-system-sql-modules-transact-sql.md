---
title: sys.system_sql_modules (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- system_sql_modules_TSQL
- sys.system_sql_modules
- sys.system_sql_modules_TSQL
- system_sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_sql_modules catalog view
ms.assetid: ad3548bc-4780-4821-b962-b421d52daed9
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 6f566fa663aecbb0a1ab7e82396a5560f8ecb48b
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39543382"
---
# <a name="syssystemsqlmodules-transact-sql"></a>sys.system_sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  SQL 言語定義モジュールを含むシステム オブジェクトごとに 1 行のデータを返します。 FN、IF、P、PC、TF、V 型のシステム オブジェクトには、SQL モジュールが関連付けられています。 親オブジェクトを識別するにはこのビューに参加できる[sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md)します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|モジュールを含むオブジェクトのオブジェクト識別番号。データベース内で一意です。|  
|**definition**|**nvarchar(max)**|このモジュールを定義する SQL テキスト。|  
|**uses_ansi_nulls**|**bit**|1 = モジュールは、SET ANSI_NULLS データベース オプションが ON の状態で作成されました。<br /><br /> 常に 1 を返します。|  
|**uses_quoted_identifier**|**bit**|1 = モジュールは、SET QUOTED_IDENTIFIER ON の状態で作成されました。<br /><br /> 常に 1 を返します。|  
|**is_schema_bound**|**bit**|0 = モジュールは、SCHEMABINDING オプションで作成されませんでした。<br /><br /> 常に 0 を返します。|  
|**uses_database_collation**|**bit**|0 = モジュールは、データベースの既定の照合順序に依存していません。<br /><br /> 常に 0 を返します。|  
|**is_recompiled**|**bit**|0 = プロシージャは、WITH RECOMPILE オプションを使って作成されませんでした。<br /><br /> 常に 0 を返します。|  
|**null_on_null_input**|**bit**|0 = モジュールは、NULL 入力に対して NULL 出力を生成するように作成されませんでした。<br /><br /> 常に 0 を返します。|  
|**execute_as_principal_id**|**int**|常に NULL を返します|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.all_sql_modules &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-sql-modules-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
