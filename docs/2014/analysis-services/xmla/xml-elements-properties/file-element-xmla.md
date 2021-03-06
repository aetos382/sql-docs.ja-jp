---
title: ファイルの要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- File Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.file
- http://schemas.microsoft.com/analysisservices/2003/engine#File
- urn:schemas-microsoft-com:xml-analysis#File
helpviewer_keywords:
- File element
ms.assetid: 3dfd0e9b-746b-4ce5-8a95-610d2e573739
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b75a261f4a86d5a227e1018ad96a40d91db7b6c7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319222"
---
# <a name="file-element-xmla"></a>File 要素 (XMLA)
  親によって処理するためのファイルを識別する[バックアップ](../xml-elements-commands/backup-element-xmla.md)または[復元](../xml-elements-commands/restore-element-xmla.md)コマンド、または親[場所](location-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <File>...</File>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[バックアップ](../xml-elements-commands/backup-element-xmla.md)、[場所](location-element-xmla.md)、[復元](../xml-elements-commands/restore-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `File` 要素は UNC ファイル名を含みます。`File` 要素の使用法は親要素によって決定されます。  
  
 `Backup` コマンドの場合、`File` 要素は、`Backup` コマンドによって作成されるバックアップ ファイルの名前を決定します。 パスが指定されたパスがファイル名の一部として指定しない場合、`BackupDir`構成プロパティのインスタンスの[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]使用されます。 指定されたファイルが既に存在する場合、親コマンド `AllowOverwrite` の `Backup` 要素が `True` に設定されていない限り、エラーが発生します。  
  
 `Restore` コマンドの場合、`File` 要素は、`Restore` コマンドによって復元されるバックアップ ファイルの名前を決定します。  
  
 `Location` 要素の場合、`File` 要素は、リモート パーティションを含む [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスのリモート バックアップ ファイルを表します。 バックアップおよびリモート パーティションを復元する詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
## <a name="see-also"></a>参照  
 [AllowOverwrite 要素&#40;XMLA&#41;](allowoverwrite-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
