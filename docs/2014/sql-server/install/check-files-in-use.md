---
title: 使用中のファイルを確認してください |。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ccd65867-d4c0-43b2-8361-7fd41c6f79ac
caps.latest.revision: 10
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 32e2152d93cc49309b6824462f5d413d59d30daf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37242312"
---
# <a name="check-files-in-use"></a>使用中のファイルの確認
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムのインストール後に Windows が再起動されないようにするには、[使用中のファイルの確認] ページを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムのセットアップ プログラムで必要とされるファイルをロックしているプロセスを特定します。  
  
 更新する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続しているすべてのアプリケーションとサービスを停止します。 これには [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] および [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を停止することが含まれます。  
  
 セットアップで、インストール中にファイルがロックされていると認識された場合、インストール完了後にコンピューターの再起動が必要になることがあります。 再起動が必要な場合は、コンピューターの再起動を促すメッセージが表示されます。 セットアップ プログラムで、インストール中にサービスを終了する必要がある場合は、インストールの完了後にそのサービスが再起動されます。  
  
 インストール後にコンピューターを再起動しなくてもいいように、セットアップ時に、ファイルをロックしているプロセスの一覧が表示されます。 一覧表示されたプロセスおよびアプリケーションを停止または終了します。 次に、 **[確認の更新]** をクリックしてチェックを再実行します。 実行中のチェックを終了するには **[確認の停止]** をクリックします。 ロックされているファイルが見つからなかった場合、表には何も表示されません。 ロックされていたプロセスが終了または停止したら、 **[次へ]** をクリックして続行します。  
  
 セットアップにより、情報がログ ファイルに書き込まれます。 ログ ファイルを表示する方法の詳細については、「[SQL Server セットアップ ログ ファイルの表示と読み取り](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)」および「[SQL Server のセットアップ ログ ファイルを読み取る方法](http://go.microsoft.com/fwlink/?LinkID=134490)」を参照してください。  
  
 次の情報がログ ファイルに含まれます。  
  
-   プロセスの名前  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の名前  
  
-   プロセスの種類  
  
-   プロセスが実行されているアカウント  
  
-   プロセス ID  
  
-   ロックされているファイルの名前  
  
## <a name="uielement-list"></a>UI 要素の一覧  
  
|名前|説明|  
|----------|-----------------|  
|Process|更新対象のファイルを使用しているプロセスの完全な名前を表示します。|  
|型|プロセスの種類を表示します。|  
|アカウント|プロセスが実行されているアカウントを表示します。|  
|プロセス ID|プロセス ID を表示します。|  
  
  
