---
title: "CREATE FULLTEXT INDEX (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/05/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FULLTEXT_INDEX_TSQL
- CREATE_FULLTEXT_INDEX_TSQL
- CREATE FULLTEXT INDEX
- FULLTEXT INDEX
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], creating
- index creation [SQL Server], CREATE FULLTEXT INDEX statement
- CREATE FULLTEXT INDEX statement
ms.assetid: 8b80390f-5f8b-4e66-9bcc-cabd653c19fd
caps.latest.revision: 110
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 92749ed0518de83be07c6a80f9e3306741507166
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-fulltext-index-transact-sql"></a>CREATE FULLTEXT INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータベース内のテーブルまたはインデックス付きビューで、フルテキスト インデックスを作成します。 テーブルまたはインデックス付きビューごとに 1 つのフルテキスト インデックスのみ使用でき、各フルテキスト インデックスは 1 つのテーブルまたはインデックス付きビューに適用されます。 フルテキスト インデックスには、1,024 列まで格納できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE FULLTEXT INDEX ON table_name  
   [ ( { column_name   
             [ TYPE COLUMN type_column_name ]  
             [ LANGUAGE language_term ]   
             [ STATISTICAL_SEMANTICS ]  
        } [ ,...n]   
      ) ]  
    KEY INDEX index_name   
    [ ON <catalog_filegroup_option> ]  
    [ WITH [ ( ] <with_option> [ ,...n] [ ) ] ]  
[;]  
  
<catalog_filegroup_option>::=  
 {  
    fulltext_catalog_name   
 | ( fulltext_catalog_name, FILEGROUP filegroup_name )  
 | ( FILEGROUP filegroup_name, fulltext_catalog_name )  
 | ( FILEGROUP filegroup_name )  
 }  
  
<with_option>::=  
 {  
   CHANGE_TRACKING [ = ] { MANUAL | AUTO | OFF [, NO POPULATION ] }   
 | STOPLIST [ = ] { OFF | SYSTEM | stoplist_name }  
 | SEARCH PROPERTY LIST [ = ] property_list_name   
 }  
