---
title: Constants (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- uniqueidentifier data type
- bit data type
- constants [SQL Server]
- scalar values
- money data type, constants
- binary [SQL Server], constants
- float data type
- Unicode [SQL Server], constants
- constants [Transact-SQL]
- integer constants
- decimal data type, constants
- character strings [SQL Server], constants
- positive values [SQL Server]
- formats [SQL Server], constants
- datetime data type [SQL Server]
- literals [SQL Server], constants
- real data type
- negative values
ms.assetid: 58ae3ff3-b1d5-41b2-9a2f-fc7ab8c83e0e
caps.latest.revision: 22
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 87935f96118294310c2aa4baedcaa2f962935d3a
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39459676"
---
# <a name="constants-transact-sql"></a>定数 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

リテラル値またはスカラー値としても知られる定数は、特定のデータ値を表す記号です。 定数の形式は、その定数が表す値のデータ型に依存します。
  
## <a name="character-string-constants"></a>文字列定数
文字列定数では、英数字 (a ～ z、A ～ Z、および 0 ～ 9)、感嘆符 (!)、アット マーク (@)、および番号記号 (#) などの特殊文字を単一引用符で囲みます。 COLLATE 句で照合順序を指定しない限り、文字列定数には現在のデータベースの既定の照合順序が割り当てられます。 ユーザーが入力した文字列は、コンピューターのコード ページで評価され、必要に応じてデータベースの既定のコード ページに翻訳されます。
  
接続に対して QUOTED_IDENTIFIER オプションが OFF に設定されている場合は、文字列を二重引用符で囲むこともできます。ただし、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider と ODBC ドライバーでは、自動的に SET QUOTED_IDENTIFIER ON が使用されます。 単一引用符を使用することをお勧めします。
  
単一引用符で囲まれた文字列に単一引用符を埋め込む場合は、単一引用符を 2 つ続けて並べることで 1 つの単一引用符を表します。 文字列が二重引用符で囲まれている場合は該当しません。
  
次に文字列の例を示します。
  
```sql
'Cincinnati'  
'O''Brien'  
'Process X is 50% complete.'  
'The level for job_id: %d should be between %d and %d.'  
"O'Brien"  
```  
  
空文字列は、2 つの単一引用符の間に何も挿入しないで表します。 6.x 互換性モードでは、空文字列は 1 つのスペースと見なされます。
  
文字列定数では、拡張照合順序がサポートされています。
  
> [!NOTE]  
>  8,000 バイト以上の文字列定数は **varchar(max)** データ型に分類されます。  
  
## <a name="unicode-strings"></a>Unicode 文字列
Unicode 文字列の形式は文字列と同様ですが、Unicode 文字列には前に識別子 N が付きます。N は、SQL-92 標準の National Language を表します。 プレフィックス N は常に大文字になります。 たとえば、'Michél' は文字定数であり、N'Michél' は Unicode 定数です。 Unicode 定数は Unicode データとして解釈され、コード ページを使用した評価は行われません。 Unicode 定数は照合順序を持ちます。 この照合順序では主に比較と大文字小文字の区別が制御されます。 COLLATE 句で照合順序を指定しない限り、Unicode 定数には現在のデータベースの既定の照合順序が割り当てられます。 文字データでは 1 文字を 1 バイトで格納するのに対し、Unicode データでは 1 文字を 2 バイトで格納します。 詳細については、「 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。
  
Unicode 文字列定数では、拡張照合順序がサポートされています。
  
> [!NOTE]  
>  8,000 バイト以上の Unicode 文字列定数は **nvarchar(max)** データ型に分類されます。  
  
## <a name="binary-constants"></a>binary 型定数
binary 型定数は 16 進数の文字列であり、`0x` というプレフィックスが付きます。 引用符では囲みません。
  
次に binary 型文字列の例を示します。
  
```sql
0xAE  
0x12Ef  
0x69048AEFDD010E  
0x  (empty binary string)  
```  
  
> [!NOTE]  
>  8,000 バイト以上の binary 型文字列は **varbinary(max)** データ型に分類されます。  
  
## <a name="bit-constants"></a>bit 型定数
**bit** 型定数は数値の 0 または 1 で表します。引用符では囲みません。 bit 型定数に 1 より大きい数値を使用すると、その値は 1 に変換されます。
  
## <a name="datetime-constants"></a>datetime 型定数
**datetime** 型定数は、特定の形式の日付文字値で表し、単一引用符で囲みます。
  
例を次に **datetime** 定数。
  
```sql
'December 5, 1985'  
'5 December, 1985'  
'851205'  
'12/5/98'  
```  
  
次に datetime 型定数の例を示します。
  
```sql
'14:30:24'  
'04:24 PM'  
```  
  
## <a name="integer-constants"></a>整数定数
**integer** 型定数は数値文字列で表し、引用符では囲みません。また、小数点は含みません。 **integer** 定数は整数である必要があります。 10 進数に含まれることはできません。
  
例を次に **integer** 定数。
  
```sql
1894  
2  
```  
  
## <a name="decimal-constants"></a>decimal 型定数
**decimal** 型定数は、小数点を含む数値文字列で表し、引用符では囲みません。
  
例を次に **decimal** 定数。
  
```sql
1894.1204  
2.0  
```  
  
## <a name="float-and-real-constants"></a>float 型と real 型定数
**float** および **real** 型定数は科学的表記法で表します。
  
次に **float** または **real** 値の例を示します。
  
```sql
101.5E5  
0.5E-2  
```  
  
## <a name="money-constants"></a>money 型定数
**money** 型定数は数値文字列で表し、オプションで小数点および通貨記号をプレフィックスとして付加することができます。 **money** 型定数は、引用符では囲みません。
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、金額を表す文字列の 3 桁ごとにコンマ (,) を挿入するなどのグループ化ルールを設定することはできません。
  
> [!NOTE]  
>  コンマは、指定した任意の場所無視 **money** リテラルです。  
  
例を次に **money** 定数。
  
```sql
$12  
$542023.14  
```  
  
## <a name="uniqueidentifier-constants"></a>uniqueidentifier 型定数
**uniqueidentifier** 型定数は、GUID 値を表す文字列です。 文字型または binary 型文字列の形式で指定できます。
  
次の例は、両方とも同じ GUID を指定しています。
  
```sql
'6F9619FF-8B86-D011-B42D-00C04FC964FF'  
0xff19966f868b11d0b42d00c04fc964ff  
```  
  
## <a name="specifying-negative-and-positive-numbers"></a>負または正の数値の指定  
数値が正であるか負であるかを示すには、数値型定数に **+** または **-** 単項演算子を付加します。 この方法で、符号付き数値を表す数式を作成できます。 **+** または **-** 単項演算子が付加されない場合、正の値になります。
  
署名 **integer** 式。  
  
```sql
+145345234
-2147483648
```
署名 **decimal** 式。  
  
```sql
+145345234.2234
-2147483648.10
```
  
署名 **float** 式。  
  
```sql
+123E-3
-12E5
```
  
署名 **money** 式。  
  
```sql
-$45.56
+$423456.99
```
  
## <a name="enhanced-collations"></a>拡張照合順序  
SQL Server では、拡張照合順序をサポートする文字列定数および Unicode 文字列定数がサポートされています。 詳細については、を参照してください #40。 [部単位で印刷する (& a)。TRANSACT-SQL と #41; ](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)句。
  
## <a name="see-also"></a>参照
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[演算子 (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)
  
  
