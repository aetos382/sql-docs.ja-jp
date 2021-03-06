---
title: ITableDefinition でのデータ型マッピング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- SQL Server Native Client OLE DB provider, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
ms.assetid: 13292d1f-c17e-4d11-bf98-3460a10cbb18
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2ff2a43c9ff48322e3b93e01899942a692f52a39
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412271"
---
# <a name="data-type-mapping-in-itabledefinition"></a>ITableDefinition でのデータ型のマッピング
  使用してテーブルを作成するときに、 **itabledefinition::createtable**関数の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーが指定できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型、 *pwszTypeName*渡される DBCOLUMNDESC 配列のメンバーです。 OLE DB データ型で表されるマッピングのコンシューマーは、名前で列のデータ型を指定する場合、 *wType* DBCOLUMNDESC 構造体のメンバーは無視されます。  
  
 DBCOLUMNDESC 構造体を使用して OLE DB データ型を持つ新しい列のデータ型を指定するときに*wType* 、メンバー、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが OLE DB データ型を次のようにマップされます。  
  
|OLE DB データ型|SQL Server<br /><br /> データ型 (data type)|関連情報|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**バイナリ**、 **varbinary**、**イメージ、** または**varbinary (max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、 *ulColumnSize* DBCOLUMNDESC 構造体のメンバー。 値、およびのバージョンに基づいて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーにマップする型**イメージ**します。<br /><br /> 場合の値*ulColumnSize*の最大長よりも小さい、**バイナリ**データ型の列、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、DBCOLUMNDESC *rgPropertySets*メンバー。 DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーにマップする型**バイナリ**します。 プロパティの値が VARIANT_FALSE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーにマップする型**varbinary**します。 いずれの場合も、DBCOLUMNDESC *ulColumnSize*メンバーが作成された SQL Server の列の幅を決定します。|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**numeric**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの検査、DBCOLUMDESC *bPrecision*と*bScale*メンバーには、有効桁数を決定し、拡張、**数値**列です。|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**、 **varchar**、**テキスト、** または**varchar (max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、 *ulColumnSize* DBCOLUMNDESC 構造体のメンバー。 値とのバージョンに基づいて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーにマップする型**テキスト**します。<br /><br /> 場合の値*ulColumnSize*マルチバイト文字データ型の列の最大長よりも小さい、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、DBCOLUMNDESC *rgPropertySets*メンバー。 DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーにマップする型**char**します。 プロパティの値が VARIANT_FALSE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーにマップする型**varchar**します。 いずれの場合も、DBCOLUMNDESC *ulColumnSize*メンバーの幅を決定する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列を作成します。|  
|DBTYPE_UDT|**UDT**|次の情報が使用される`DBCOLUMNDESC`構造体**itabledefinition::createtable** UDT 列が必要な場合。<br /><br /> -   *pwSzTypeName*は無視されます。<br />-   *rgPropertySets*含める必要があります、`DBPROPSET_SQLSERVERCOLUMN`プロパティに関するセクションで説明したように設定`DBPROPSET_SQLSERVERCOLUMN`の[ユーザー種類](../native-client/features/using-user-defined-types.md)します。|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**、 **nvarchar**、 **ntext、** または**nvarchar (max)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、 *ulColumnSize* DBCOLUMNDESC 構造体のメンバー。 値に基づいて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーにマップする型**ntext**します。<br /><br /> 場合の値*ulColumnSize* Unicode 文字データ型列の最大長よりも小さい、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、DBCOLUMNDESC *rgPropertySets*メンバー。 DBPROP_COL_FIXEDLENGTH が VARIANT_TRUE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーにマップする型**nchar**します。 プロパティの値が VARIANT_FALSE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーにマップする型**nvarchar**します。 いずれの場合も、DBCOLUMNDESC *ulColumnSize*メンバーの幅を決定する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列を作成します。|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  新しいテーブルの作成時には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって上記の表に示した OLE DB データ型の列挙値のみがマップされます。 それ以外の OLE DB データ型の列が含まれたテーブルを作成すると、エラーが発生します。  
  
## <a name="see-also"></a>参照  
 [データ型&#40;OLE DB&#41;](data-types-ole-db.md)  
  
  
