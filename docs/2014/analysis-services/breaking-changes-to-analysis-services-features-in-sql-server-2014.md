---
title: 重大な変更を Analysis Services の SQL Server 2014 の機能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- breaking changes [Analysis Services]
- upgrading Analysis Services
ms.assetid: aeb02542-5a6c-458c-a110-13413dd3e9d9
caps.latest.revision: 46
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a00010f10148d4ed949a7d5602a68fb6a53b3f6e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238052"
---
# <a name="breaking-changes-to-analysis-services-features-in-sql-server-2014"></a>SQL Server 2014 の Analysis Services 機能における重大な変更
  このトピックでは、 [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)]における重大な変更について説明します。 これらの変更によって、以前のバージョンの SQL Server に基づくアプリケーション、スクリプト、機能が使用できなくなる場合があります。  
  
 このトピックの内容  
  
-   [SQL Server 2014 における重大な変更](#bkmk_sql2014)  
  
-   [SQL Server 2012 SP1 における重大な変更](#bkmk_2012Sp1)  
  
-   [SQL Server 2012 における重大な変更](#bkmk_sql11)  
  
-   [SQL Server 2008/SQL Server 2008 R2 における重大な変更](#bkmk_sql10)  
  
##  <a name="bkmk_sql2014"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] における重大な変更  
 テーブル、多次元、データ マイニングで発表された変更の重大な新しいがあるまたは[!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)]このリリースで機能します。  ただし、ため[!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)]はこれと似ています、[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]と[!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]両方の以前のリリースからの変更の重大なバージョンが用意されてからアップグレードする場合の便利なように、ここ[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]します。  
  
##  <a name="bkmk_2012Sp1"></a> SQL Server 2012 SP1 における重大な変更  
 グローバリゼーションに関連するコードの変更は、一部のアプリケーションの互換性に影響することがわかっています。 既知の問題は次のとおりです。  
  
 **オブジェクト識別子の大文字小文字の区別**  
 すべてのオブジェクト識別子で大文字と小文字を区別しないようにするためのコード変更は、一部の言語では反対の影響を与えます。 この変更の目的は、照合順序に関係なく、すべてのオブジェクト識別子で大文字と小文字を区別しないようにすることです。 この変更により、同じソリューションのスタックで通常使用される他のアプリケーションと Analysis Services を揃えることになります。  
  
 26 の基本的なラテン語アルファベット文字に基づく言語の場合、現在はオブジェクト識別子で大文字と小文字が区別されないため、これは目的どおりの動作です。  
  
 キリル文字や、大文字と小文字の区別がある他の言語スクリプト (ギリシャ語、アルメニア語、およびコプト語) のオブジェクト識別子は、現在、大文字と小文字が区別されています。 互換性に影響する変更は、オブジェクト識別子とそれを参照する方法の間で大文字小文字の区別が異なる場合に発生する可能性が最も高くなります (たとえば、オブジェクト識別子をすべて小文字で参照する処理スクリプトなど)。 この動作は将来的に変更される可能性がありますが、一時的な回避策として、オブジェクト識別子として同じ大文字と小文字の区別を使用するようにスクリプトを変更することをお勧めします。  
  
##  <a name="bkmk_sql11"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] における重大な変更  
 このセクションの重大な変更について説明[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]機能[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]します。  
  
|問題点|説明|  
|-----------|-----------------|  
|[!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] のインストール用のセットアップ コマンドが削除されました。|セットアップでは [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] がインストールされますが、構成されなくなりました。 構成操作に使用される値を収集するためのセットアップ コマンドが削除されました。 削除されたコマンドは、/FARMACCOUNT、/FARMPASSWORD、/PASSPHRASE、/FARMADMINPORT などです。<br /><br /> 自動セットアップ用のインストール スクリプトを作成していた場合、[!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] をインストールするには、スクリプトを修正する必要があります。 代替手段として、自動モードでサーバーを構成する PowerShell コマンドレットを使用してください。 詳細については、次を参照してください。[コマンド プロンプトから PowerPivot をインストール](../../2014/sql-server/install/install-powerpivot-from-the-command-prompt.md)と[Windows PowerShell を使用して、PowerPivot 構成](power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)します。|  
  
##  <a name="bkmk_sql10"></a> における重大な変更 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]/[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]  
 このセクションでは、以前のリリースからの重大な変更について説明します。 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] からアップグレードする場合は、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] と [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] における重大な変更の内容を確認してください。  
  
