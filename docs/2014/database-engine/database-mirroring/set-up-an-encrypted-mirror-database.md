---
title: 暗号化されたミラー データベースの設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- database master key [SQL Server], database mirroring
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 7329a575-be29-46e0-abc6-1344db37920c
caps.latest.revision: 22
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 550531519953de312f04655f5e7cf58c80a07448
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279128"
---
# <a name="set-up-an-encrypted-mirror-database"></a>暗号化されたミラー データベースの設定

ミラー データベースのデータベース マスター キーの暗号化を自動的に解除できるようにするには、マスター キーの暗号化に使用したパスワードをミラー サーバー インスタンスに指定する必要があります。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンには、パスワードを転送するメカニズムがあります。 データベース ミラーリングを開始する前にデータベース マスター キーに対する資格情報を作成するには、 **sp_control_dbmasterkey_password** を使用します。 この処理は、ミラー化するすべてのデータベースに対して行う必要があります。 詳細については、「 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql)」を参照してください。
  
> [!CAUTION]  
>  **sa** など高いレベルの特権を持つサーバー プリンシパルからのアクセスを禁止したままにしておく必要のあるデータベースについては、フェールオーバー時の暗号化解除を有効にしないでください。 データベースのキー階層をサービス マスター キーで暗号化解除できないようにデータベースを構成できます。 このオプションは、 **sa** など特権レベルの高いサーバー プリンシパルからアクセスできてはならない情報を格納しているデータベースに対する多層防御の 1 つとしてサポートされています。 このようなデータベースに対してフェールオーバー時の暗号化解除を有効にすると、この多層防御が効力を失います。その結果、 **sa** など特権レベルの高いサーバー プリンシパルによるデータベースの暗号化解除が可能になります。  


<!-- Note: We cannot append '?view=sql-server-2016' to these, even tho in theory we might want to. -->

## <a name="see-also"></a>参照

[sp_control_dbmasterkey_password &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql)

[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)

[ALTER MASTER KEY &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql)

[暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)

[データベース ミラーリングの設定 &#40;SQL Server&#41;](database-mirroring-sql-server.md)

