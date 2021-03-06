---
title: xml データ型に対する FOR XML サポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- user-defined functions [SQL Server], XML
- xml data type [SQL Server], FOR XML clause
ms.assetid: 365de07d-694c-4c8b-b671-8825be27f87c
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 14010ca375afdf5166f737a27e33f8ed3fc42c49
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327345"
---
# <a name="for-xml-support-for-the-xml-data-type"></a>xml データ型に対する FOR XML サポート
  FOR XML クエリの列を指定する場合`xml`型 SELECT 句で列の値は、ELEMENTS ディレクティブを指定するかどうかに関係なく、返された xml 要素としてマップされます。 `xml` 型の列内の XML 宣言はシリアル化されません。  
  
 たとえば、顧客の連絡先情報の取得、次のクエリなど、 `BusinessEntityID`、 `FirstName`、および`LastName`列、およびからの電話番号、`AdditionalContactInfo`の列`xml`型。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumber  
FROM Person.Person  
WHERE AdditionalContactInfo.query('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
')IS NOT NULL  
FOR XML AUTO, TYPE;  
```  
  
 列の値がから取得した追加の連絡先情報の値を除く、属性として返されるクエリでは ELEMENTS ディレクティブを指定しないため、`xml`型の列。 これらは要素として返されます。  
  
 結果の一部を次に示します。  
  
 `<Person.Person BusinessEntityID="291" FirstName="Gustavo" LastName="Achong">`  
  
 `<PhoneNumber>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1112</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1111</act:number>`  
  
 `</PhoneNumber>`  
  
 `</Person.Person>`  
  
 `<Person.Person BusinessEntityID="293" FirstName="Catherine" LastName="Abel">`  
  
 `<PhoneNumber>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-2222</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-1234</act:number>`  
  
 `</PhoneNumber>`  
  
```  
</Person.Person>  
...  
```  
  
 XQuery によって生成された XML 列に対して列の別名を指定した場合、その別名は XQuery によって生成された XML にラッパー要素を追加する際に使用されます。 たとえば、次のクエリでは、列の別名として `MorePhoneNumbers` を指定しています。  
  
```  
SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumber  
FROM Person.Person  
WHERE AdditionalContactInfo.query('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
')IS NOT NULL  
FOR XML AUTO, TYPE;  
```  
  
 XQuery によって返された XML は、次の結果の一部で示すように、<`MorePhoneNumbers`> 要素でラップされます。  
  
 `<Person.Person BusinessEntityID="291" FirstName="Gustavo" LastName="Achong">`  
  
 `<MorePhoneNumbers>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1112</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1111</act:number>`  
  
 `</MorePhoneNumbers>`  
  
 `</Person.Person>`  
  
 `<Person.Person BusinessEntityID="293" FirstName="Catherine" LastName="Abel">`  
  
 `<MorePhoneNumbers>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-2222</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-1234</act:number>`  
  
 `</MorePhoneNumbers>`  
  
```  
</Person.Person>  
...  
```  
  
 クエリで ELEMENTS ディレクティブを指定した場合、結果の XML では、BusinessEntityID、LastName、および FirstName が要素として返されます。  
  
 次の例では、FOR XML の処理ロジックにから XML データ内の任意の XML 宣言がシリアル化しないことを示しています、`xml`型の列。  
  
```  
create table t(i int, x xml)  
go  
insert into t values(1, '<?xml version="1.0" encoding="UTF-8" ?>  
                             <Root SomeID="10" />')  
select i, x  
from   t  
for xml auto;  
```  
  
 結果は次のとおりです。 結果の XML では、XML 宣言 <`?xml version="1.0" encoding="UTF-8" ?`> はシリアル化されません。  
  
```  
<root>  
  <t i="1">  
    <x>  
      <Root SomeID="10" />  
    </x>  
  </t>  
</root>  
```  
  
## <a name="returning-xml-from-a-user-defined-function"></a>ユーザー定義関数から XML を返す  
 FOR XML クエリを使用して、次のいずれかを返すユーザー定義関数から XML を返すことができます。  
  
-   1 つの `xml` 型の列を持つテーブル  
  
-   インスタンス、`xml`型  
  
 たとえば、次のユーザー定義関数がの 1 つの列を持つテーブルを返します`xm`l 型。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE FUNCTION dbo.MyUDF (@ProudctModelID int)  
RETURNS @T TABLE  
  (  
     ProductDescription xml  
  )  
AS  
BEGIN  
  INSERT @T  
     SELECT CatalogDescription.query('  
declare namespace PD="http://www.adventure-works.com/schemas/products/description";  
                    //PD:ProductDescription  ')  
     FROM Production.ProductModel  
     WHERE ProductModelID = @ProudctModelID  
  RETURN  
END;  
```  
  
 ユーザー定義関数を実行して、その関数から返されたテーブルにクエリを実行することができます。 この例では、テーブルのクエリによって返された XML が割り当てられている、`xml`型の変数。  
  
```  
declare @x xml;  
set @x = (SELECT * FROM MyUDF(19));  
select @x;  
```  
  
 次に、別のユーザー定義関数の例を示します。 このユーザー定義関数は、`xml` 型のインスタンスを返します。 この例では、スキーマの名前空間が指定されているため、ユーザー定義関数は型指定された XML インスタンスを返します。  
  
```  
DROP FUNCTION dbo.MyUDF;  
GO  
CREATE FUNCTION MyUDF (@ProductModelID int)   
RETURNS xml ([Production].[ProductDescriptionSchemaCollection])  
AS  
BEGIN  
  declare @x xml  
  set @x =   ( SELECT CatalogDescription  
          FROM Production.ProductModel  
          WHERE ProductModelID = @ProductModelID )  
  return @x  
END;  
```  
  
 ユーザー定義関数から返された XML は、次のように `xml` 型の変数に代入できます。  
  
```  
declare @x xml;  
SELECT @x= dbo.MyUDF4 (19) ;  
select @x;  
```  
  
## <a name="see-also"></a>参照  
 [各種 SQL Server データ型の FOR XML サポート](for-xml-support-for-various-sql-server-data-types.md)  
  
  