|問題点|説明|  
|-----------|-----------------|  
|shallow exists 関数が、列挙メンバーまたは列挙セットの相互結合が含まれる名前付きセットとは異なる動作をする|[!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)] では、shallow exists 関数は、列挙メンバーまたは列挙セットの相互結合が含まれる名前付きセットとは動作しません。 元の旧バージョンと互換性のためのリリース バージョンおよび SP1 の[!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)]、1、または旧バージョンと互換性のため、構成プロパティを"\olap\query\namedsetshallowexistsmode"設定[!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)]SP2 では、2 に設定します。|  
|VBA 関数による null 値と空の値が異なる処理が、 [!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)]|[!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)]、VBA 関数の返された 0 または null 値または空の値と空の文字列を引数として使用しました。 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] では、null が返されます。|  
|DSO は既定ではインストールされないため、移行ウィザードは失敗します。|既定では、SQL Server 2008 には DSO (Decision Support オブジェクト) 下位互換コンポーネントがインストールされません。 下位互換パッケージは既定でインストールされますが、パッケージの DSO コンポーネントは無効になります。 SQL Server Analysis Services 移行ウィザードはこのコンポーネントに依存しているため、このコンポーネントがインストールされていない場合、移行ウィザードは正常に動作しません。 DSO コンポーネントをインストールするには、次の操作を行います。<br /><br /> 1) コントロール パネルを開きます。<br />2) で、Windows XP または Windows Server 2003 では、次のように選択します。**プログラム追加と削除**します。 Windows Vista および Windows Server 2008 の場合は、 **[プログラムと機能]** をクリックします。<br />3) を右クリック**Microsoft SQL Server 2005 の旧バージョンと互換性**、選び**変更**します。<br />4) では、旧バージョンとの互換性セットアップ ウィザードでは、次のようにクリックします。**次**します。<br />5) にプログラムのメンテナンス ページで、次のように選択します。**変更**、 をクリックし、**次**します。<br />6) [機能の選択] ページで、Decision Support オブジェクト (DSO) が使用できない場合下矢印をクリックし、選択**この機能はローカル ハード ドライブにインストールする**します。 **[次へ]** をクリックします。<br />7) のプログラム ページでの変更の準備完了、次のようにクリックします。**インストール**します。<br />8) と、インストールが完了したら、クリックして**完了**します。<br /><br /> <br /><br /> 移行が完了したら、前の手順に従って DSO のオプションを **[この機能は使用できません]** に変更して、DSO を削除できます。<br /><br /> 下位互換パッケージがインストールされていない場合、SQL Server 2008 配布メディアからインストールすることができます。 ターゲット アーキテクチャ (x86、x64、ia64) ごとにバージョンが存在することに注意してください。 これらのバージョンは、次の場所にあります。<br /><br /> x86\Setup\x86\SQLServer2005_BC.msi<br /><br /> x64\Setup\x64\SQLServer2005_BC.msi<br /><br /> ia64\Setup\ia64\SQLServer2005_BC.msi|  
|パーティションの場所をデータ フォルダーに指定することはお勧めしません。|サーバーは、データ フォルダーを管理すると共に、オブジェクトの作成、削除、変更に応じてフォルダーを作成または削除します。 したがって、データ フォルダー内にパーティション格納場所を指定することは、特にデータベース、キューブ、およびディメンションのサブフォルダーでは、お勧めしません。 サーバーで [作成] または [変更] を使用してこの手順を実行できますが、警告が表示されます。 SQL Server 2005 Analysis Services からデータベースをアップグレードするときに[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]作業は、データ フォルダーにパーティション格納場所を持つ Analysis Services、します。 復元または同期の際は、パーティション格納場所をデータ フォルダーの外部に移動する必要があります。|  
|ProClarity Analytics Server および Microsoft Office PerformancePoint Server 2007 で MDX の "EXISTING" キーワードを使用するクエリに対して、予期しない結果が返される場合があります。|ProClarity Analytics Server および Microsoft Office PerformancePoint Server 2007 では、MDX の EXISTING キーワードが正しく使用されない特定のシナリオがあります。 行われた変更により[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]Analysis Services では、これらのクエリが予期しない結果を返す可能性があります。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services の旧バージョンとの互換性](analysis-services-backward-compatibility.md)  
  
  
