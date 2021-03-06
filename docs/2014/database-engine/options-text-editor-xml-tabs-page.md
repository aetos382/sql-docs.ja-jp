---
title: 'オプション ([テキスト エディター: XML:Tabs] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
ms.assetid: 13bf5f8c-aba3-4c05-b8bb-eb475797c9bd
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 2843acbc8935d8bd9f505a9265c704a342ddee3d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37324922"
---
# <a name="options-text-editorxmltabs-page"></a>オプション ([テキスト エディター: XML:Tabs] ページ)
  このダイアログ ボックスを使用すると、XML ドキュメントの編集に使用される XML エディターのタブの動作を変更できます。 この設定を表示するには、**[ツール]** メニューの **[オプション]** をクリックして、**[テキスト エディター]** フォルダーを展開し、さらに **[XML]** サブフォルダーを展開して、**[タブ]** をクリックします。  
  
## <a name="setting-options-in-multiple-locations"></a>複数の場所でのオプション設定  
 XML エディターのオプションは、**[すべての言語] の [全般]** ダイアログで設定することもできます。 ただし、DMX エディターや MDX エディターなど、他の **エディターに対し、** [すべての言語] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のダイアログを使用して異なるオプションを設定する場合は、ここで紹介したダイアログを使用して XML エディターのオプションを設定し直す必要があります。  
  
## <a name="indenting"></a>インデント  
 **なし**  
 このオプションが選択されている場合、Enter キーを押したときに作成される新しい行は、インデントされません。 カーソルは、新しい行の 1 列目に置かれます。  
  
 **ブロック**  
 このオプションが選択されている場合、Enter キーを押したときに作成される新しい行は、直前の行と同じ位置まで自動的にインデントされます。  
  
 **スマート**  
 このオプションが選択されている場合、Enter キーを押したときに作成される新しい行の位置は、コンテキストに応じて決定されます。 たとえば、左中かっこ ({) の後では、かっこで囲まれる行は自動的にタブ 1 個を追加してインデントされます。 対応する右中かっこ (}) は、左中かっこに合わせた位置に置かれます。  
  
## <a name="tabs"></a>タブ  
 **[タブ サイズ]**  
 タブ ストップ間の間隔をスペース数で設定します。 既定値は、スペースが 4 つです。  
  
 **インデントのサイズ**  
 自動インデントのサイズをスペース数で設定します。 既定値は、スペースが 4 つです。 指定されたサイズになるように、タブ文字、スペース文字、またはその両方が挿入されます。  
  
 **スペースを挿入します。**  
 このオプションを選択すると、タブ文字を使用せずにスペース文字だけを挿入してインデントします。 たとえば **[インデント サイズ]** が 5 に設定されている場合、 のメイン ウィンドウで **キーを押すか、ツール バーの [** インデント [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ] ボタンを押すごとに、5 つのスペース文字が挿入されます。  
  
 **タブを保持します。**  
 このオプションを選択すると、インデントするときにできる限り多くのタブ文字を挿入します。 それぞれのタブ文字が、**[タブ サイズ]** で指定された数のスペースを満たします。 **[インデント サイズ]** が **[タブ サイズ]** の倍数でない場合は、その差を埋めるためにスペース文字が追加されます。  
  
  