```  
  
## <a name="arguments"></a>引数  
 *table_name*  
 フルテキスト インデックスに含まれている列を格納するテーブルまたはインデックス付きビューの名前を指定します。  
  
 *column_name*  
 フルテキスト インデックスに含める列の名前を指定します。 型の列のみ**char**、 **varchar**、 **nchar**、 **nvarchar**、**テキスト**、 **ntext**、**イメージ**、 **xml**、および**varbinary (max)**フルテキスト検索のインデックスを作成できます。 複数の列を指定するには、繰り返し、 *column_name*次のように句。  
  
 CREATE FULLTEXT INDEX ON *table_name* (*column_name1* [...], *column_name2* [...]).  
  
 型の列*type_column_name*  
 テーブルの列の名前を指定*type_column_name*、つまりドキュメント型を保持するために使用される、 **varbinary (max)**または**イメージ**ドキュメント。 型列と呼ばれるこの列には、ユーザー指定のファイル拡張子 (.doc、.pdf、.xls など) が格納されます。 型列は、 **char**型、 **nchar**型、 **varchar**型、 **nvarchar**型にする必要があります。  
  
 型の列を指定*type_column_name*場合にのみ、 *column_name*を指定します、 **varbinary (max)**または**イメージ**れるデータ列バイナリ データとして格納されています。それ以外の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はエラーを返します。  
  
> [!NOTE]  
>  インデックスの作成時に、Full-text Engine を使用して、省略形で各テーブル行の型の列でドキュメントを使用するフルテキスト検索フィルターを特定*column_name*です。 フィルターはドキュメントをバイナリ ストリームとして読み込み、書式設定情報を削除し、ドキュメントからワード ブレーカー コンポーネントへテキストを送信します。 詳細については、「 [検索用フィルターの構成と管理](../../relational-databases/search/configure-and-manage-filters-for-search.md)」を参照してください。  
  
 言語*language_term*  
 格納されたデータの言語は、 *column_name*です。  
  
 *language_term*を省略して、文字列、整数、または言語のロケール識別子 (LCID) に対応する 16 進数の値として指定できます。 値を指定しなかった場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの既定の言語が使用されます。  
  
 場合*language_term*を指定すると、その言語に格納されているインデックスのデータに使用される**char**、 **nchar**、 **varchar**、 **nvarchar**、**テキスト**、および**ntext**列です。 この言語は場合、クエリ時に使用される既定の言語*language_term*列に対してフルテキスト述語の一部として指定されていません。  
  
 文字列として指定すると*language_term* syslanguages システム テーブルの別名の列の値に対応しています。 文字列は、ように、単一引用符で囲む必要があります**'***language_term***'**です。 整数として指定すると*language_term*言語を識別する実際の LCID です。 16 進数の値として指定する*language_term*は 0 x 後に LCID の 16 進値です。 16 進数の値は、先頭の 0 を含め、8 桁以内で指定してください。  
  
 値を 2 バイト文字セット (DBCS) の形式で指定すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で Unicode に変換されます。  
  
 指定した言語のワード ブレーカーとステミング機能などのリソースを有効にする必要があります*language_term*です。 このようなリソースは、指定した言語をサポートしていない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はエラーを返します。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの既定のフルテキスト言語に関する情報を取得するには、sp_configure ストアド プロシージャを使用します。 詳細については、このトピックの「 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)のバックアップと復元で使用する基本的なバックアップ メディア用語を紹介します。  
  
 列のデータ型が BLOB および XML 以外で、複数の言語のテキスト データが含まれている場合や、列に格納されているテキストの言語が不明な場合は、ニュートラル (0x0) 言語リソースを使用することもできます。 ただしその前に、ニュートラル (0x0) 言語リソースを使用した場合にどのような結果が起こりうるのかを理解しておく必要があります。 考えられる解決策とした場合、ニュートラル (0x0) 言語リソースを使用しての影響については、次を参照してください。 [、フルテキスト インデックスを作成時の言語を選択](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md)です。  
  
 データ型が XML または BLOB の列に格納されているドキュメントに対しては、そのドキュメントの言語のエンコードがインデックス作成時に使用されます。 たとえば、XML 列で、 **xml:lang**言語が XML ドキュメントの属性によって決定されます。 クエリ時に、以前指定した値で*language_term*しない限り、フルテキスト クエリに使用される既定の言語になります*language_term*フルテキスト クエリの一部として指定されます。  
  
 STATISTICAL_SEMANTICS  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 キー フレーズを追加で作成し、統計的セマンティック インデックス作成の一部である類似性のインデックスを記録します。 詳細については、「[セマンティック検索 &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md)」を参照してください。  
  
 キー インデックス*index_name*  
 一意なキー インデックスの名前は、 *table_name*です。 KEY INDEX は、一意で、単一のキーを含む、NULL 値を許容しない列であることが必要です。 フルテキストの一意キーには、一番小さな一意キー インデックスを選択します。  最適なパフォーマンスが得られるように、フルテキスト キーには整数データ型を使用することをお勧めします。  
  
 *fulltext_catalog_name*  
 フルテキスト インデックスに使用するフルテキスト カタログを指定します。 このカタログはデータベース内に存在する必要があります。 この句は省略可能です。 指定しない場合は、既定のカタログが使用されます。 既定のカタログが存在しない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はエラーを返します。  
  
 ファイル グループ*filegroup_name*  
 指定したファイル グループに、指定したフルテキスト インデックスを作成します。 ファイル グループは既に存在している必要があります。 FILEGROUP 句を指定しなかった場合、フルテキスト インデックスは、非パーティション テーブルの場合にはベース テーブルまたはベース ビューと同じファイル グループに、パーティション テーブルの場合にはプライマリ ファイル グループに配置されます。  
  
 [=] の CHANGE_TRACKING {MANUAL |**自動**|オフ [、NO POPULATION]}  
 によって、フルテキスト インデックスで対応されるテーブルの列に加えられた変更 (更新、削除または挿入) が反映されるかどうかを指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フルテキスト インデックスにします。 WRITETEXT および UPDATETEXT によるデータの変更は、フルテキスト インデックスには反映されず、変更の監視でも取得されません。  
  
 MANUAL  
 ALTER FULLTEXT INDEX を呼び出すことによって、追跡された変更を手動で反映する必要がありますを指定しています. START UPDATE POPULATION[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント (*手動作成*)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用すると、この [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを定期的に呼び出すことができます。  
  
 **自動**  
 ベース テーブルでデータが変更されたとに、追跡された変更を自動的に反映されることを指定します (*自動作成*)。 この場合、フルテキスト インデックスに対して変更は自動的に反映されますが、反映までに少し時間がかかることがあります。 AUTO は既定値です。  
  
 OFF [ `,` NO POPULATION]  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、インデックスの対象となるデータに対して行われた変更の一覧を保持しません。 NO POPULATION が指定されていないときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が作成された後に、インデックスを完全に設定します。  
  
 NO POPULATION オプションは、CHANGE_TRACKING が OFF の場合にだけ使用できます。 NO POPULATION を指定した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではインデックスの作成後、インデックスに対して値は設定されません。 この場合、ユーザーが START FULL POPULATION 句または START INCREMENTAL POPULATION 句を指定して ALTER FULLTEXT INDEX コマンドを実行した後でなければ、インデックスは作成されません。  
  
 ストップ リスト [=] {オフ |**システム** | *stoplist_name* }  
 フルテキスト ストップリストをインデックスに関連付けます。 インデックスには、指定したストップリストの一部であるトークンは設定されません。 STOPLIST を指定しない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってシステム フルテキスト ストップリストがインデックスに関連付けられます。  
  
 OFF  
 フルテキスト インデックスにストップリストを関連付けないことを指定します。  
  
 **システム**  
 このフルテキスト インデックスに対して既定のフルテキスト システム ストップリストを使用することを指定します。  
  
 *stoplist_name*  
 フルテキスト インデックスに関連付けるストップリストの名前を指定します。  
  
 検索プロパティ リスト [=] *property_list_name*  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 検索プロパティ リストとインデックスを関連付けます。  
  
 OFF  
 フルテキスト インデックスにプロパティ リストを関連付けないことを指定します。  
  
 *property_list_name*  
 フルテキスト インデックスに関連付ける検索プロパティ リストの名前を指定します。  
  
## <a name="remarks"></a>解説  
 フルテキスト インデックスの詳細については、次を参照してください。[の作成とフルテキスト インデックスの管理](../../relational-databases/search/create-and-manage-full-text-indexes.md)です。  
  
 **Xml**列、XML 要素のコンテンツにインデックスが、XML マークアップは無視されます、フルテキスト インデックスを作成することができます。 属性値には、数値でない限り、フルテキスト インデックスが設定されます。 要素タグはトークンの境界として使用されます。 複数言語を含む整形式の XML または HTML ドキュメントやフラグメントはサポートされます。 詳細については、「 [XML 列でのフルテキスト検索の使用](../../relational-databases/xml/use-full-text-search-with-xml-columns.md)」を参照してください。  
  
 インデックス キー列は整数データ型にすることをお勧めします。 整数データ型にすると、クエリの実行が最適化されます。  
  
## <a name="interactions-of-change-tracking-and-no-population-parameter"></a>変更の追跡と NO POPULATION パラメーターの相関関係  
 フルテキスト インデックスが作成されるかどうかは、変更の追跡が有効になっているかどうかと、ALTER FULLTEXT INDEX ステートメントで WITH NO POPULATION が指定されているかどうかによって決まります。 次の表は、その相関関係の結果をまとめたものです。  
  
|変更の追跡|WITH NO POPULATION|結果|  
|---------------------|------------------------|------------|  
|有効ではない|指定なし|インデックスで完全作成が実行されます。|  
|有効ではない|[Specified]|ALTER FULLTEXT INDEX...START POPULATION ステートメントが実行されるまで、インデックスの作成は行われません。|  
|有効|指定あり|エラーが発生し、インデックスは変更されません。|  
|有効|指定なし|インデックスで完全作成が実行されます。|  
  
 詳細については、フルテキスト インデックスを設定する、次を参照してください。 [、フルテキスト インデックスの作成](../../relational-databases/search/populate-full-text-indexes.md)です。  
  
## <a name="permissions"></a>Permissions  
 実行するには、フルテキスト カタログに対する REFERENCES 権限とテーブルまたはインデックス付きビューに対する ALTER 権限が与えられているか、sysadmin 固定サーバー ロール、db_owner 固定データベース ロールまたは db_ddladmin 固定データベース ロールのメンバーであることが必要です。  
  
 SET STOPLIST を指定した場合は、ユーザーが指定のストップリストに対する REFERENCES 権限を持っている必要があります。 ストップリストの所有者がこの権限を許可できます。  
  
> [!NOTE]  
>  パブリックでに付属している既定のストップ リストに対する REFERENCE 権限が付与[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-unique-index-a-full-text-catalog-and-a-full-text-index"></a>A. 一意のインデックス、フルテキスト カタログ、およびフルテキスト インデックスを作成する  
 次の例では、一意のインデックスを作成で、`JobCandidateID`の列、`HumanResources.JobCandidate`のテーブル、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]サンプル データベース。 その後、既定のフルテキスト カタログ、`ft` を作成します。 そして最後に、`Resume` カタログおよびシステム ストップリストを使用して `ft` 列にフルテキスト インデックスを作成します。  
  
```  
CREATE UNIQUE INDEX ui_ukJobCand ON HumanResources.JobCandidate(JobCandidateID);  
CREATE FULLTEXT CATALOG ft AS DEFAULT;  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate(Resume)   
   KEY INDEX ui_ukJobCand   
   WITH STOPLIST = SYSTEM;  
