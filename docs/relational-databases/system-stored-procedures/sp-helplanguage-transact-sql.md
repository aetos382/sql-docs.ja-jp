---
title: sp_helplanguage (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helplanguage
- sp_helplanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplanguage
- default languages
ms.assetid: 8c4651a5-7dbc-49c5-8691-dc72103c2dfa
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 29f366517986620444e018a5348e623aa541b00a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39560632"
---
# <a name="sphelplanguage-transact-sql"></a>sp_helplanguage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] での特定の代替言語、またはすべての言語に関する情報を報告します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helplanguage [ [ @language = ] 'language' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@language=** ] **'***言語***'**  
 情報を表示する代替言語の名前です。 *言語*は**sysname**、既定値は NULL です。 場合*言語*が指定すると、指定した言語に関する情報が返されます。 言語が指定されていない場合は、すべての言語については、 **sys.syslanguages**互換性ビューが返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**langid**|**smallint**|言語 ID 番号です。|  
|**dateformat**|**nchar(3)**|日付の形式です。|  
|**datefirst**|**tinyint**|週の最初の曜日。1 は月曜、2 は火曜のようになり、7 は日曜になります。|  
|**アップグレード**|**int**|この言語を使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の最新アップグレード バージョンです。|  
|**name**|**sysname**|言語名です。|  
|**alias**|**sysname**|言語の別名です。|  
|**か月間**|**nvarchar(372)**|月の名前です。|  
|**shortmonths**|**nvarchar(132)**|月の短縮名です。|  
|**days**|**nvarchar(217)**|曜日です。|  
|**lcid**|**int**|この言語を使用する Windows のロケール ID です。|  
|**msglangid**|**smallint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メッセージ グループ id。|  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-information-about-a-single-language"></a>A. 特定の言語に関する情報を返す  
 次の例では、代替言語に関する情報を表示する`French`します。  
  
```  
sp_helplanguage French;  
```  
  
### <a name="b-returning-information-about-all-languages"></a>B. すべての言語に関する情報を返す  
 次の例では、インストールされているすべての代替言語に関する情報を表示します。  
  
```  
sp_helplanguage;  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [@@LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/functions/language-transact-sql.md)   
 [言語を設定する (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-language-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
