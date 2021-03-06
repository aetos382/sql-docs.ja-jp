---
title: CERTPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CERTPROPERTY
- CERTPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], schema names
- schemas [SQL Server], names
- CERTPROPERTY function
ms.assetid: 966c09aa-bc4e-45b0-ba53-c8381871f638
caps.latest.revision: 22
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 563c116b656fda3dc19ab82a9283c570a3c850d0
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37790863"
---
# <a name="certproperty-transact-sql"></a>CERTPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

指定した証明書のプロパティの値を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
CertProperty ( Cert_ID , '<PropertyName>' )  
  
<PropertyName> ::=  
   Expiry_Date | Start_Date | Issuer_Name   
   | Cert_Serial_Number | Subject | SID | String_SID   
```  
  
## <a name="arguments"></a>引数  
*Cert_ID*  
データ型 int の証明書の ID 値
  
*Expiry_Date*  
証明書の有効期限。
  
*Start_Date*  
証明書が有効になる日付。
  
*Issuer_Name*  
証明書の名前。
  
*Cert_Serial_Number*  
証明書のシリアル番号。
  
*Subject*  
証明書のサブジェクト。
  
 *SID*  
証明書の SID。 これは、この証明書にマップされているログインまたはユーザーの SID でもあります。
  
*String_SID*  
文字列としての証明書の SID。 これは、この証明書にマップされているログインまたはユーザーの SID でもあります。
  
## <a name="return-types"></a>戻り値の型
プロパティは単一引用符で囲んで指定する必要があります。
  
戻り値の型は、関数の呼び出しで指定されたプロパティによって異なります。 戻り値の型 **sql_variant** は、すべての戻り値をラップします。
-   *Expiry_Date* と *Start_Date* 返す **datetime**です。  
-   *Cert_Serial_Number*、*Issuer_Name*、*String_SID*、*Subject* はすべて **nvarchar** を返します。  
-   *SID* 返します **varbinary**です。  
  
## <a name="remarks"></a>Remarks  
[sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md) カタログ ビューの証明書情報を参照してください。
  
## <a name="permissions"></a>アクセス許可  
証明書に関する適切なアクセス許可が必要です。また、証明書に対する呼び出し元の VIEW アクセス許可が拒否されていない必要があります。 証明書のアクセス許可の詳細については、[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md) および [GRANT CERTIFICATE PERMISSIONS &#40;Transact-SQL&#41;](../../t-sql/statements/grant-certificate-permissions-transact-sql.md) を参照してください。
  
## <a name="examples"></a>使用例  
次の例では、証明書のサブジェクトを返します。
  
```sql
-- First create a certificate.  
CREATE CERTIFICATE Marketing19 WITH   
    START_DATE = '04/04/2004' ,  
    EXPIRY_DATE = '07/07/2040' ,  
    SUBJECT = 'Marketing Print Division';  
GO  
  
-- Now use CertProperty to examine certificate  
-- Marketing19's properties.  
DECLARE @CertSubject sql_variant;  
set @CertSubject = CertProperty( Cert_ID('Marketing19'), 'Subject');  
PRINT CONVERT(nvarchar, @CertSubject);  
GO  
```  
  
## <a name="see-also"></a>参照
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
[#40 です。 (&)、証明書を変更します。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-certificate-transact-sql.md)  
[CERT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/cert-id-transact-sql.md)
[暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
[セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)
  
  
