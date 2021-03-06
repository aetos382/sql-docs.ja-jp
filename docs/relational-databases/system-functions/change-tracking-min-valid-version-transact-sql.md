---
title: CHANGE_TRACKING_MIN_VALID_VERSION (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CHANGE_TRACKING_CLEANUP_VERSION
- CHANGE_TRACKING_CLEANUP_VERSION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CHANGE_TRACKING_MIN_VALID_VERSION
- change tracking [SQL Server], CHANGE_TRACKING_MIN_VALID_VERSION
ms.assetid: 5a43d23f-adcf-4c0b-95ad-07cee03c1f9d
caps.latest.revision: 16
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: d9a53856fc95d8564c6b08f4867bba0f8a9604b5
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39535512"
---
# <a name="changetrackingminvalidversion-transact-sql"></a>CHANGE_TRACKING_MIN_VALID_VERSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  変更の追跡を使用する場合の指定したテーブルから情報を取得するに使用するために有効なクライアントの最小バージョンを返します、 [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md)関数。  
    
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CHANGE_TRACKING_MIN_VALID_VERSION ( table_object_id )  
```  
  
## <a name="arguments"></a>引数  
 *table_object_id*  
 テーブルのオブジェクト ID です。 *table_object_id*は、 **int**します。  
  
## <a name="return-type"></a>戻り値の型  
 **bigint**  
  
## <a name="remarks"></a>コメント  
 この関数の値の検証を使用して、 *last_sync_version* CHANGETABLE のパラメーター。 場合*last_sync_version*が CHANGETABLE を後の呼び出しから返される結果を有効にすることはできない、この関数によって報告される値より小さい。  
  
 CHANGE_TRACKING_MIN_VALID_VERSION は、次の情報を使用して戻り値を判断します。  
  
-   テーブルで変更の追跡を有効にした日時。  
  
-   バックグラウンド クリーンアップ タスクを実行して、データベースに対して指定した保持期間より古い変更追跡情報を削除した日時。  
  
-   テーブルが切り捨てられたかどうか。 これにより、テーブルに関連付けられている変更追跡情報がすべて削除されます。  
  
 次のいずれかの条件に該当する場合、この関数は NULL を返します。  
  
-   データベースで変更の追跡が有効になっていない。  
  
-   指定されたテーブル オブジェクト ID が現在のデータベースで有効でない。  
  
-   オブジェクト ID で指定されたテーブルに対する十分な権限がない。  
  
## <a name="examples"></a>使用例  
 次の例では、指定されたバージョンが有効なバージョンかどうかを判断します。 例では、有効な最小のバージョンの取得、`dbo.Employees`テーブル、および次の値を比較し、`@last_sync_version`変数。 `@last_sync_version` の値が `@min_valid_version` の値より小さい場合、変更された行の一覧は有効ではありません。  
  
> [!NOTE]  
>  通常は、データの同期に使用した最新のバージョン番号が格納されているテーブルまたはその他の場所から値を取得します。  
  
```  
-- The tracked change is tagged with the specified context   
DECLARE @min_valid_version bigint, @last_sync_version bigint;  
  
SET @min_valid_version =   
CHANGE_TRACKING_MIN_VALID_VERSION(OBJECT_ID('dbo.Employees'));  
  
SET @last_sync_version = 11  
IF (@last_sync_version < @min_valid_version)  
-- Error � do not obtain changes  
ELSE  
-- Obtain changes using CHANGETABLE(CHANGES ...)  
```  
  
## <a name="see-also"></a>参照  
 [変更追跡関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [sys.change_tracking_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables.md)  
  
  
