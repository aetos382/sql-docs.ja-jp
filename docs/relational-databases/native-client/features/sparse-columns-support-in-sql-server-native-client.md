---
title: SQL Server Native Client におけるスパース列のサポート |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sparse columns, ODBC
- sparse columns, SQL Server Native Client
- sparse columns, OLE DB
ms.assetid: aee5ed81-7e23-42e4-92d3-2da7844d9bc3
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 089c35fd4fffaa2f531dc09b407f1800cc962b92
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39533142"
---
# <a name="sparse-columns-support-in-sql-server-native-client"></a>SQL Server Native Client におけるスパース列のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はスパース列をサポートしています。 スパース列の詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を参照してください[スパース列の使用](../../../relational-databases/tables/use-sparse-columns.md)と[列セットの使用](../../../relational-databases/tables/use-column-sets.md)します。  
  
 スパース列の詳細についてでサポート[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client を参照してください[スパース列をサポート&#40;ODBC&#41; ](../../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)と[スパース列をサポート&#40;OLE DB&#41; ](../../../relational-databases/native-client/ole-db/sparse-columns-support-ole-db.md).  
  
 この機能を説明するサンプル アプリケーションについては、「[SQL Server データ プログラミング サンプル](http://msftdpprodsamples.codeplex.com/)」を参照してください。  
  
## <a name="user-scenarios-for-sparse-columns-and-sql-server-native-client"></a>スパース列と SQL Server Native Client のユーザー シナリオ  
 スパース列を使用する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ユーザーの一般的なユーザー シナリオの概要を次の表に示します。  
  
|シナリオ|動作|  
|--------------|--------------|  
|**選択\*テーブルから**または iopenrowset::openrowset します。|スパース **column_set** のメンバーでないすべての列と、スパース **column_set** のメンバーであるすべての NULL 以外の列の値を含む XML 列が返されます。|  
|名前で列を参照する。|スパース列かどうか、**column_set** のメンバーであるかどうかに関係なく、列を参照できます。|  
|XML 計算列を通じて **column_set** メンバー列にアクセスする。|スパース **column_set** のメンバーである列に、名前で **column_set** を選択してアクセスし、**column_set** 列の XML を更新して値を挿入および更新できます。<br /><br /> 値は、**column_set** 列のスキーマに準拠している必要があります。|  
|SQLColumns を NULL または '%' (ODBC) の列検索パターンでのテーブルのすべての列のメタデータを取得します。または、DBSCHEMA_COLUMNS スキーマ行セット列の制限なし (OLE DB) を使用します。|**column_set** のメンバーでないすべての列について 1 つの行が返されます。 テーブルにスパース **column_set** がある場合は、そのスパースについて 1 つの行が返されます。<br /><br /> この場合、**column_set** のメンバーである列のメタデータは返されないことに注意してください。|  
|スパース列かどうか、**column_set** のメンバーかどうかに関係なく、すべての列のメタデータを取得する。 この場合、大量の行が返される可能性があります。|記述子フィールド SQL_SOPT_SS_NAME_SCOPE を SQL_SS_NAME_SCOPE_EXTENDED および呼び出しに設定[SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md) (ODBC)。<br /><br /> DBSCHEMA_COLUMNS_EXTENDED スキーマ行セット (OLE DB) の idbschemarowset::getrowset を呼び出します。<br /><br /> このシナリオは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より前のリリースの [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client を使用するアプリケーションでは使用できません。 ただし、このようなアプリケーションでは、システム ビューを直接クエリする可能性があります。|  
|**column_set** のメンバーである列についてのみメタデータを取得する。 この場合、大量の行が返される可能性があります。|記述子フィールド SQL_SOPT_SS_NAME_SCOPE を SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET に設定し、SQLColumns (ODBC) を呼び出します。<br /><br /> DBSCHEMA_SPARSE_COLUMN_SET スキーマ行セット (OLE DB) の idbschemarowset::getrowset を呼び出します。<br /><br /> このシナリオは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より前のリリースの [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client を使用するアプリケーションでは使用できません。 ただし、そのようなアプリケーションでは、システム ビューに対してクエリを実行できます。|  
|列がスパース列かどうかを確認する。|SQLColumns 結果セット (ODBC) の SS_IS_SPARSE 列を参照してください。<br /><br /> DBSCHEMA_COLUMNS スキーマ行セットの SS_IS_SPARSE 列を調べます (OLE DB)。<br /><br /> このシナリオは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より前のリリースの [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client を使用するアプリケーションでは使用できません。 ただし、そのようなアプリケーションでは、システム ビューに対してクエリを実行できます。|  
|列が判断を**column_set**します。|SQLColumns 結果セットの SS_IS_COLUMN_SET 列を参照してください。 または、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固有の列属性である SQL_CA_SS_IS_COLUMN_SET を調べます (ODBC)。<br /><br /> DBSCHEMA_COLUMNS スキーマ行セットの SS_IS_COLUMN_SET 列を調べます。 または、 *dwFlags* icolumnsinfo::getcolumninfo または DBCOLUMNFLAGS icolumnsrowset::getcolumnsrowset によって返される行セットで返されます。 **Column_set**列、DBCOLUMNFLAGS_SS_ISCOLUMNSET が設定されます (OLE DB)。<br /><br /> このシナリオは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より前のリリースの [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client を使用するアプリケーションでは使用できません。 ただし、そのようなアプリケーションでは、システム ビューに対してクエリを実行できます。|  
|**column_set** を含まないテーブルに対して BCP でスパース列をインポートおよびエクスポートする。|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の以前のバージョンから動作は変更されていません。|  
|**column_set** を含むテーブルに対して BCP でスパース列をインポートおよびエクスポートする。|**Column_set**がインポートされ、XML と同じ方法でエクスポートは、として**varbinary (max)** 場合またはとしてバイナリの型としてバインドされている**nvarchar (max)** 場合として、バインド**char**または**wchar**型。<br /><br /> スパース **column_set** のメンバーである列は個別の列としてはエクスポートされず、**column_set** の値でのみエクスポートされます。|  
|**queryout** BCP の動作。|明示的に指定された列の処理は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の以前のバージョンから変更されていません。<br /><br /> スキーマが異なる列の間のインポートおよびエクスポートを含むシナリオでは、特別な処理が必要になる場合があります。<br /><br /> BCP の詳細については、後の「一括コピー (BCP) によるスパース列のサポート」を参照してください。|  
  
## <a name="down-level-client-behavior"></a>下位クライアントの動作  
 下位クライアントでは、SQLColumns および DBSCHMA_COLUMNS でメタデータが返されるのは、スパース **column_set** のメンバーでない列のみです。 導入された追加の OLE DB スキーマ行セット[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]Native Client を使用可能にすることはできませんも SQL_SOPT_SS_NAME_SCOPE を使用して ODBC の SQLColumns に変更されます。  
  
 下位クライアントでは、スパース **column_set** のメンバーである列に名前でアクセスできます。[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] クライアントでは、XML 列として **column_set** 列にアクセスできます。  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>一括コピー (BCP) によるスパース列のサポート  
 スパース列の ODBC または OLE DB の BCP API への変更がないまたは**column_set**機能します。  
  
 テーブルに **column_set** がある場合、スパース列は個別の列として処理されません。 値のすべてのスパース列の値が含まれている、 **column_set**、これは、XML 列と同じ方法でエクスポートは、として**varbinary (max)** 場合またはとしてバイナリの型としてバインド**nvarchar (max)** 場合としてバインド、 **char**または**wchar**型)。 インポート時に、 **column_set**値は、のスキーマに準拠する必要があります、 **column_set**します。  
  
 **queryout** の操作については、明示的に参照されている列の処理方法は変更されていません。 **column_set** 列の動作は XML 列と同じで、名前で参照されているスパース列の処理には、列がスパース列であることの影響はありません。  
  
 ただし、**queryout** をエクスポートに使用する場合に、スパース列セットのメンバーであるスパース列を名前で参照すると、同じ構造のテーブルへの直接インポートができなくなります。 これは、BCP では **select \*** 操作と一貫したメタデータがインポートのために使用され、そのメタデータを **column_set** メンバー列と対応させることはできないからです。 **column_set** メンバー列を個別にインポートするには、目的の **column_set** 列を参照するテーブルのビューを定義して、そのビューを使用してインポート操作を行う必要があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client プログラミング](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
