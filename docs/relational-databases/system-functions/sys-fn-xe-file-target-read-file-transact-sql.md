---
title: sys.fn_xe_file_target_read_file (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_xe_file_target_read_file_TSQL
- fn_xe_file_target_read_file
- sys.fn_xe_file_target_read_file_TSQL
- sys.fn_xe_file_target_read_file
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], functions
- fn_xe_file_target_read_file function
- sys.fn_xe_file_target_read_file function
ms.assetid: cc0351ae-4882-4b67-b0d8-bd235d20c901
caps.latest.revision: 20
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 9d21a49c24dd33ffebd00eae8e33ed9e4601706c
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39535712"
---
# <a name="sysfnxefiletargetreadfile-transact-sql"></a>sys.fn_xe_file_target_read_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  拡張イベント非同期ファイル ターゲットによって作成されるファイルを読み取ります。 行ごとに、XML 形式の 1 つのイベントが返されます。  
  
> [!WARNING]  
>  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] XEL および XEM 形式で生成されたトレース結果をそのまま使用します。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] トレース結果を XEL 形式でのイベントのみをサポートを拡張します。 SQL Server Management Studio を使用して、トレース結果を XEL 形式で読み取ることをお勧めします。    
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_xe_file_target_read_file ( path, mdpath, initial_file_name, initial_offset )  
```  
  
## <a name="arguments"></a>引数  
 *path*  
 読み取るファイルのパスです。 *パス*ワイルドカードを含めることができ、ファイルの名前が含まれます。 *パス*は**nvarchar (260)** します。 既定値はありません。 Azure SQL Database のコンテキストでは、この値は、Azure Storage 内のファイルへの HTTP URL が。
  
 *mdpath*  
 ファイルまたはで指定されたファイルに対応するメタデータ ファイルへのパス、*パス*引数。 *mdpath*は**nvarchar (260)** します。 既定値はありません。 SQL Server 2016 以降、このパラメーターは、null として指定することができます。
  
> [!NOTE]  
>  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 必要ありません、 *mdpath*パラメーター。 ただし、以前のバージョンの SQL Server で生成されたログ ファイルに対する下位互換性のために残されています。  
  
 *initial_file_name*  
 最初のファイルから読み取る*パス*します。 *initial_file_name*は**nvarchar (260)** します。 既定値はありません。 場合**null**で見つかったすべてのファイル引数として指定する*パス*は読み取り専用です。  
  
> [!NOTE]  
>  *initial_file_name*と*initial_offset*はペアの引数。 いずれかの引数の値を指定した場合は、もう一方の引数の値も指定する必要があります。  
  
 *initial_offset*  
 以前に読み取られた最後のオフセットを指定します。そのオフセットまでのすべてのイベントがスキップされます。 イベントの列挙は、指定したオフセットより後のイベントから開始されます。 *initial_offset*は**bigint**します。 場合**null**引数ファイル全体が読み取られるように指定します。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|module_guid|**uniqueidentifier**|イベント モジュールの GUID です。 NULL 値は許可されません。|  
|package_guid|**uniqueidentifier**|イベント パッケージの GUID です。 NULL 値は許可されません。|  
|object_name|**nvarchar (256)**|イベントの名前です。 NULL 値は許可されません。|  
|event_data|**nvarchar(max)**|XML 形式のイベント コンテンツです。 NULL 値は許可されません。|  
|file_name|**nvarchar(260)**|イベントを含むファイルの名前です。 NULL 値は許可されません。|  
|file_offset|**bigint**|イベントを含むファイル内のブロックのオフセットです。 NULL 値は許可されません。|  
|timestamp_utc|**datetime2**|**適用対象**: [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。<br /><br />日付とイベントの時刻 (UTC タイム ゾーン)。 NULL 値は許可されません。|  

  
## <a name="remarks"></a>コメント  
 大きな結果を読み取り、実行することによって設定**sys.fn_xe_file_target_read_file**で[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]エラーが発生する可能性があります。 使用して、**結果をファイルに**モード (**Ctrl + Shift + F**) ファイルに大きな結果セットをエクスポートし、代わりに別のツールでファイルを読み取る。  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-retrieving-data-from-file-targets"></a>A. ファイル ターゲットからデータを取得する  
 すべてのファイルからすべての行を取得する例を次に示します。 この例では、ファイル ターゲットとメタファイルが C:\ drive のトレース フォルダーにあります。  
  
```  
SELECT * FROM sys.fn_xe_file_target_read_file('C:\traces\*.xel', 'C:\traces\metafile.xem', null, null);  
```  
  
## <a name="see-also"></a>参照  
 [拡張イベントの動的管理ビュー](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)   
 [Extended Events Catalog Views &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
  
