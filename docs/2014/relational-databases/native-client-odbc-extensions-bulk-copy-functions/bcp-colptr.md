---
title: bcp_colptr |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_colptr
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colptr function
ms.assetid: 02ece13e-1da3-4f9d-b860-3177e43d2471
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0c548a1decd7410cd1cbc8df3ee68126e62ca25
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413571"
---
# <a name="bcpcolptr"></a>bcp_colptr
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への現在のコピー操作に関するプログラム変数のデータ アドレスを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_colptr (  
HDBC   
hdbc  
,  
LPCBYTE   
pData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *pData*  
 コピーするデータを指すポインターです。 バインドされたデータ型は、大きな値型 (SQLTEXT や SQLIMAGE) 場合*pData* NULL を指定できます。 NULL *pData*を使用してチャンクで長い形式のデータ値は SQL Server に送信することを示します[bcp_moretext](bcp-moretext.md)します。  
  
 場合*pData* NULL と列に設定されている大きな値の型でない束縛のフィールドに対応する**bcp_colptr**が失敗します。  
  
 大きな値の型の詳細については、次を参照してください。 [bcp_bind](bcp-bind.md)**します。**  
  
 *idxServerCol*  
 データベース テーブル内にある、データのコピー先となる列の序数位置です。 テーブル内の最初の列は列 1 です。 列の序数位置がによって報告された[SQLColumns](../native-client-odbc-api/sqlcolumns.md)します。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>コメント  
 **Bcp_colptr**による SQL Server へデータをコピーするときに、特定の列のソース データのアドレスを変更することができます関数[bcp_sendrow](bcp-sendrow.md)します。  
  
 呼び出してユーザー データへのポインターを設定する最初に、 **bcp_bind**します。 呼び出しの間で、プログラム変数のデータのアドレスが変更された場合**bcp_sendrow**、呼び出すことができます**bcp_colptr**データへのポインターをリセットします。 次回の呼び出し**bcp_sendrow**への呼び出しによってアドレス指定されたデータを送信**bcp_colptr**します。  
  
 個別の必要がある**bcp_colptr**データのアドレスをテーブルの各列に対して呼び出しが変更します。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