GO  
```  
  
### <a name="b-creating-a-full-text-index-on-several-table-columns"></a>B. 複数のテーブル列にフルテキスト インデックスを作成する  
 次の例では、`production_catalog` サンプル データベースにフルテキスト カタログ、`AdventureWorks` を作成します。 その後、この新しいカタログを使用するフルテキスト インデックスを作成します。 フルテキスト インデックスは、`ReviewerName` の `EmailAddress`、`Comments`、および `Production.ProductReview` 列にあります。 各列の例では、指定、英語の LCID、 `1033`、これは、列内のデータの言語です。 このフルテキスト インデックスは、既存の一意なキー インデックスを使用して`PK_ProductReview_ProductReviewID`です。 このインデックス キーは整数列、推奨される`ProductReviewID`です。  
  
```  
CREATE FULLTEXT CATALOG production_catalog;  
GO  
CREATE FULLTEXT INDEX ON Production.ProductReview  
 (   
  ReviewerName  
     Language 1033,  
  EmailAddress  
     Language 1033,  
  Comments   
     Language 1033       
 )   
  KEY INDEX PK_ProductReview_ProductReviewID   
      ON production_catalog;   
GO  
```  
  
### <a name="c-creating-a-full-text-index-with-a-search-property-list-without-populating-it"></a>C. インデックスの値を設定せずに、検索プロパティ リストのフルテキスト インデックスを作成する  
 次の例では、`Title` テーブルの `DocumentSummary`、`Document`、および `Production.Document` の各列にフルテキスト インデックスを作成します。 この例では英語の LCID、指定`1033`、これは、列内のデータの言語です。 このフルテキスト インデックスは、既定のフルテキスト カタログおよび既存の一意なキー インデックス、`PK_Document_DocumentID` を使用します。 このインデックス キーは整数列、推奨される`DocumentID`です。  
  
 この例では、ストップリストとして SYSTEM を指定します。 また、検索プロパティ リストを指定`DocumentPropertyList`以外の場合は、このプロパティ リストを作成する例についてを参照してください[CREATE SEARCH PROPERTY LIST & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-search-property-list-transact-sql.md).  
  
 この例では、変更の追跡が OFF で、NO POPULATION を指定しています。 代わりに、ALTER FULLTEXT INDEX ステートメントを指定して、後のピーク タイム以外の時間に新しいインデックスの完全作成を開始し、自動変更追跡を有効にしています。  
  
```  
CREATE FULLTEXT INDEX ON Production.Document  
  (   
  Title  
      Language 1033,   
  DocumentSummary  
      Language 1033,   
  Document   
      TYPE COLUMN FileExtension  
      Language 1033   
  )  
  KEY INDEX PK_Document_DocumentID  
          WITH STOPLIST = SYSTEM, SEARCH PROPERTY LIST = DocumentPropertyList, CHANGE_TRACKING OFF, NO POPULATION;  
   GO  
```  
  
 後のピーク タイム以外の時間にインデックスを作成  
  
```  
ALTER FULLTEXT INDEX ON Production.Document SET CHANGE_TRACKING AUTO;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [フルテキスト インデックスの作成と管理](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-fulltext-index-transact-sql.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [sys.fulltext_indexes & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)   
 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
