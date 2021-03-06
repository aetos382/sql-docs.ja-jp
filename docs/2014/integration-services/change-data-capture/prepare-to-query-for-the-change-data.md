---
title: 変更データのクエリを準備する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],preparing query
ms.assetid: 9ea2db7a-3dca-4bbf-9903-cccd2d494b5f
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 88f2dd6e5caf6cf5b601f07ca826d85808f9e6f9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37248812"
---
# <a name="prepare-to-query-for-the-change-data"></a>変更データのクエリを準備する
  変更データの増分読み込みを実行する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの制御フローにおいて、3 番目に行う最後のタスクは、変更データのクエリを準備してデータ フロー タスクを追加することです。  
  
> [!NOTE]  
>  制御フローの 2 番目のタスクは、選択した間隔の変更データが準備できていることを確認することです。 このタスクの詳細については、「[データの変更の準備ができているかどうかを判断する](determine-whether-the-change-data-is-ready.md)」を参照してください。 制御フローをデザインするプロセス全体の説明については、「[変更データ キャプチャ &#40;SSIS&#41;](change-data-capture-ssis.md)」を参照してください。  
  
## <a name="design-considerations"></a>デザインに関する考慮事項  
 変更データを取得するには、間隔のエンドポイントを入力パラメーターとして受け取り、指定した間隔の変更データを返す Transact-SQL テーブル値関数を呼び出します。 この関数は、データ フローの変換元コンポーネントによって呼び出されます。 この変換元コンポーネントに関する詳細については、「 [変更データを取得および理解する](retrieve-and-understand-the-change-data.md)」を参照してください。  
  
 OLE DB ソース、ADO ソース、ADO NET ソースなどの最もよく使用される [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 変換元コンポーネントでは、テーブル値関数のパラメーター情報を取得できません。 したがって、ほとんどの変換元では、パラメーター化された関数を直接呼び出すことはできません。  
  
 入力パラメーターを関数に渡すには、次の 2 つのデザイン方法があります。  
  
-   **パラメーター化クエリを文字列として作成します**。 スクリプト タスクまたは SQL 実行タスクを使用して、文字列にハードコーディングされたパラメーター値で動的 SQL 文字列を作成できます。 その後、この文字列をパッケージ変数に格納したものを使用して、変換元コンポーネントの SqlCommand プロパティを設定できます。 変換元コンポーネントでパラメーター情報が不要になるので、この方法は有効です。  
  
    > [!NOTE]  
    >  発生するオーバーヘッドは、SQL 実行タスクよりも事前コンパイルしたスクリプトの方が少なくなります。  
  
-   **パラメーター化されたラッパーを使用します**。 パラメーター化されたテーブル値関数を呼び出すラッパーとして、パラメーター化されたストアド プロシージャを作成できます。 変換元コンポーネントでストアド プロシージャのパラメーター情報を正常に取得できるので、この方法は有効です。  
  
 ここでは最初のデザイン方法を使用し、パラメーター化クエリを文字列として作成します。  
  
## <a name="preparing-the-query"></a>クエリの準備  
 入力パラメーターの値を 1 つのクエリ文字列に連結する前に、クエリで必要なパッケージ変数を設定する必要があります。  
  
#### <a name="to-set-up-package-variables"></a>パッケージ変数を設定するには  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の **[変数]** ウィンドウで、SQL 実行タスクによって返されるクエリ文字列を格納する文字列データ型の変数を作成します。  
  
     この例では、SqlDataQuery という名前の変数を使用します。  
  
 パッケージ変数を作成したら、スクリプト タスクまたは SQL 実行タスクを使用して入力パラメーターの値を連結できます。 次の 2 つの手順では、このコンポーネントを構成する方法について説明します。  
  
#### <a name="to-use-a-script-task-to-concatenate-the-query-string"></a>スクリプト タスクを使用してクエリ文字列を連結するには  
  
1.  **[制御フロー]** タブで、スクリプト タスクをパッケージの For ループ コンテナーの後に追加し、For ループ コンテナーをこのタスクに連結します。  
  
    > [!NOTE]  
    >  この手順では、パッケージによって 1 つのテーブルから増分読み込みが実行されることを前提としています。 複数のテーブルから読み込みが実行され、パッケージに親パッケージと複数の子パッケージが存在する場合、このタスクは最初のコンポーネントとして各子パッケージに追加されます。 詳細については、「 [複数のテーブルの増分読み込みを実行する](perform-an-incremental-load-of-multiple-tables.md)」を参照してください。  
  
2.  **[スクリプト タスク エディター]** の **[スクリプト]** ページで、次のオプションを選択します。  
  
    1.  **[ReadOnlyVariables]** で **[User::DataReady]**、 **[User::ExtractStartTime]**、および **[User::ExtractEndTime]** を一覧から選択します。  
  
    2.  **[ReadWriteVariables]** で [User::SqlDataQuery] を一覧から選択します。  
  
3.  **[スクリプト タスク エディター]** の **[スクリプト]** ページで、 **[スクリプトの編集]** をクリックしてスクリプト開発環境を開きます。  
  
4.  Main プロシージャに、次のいずれかのコード セグメントを入力します。  
  
    -   C# でプログラミングしている場合は、次のコード行を入力します。  
  
        ```  
        int dataReady;  
        System.DateTime extractStartTime;  
        System.DateTime extractEndTime;  
        string sqlDataQuery;  
  
        dataReady = (int)Dts.Variables["DataReady"].Value;  
        extractStartTime = (System.DateTime)Dts.Variables["ExtractStartTime"].Value;  
        extractEndTime = (System.DateTime)Dts.Variables["ExtractEndTime"].Value;  
  
        if (dataReady == 2)  
          {  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer('" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractStartTime) + "', '" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) + "')";  
          }  
        else  
          {  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer(null" + ", '" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) + "')";  
          }  
  
        Dts.Variables["SqlDataQuery"].Value = sqlDataQuery;  
        ```  
  
         \- または -  
  
    -   [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]でプログラミングしている場合は、次のコード行を入力します。  
  
        ```  
        Dim dataReady As Integer  
        Dim extractStartTime As Date  
        Dim extractEndTime As Date  
        Dim sqlDataQuery As String  
  
        dataReady = CType(Dts.Variables("DataReady").Value, Integer)  
        extractStartTime = CType(Dts.Variables("ExtractStartTime").Value, Date)  
        extractEndTime = CType(Dts.Variables("ExtractEndTime").Value, Date)  
  
        If dataReady = 2 Then  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer('" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractStartTime) & _  
              "', '" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) & _  
              "')"  
        Else  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer(null" & _  
              ", '" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) & _  
              "')"  
        End If  
  
        Dts.Variables("SqlDataQuery").Value = sqlDataQuery  
  
        ```  
  
5.  既定のコードを返す行のままに`DtsExecResult.Success`スクリプトの操作を実行します。  
  
6.  スクリプト開発環境と **[スクリプト タスク エディター]** を閉じます。  
  
#### <a name="to-use-an-execute-sql-task-to-concatenate-the-query-string"></a>SQL 実行タスクを使用してクエリ文字列を連結するには  
  
1.  **[制御フロー]** タブで、SQL 実行タスクをパッケージの For ループ コンテナーの後に追加し、For ループ コンテナーをこのタスクに連結します。  
  
    > [!NOTE]  
    >  この手順では、パッケージによって 1 つのテーブルから増分読み込みが実行されることを前提としています。 複数のテーブルから読み込みが実行され、パッケージに親パッケージと複数の子パッケージが存在する場合、このタスクは最初のコンポーネントとして各子パッケージに追加されます。 詳細については、「 [複数のテーブルの増分読み込みを実行する](perform-an-incremental-load-of-multiple-tables.md)」を参照してください。  
  
2.  **[SQL 実行タスク エディター]** の **[全般]** ページで、次のオプションを選択します。  
  
    1.  **[ResultSet]** で **[単一行]** を選択します。  
  
    2.  ソース データベースへの有効な接続を構成します。  
  
    3.  **[SQLSourceType]** で **[直接入力]** を選択します。  
  
    4.  **[SQLStatement]** に、次の SQL ステートメントを入力します。  
  
        ```  
        declare @ExtractStartTime datetime,  
        @ExtractEndTime datetime,   
        @DataReady int  
  
        select @DataReady = ?,   
        @ExtractStartTime = ?,   
        @ExtractEndTime = ?  
  
        if @DataReady = 2  
        select N'select * from CDCSample.uf_Customer'  
        + N'('''+ convert(nvarchar(30),@ExtractStartTime,120)  
        + ''', '''  
        + convert(nvarchar(30),@ExtractEndTime,120) + ''') '   
        as SqlDataQuery  
        else  
        select N'select * from CDCSample.uf_Customer'  
        + N'(null, '''  
        + convert(nvarchar(30),@ExtractEndTime,120)  
        + ''') '  
        as SqlDataQuery  
  
        ```  
  
        > [!NOTE]  
        >  `else`このサンプルで句は、開始日時として null 値を渡すことによって変更データの初期読み込みのクエリを生成します。 このサンプルは、変更データ キャプチャを有効にする前に行われた変更もデータ ウェアハウスにアップロードする必要があるシナリオには対応していません。  
  
3.  **[SQL 実行タスク エディター]** の **[パラメーター マッピング]** ページで、次のマッピングを行います。  
  
    1.  DataReady 変数をパラメーター 0 にマップします。  
  
    2.  ExtractStartTime 変数をパラメーター 1 にマップします。  
  
    3.  ExtractEndTime 変数をパラメーター 2 にマップします。  
  
4.  **[SQL 実行タスク エディター]** の **[結果セット]** ページで、結果名を SqlDataQuery 変数にマップします。  
  
     結果名は、返される単一列の名前 SqlDataQuery になります。  
  
 上記の手順で、ハードコーディングされた入力パラメーターの文字列値を使用してクエリ文字列を準備するタスクを構成しました。 次に、このクエリ文字列のコード例を示します。  
  
 `select * from CDCSample. uf_Customer('2007-06-11 14:21:58', '2007-06-12 14:21:58')`  
  
## <a name="adding-a-data-flow-task"></a>データ フロー タスクの追加  
 パッケージの制御フローをデザインする最後の手順として、データ フロー タスクを追加します。  
  
#### <a name="to-add-a-data-flow-task-and-complete-the-control-flow"></a>データ フロー タスクを追加して制御フローを完成させるには  
  
-   **[制御フロー]** タブで、データ フロー タスクを追加し、クエリ文字列を連結したタスクを連結します。  
  
## <a name="next-step"></a>次の手順  
 クエリ文字列を準備してデータ フロー タスクを構成したら、次にデータベースから変更データを取得するテーブル値関数を作成します。  
  
 **次のトピック:** [変更データを取得する関数を作成する](create-the-function-to-retrieve-the-change-data.md)  
  
  
