---
title: CountDistinct 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 902c251e-e1e8-41d2-ac20-5bb6138ac410
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 37fc5f2045f2fcf232ab8984ff83aa2ed3abb230
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227022"
---
# <a name="countdistinct-function-report-builder-and-ssrs"></a>CountDistinct 関数 (レポート ビルダーおよび SSRS)
  式で指定された NULL 以外の値が全部で何種類あるかを、指定されたスコープのコンテキストで評価して返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>構文  
  
```  
  
CountDistinct(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *式 (expression)*  
 (`Variant`) 集計関数の実行対象の式。  
  
 *スコープ (scope)*  
 (`String`) 省略可能です。 集計関数の適用先となるレポート アイテムを含むデータセット、グループ、またはデータ領域の名前です。 *scope* を指定しない場合、現在のスコープが使用されます。  
  
 *再帰*  
 (**列挙型**) 省略可。 `Simple` (既定値) または`RdlRecursive`します。 集計を再帰的に実行するかどうかを指定します。  
  
## <a name="return-type"></a>戻り値の型  
 返します、`Integer`します。  
  
## <a name="remarks"></a>コメント  
 *scope* の値は文字列定数である必要があり、式にすることはできません。 外部の集計または他の集計を指定しない集計では、 *scope* は現在のスコープまたはコンテナー スコープを参照する必要があります。 集計の集計では、入れ子になった集計に、子のスコープを指定できます。  
  
 *Expression* には、入れ子になった集計関数への呼び出しを含めることができます。ただし、次に示すように、これには例外および条件があります。  
  
-   入れ子集計の*Scope* は、外部集計のスコープと同じであるか、そのスコープに含まれている必要があります。 式内のすべてのスコープについては、1 つのスコープがそれ以外のすべてのスコープに対する子であるようなリレーションシップが必要です。  
  
-   入れ子集計の*Scope* には、データセット名は使用できません。  
  
-   *式*する必要がありますが含まれていない`First`、 `Last`、 `Previous`、または`RunningValue`関数。  
  
-   *Expression* には、 *recursive*を指定する入れ子集計を含めることができません。  
  
 詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。  
  
 再帰的集計については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、既定のスコープおよび親グループのスコープで、 `Size` の NULL でない一意の値の数を計算する式を示します。 この式は、子グループ `GroupbySubcategory`に属する行内のセルに追加されます。 親グループは `GroupbyCategory`です。 この式では、 `GroupbySubcategory` (既定のスコープ) の結果、次に `GroupbyCategory` (親グループのスコープ) の結果が表示されます。  
  
> [!NOTE]  
>  実際には、式に復帰と改行を含めないでください。サンプル コードでは、ドキュメントを読みやすくするためにこれらが含まれています。 次の例をコピーする場合は、各行の復帰を削除してください。  
  
```  
="Distinct count (Subcategory): " & CountDistinct(Fields!Size.Value) &   
"Distinct count (Category): " & CountDistinct(Fields!Size.Value,"GroupbyCategory")  
```  
  
## <a name="see-also"></a>参照  
 [レポートで式を使用して&#40;レポート ビルダーおよび SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [合計、集計、および組み込みコレクションの式のスコープ&#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
