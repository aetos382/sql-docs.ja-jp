---
title: ジョブの変更 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 06edea33c572f0534e76a9425de56a73ebee53ae
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979104"
---
# <a name="modify-a-job"></a>Modify a Job
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> 
  [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]、[!INCLUDE[tsql](../../includes/tsql_md.md)]、または SQL Server 管理オブジェクトを使用して、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ジョブのプロパティを変更する方法について説明します。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**   
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   **ジョブを変更する方法:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server 管理オブジェクト](#SMO)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのマスター ジョブの対象サーバーを、ローカル サーバーとリモート サーバーの両方に設定することはできません。  
  
### <a name="Security"></a>Security  
**sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか変更できません。 詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="SSMS"></a>SQL Server Management Studio の使用  
  
#### <a name="to-modify-a-job"></a>ジョブを変更するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、変更するジョブを右クリックします。次に、 **[プロパティ]** をクリックします。  
  
3.  **[ジョブのプロパティ]** ダイアログ ボックスの対応するページを使用して、ジョブのプロパティ、ステップ、スケジュール、警告、および通知を変更します。  
  
## <a name="TSQL"></a>Transact-SQL の使用  
  
#### <a name="to-modify-a-job"></a>ジョブを変更するには  
  
1.  オブジェクト エクスプローラーで、データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。  
  
2.  ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  クエリ ウィンドウで、次のシステム ストアド プロシージャを使用してジョブを変更します。  
  
    -   ジョブの属性を変更するには、 [sp_update_job (Transact-SQL)](http://msdn.microsoft.com/cbdfea38-9e42-47f3-8fc8-5978b82e2623) を実行します。  
  
    -   ジョブ定義のスケジューリングの詳細を変更するには、 [sp_update_schedule (Transact-SQL)](http://msdn.microsoft.com/97b3119b-e43e-447a-bbfb-0b5499e2fefe) を実行します。  
  
    -   [sp_add_jobstep (Transact-SQL)](http://msdn.microsoft.com/97900032-523d-49d6-9865-2734fba1c755) を実行して、新しいジョブ ステップを追加します。  
  
    -   [sp_update_jobstep (Transact-SQL)](http://msdn.microsoft.com/e158802c-c347-4a5d-bf75-c03e5ae56e6b) を実行して、既存のジョブ ステップを変更します。  
  
    -   ジョブからジョブ ステップを削除するには、 [sp_delete_jobstep (Transact-SQL)](http://msdn.microsoft.com/421ede8e-ad57-474a-9fb9-92f70a3e77e3) を実行します。  
  
    -   任意の SQL Server エージェント マスター ジョブを変更するための追加のストアド プロシージャ:  
  
        -   [sp_delete_jobserver (Transact-SQL)](http://msdn.microsoft.com/6d63ed32-68cf-4d8f-aa40-05a3826e05b8) を実行して、ジョブに現在関連付けられているサーバーを削除します。  
  
        -   [sp_add_jobserver (Transact-SQL)](http://msdn.microsoft.com/485252cc-0081-490a-9bd1-cbbd68eea286) を実行して、サーバーを現在のジョブに関連付けます。  
  
## <a name="SMO"></a>SQL Server 管理オブジェクトの使用  
**ジョブを変更するには**  
  
Visual Basic、Visual C#、PowerShell などの選択したプログラミング言語で **Job** クラスを使用します。 詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](http://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。  
  
