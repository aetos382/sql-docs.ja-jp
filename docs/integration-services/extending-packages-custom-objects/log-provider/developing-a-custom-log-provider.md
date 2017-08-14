---
title: "カスタム ログ プロバイダーの開発 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SSIS packages, log providers
- custom log providers [Integration Services]
- SQL Server Integration Services packages, log providers
- log providers [Integration Services]
- packages [Integration Services], logs
- Integration Services packages, log providers
ms.assetid: 3f715b95-7074-4f5c-8ae2-246998052e78
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9d5dee6649539d340fd9954798db913136553aae
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="developing-a-custom-log-provider"></a>カスタム ログ プロバイダーの開発
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] には、パッケージの実行中に発生したイベントをキャプチャできるようにする広範なログ記録機能があります。 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]さまざまなログ プロバイダーを作成して、XML、テキスト、データベースなどの形式、または Windows イベント ログに格納するログの使用が含まれます。 提供されるログ プロバイダーと出力形式が、要件を必ずしも満たさない場合は、カスタム ログ プロバイダーを作成できます。  
  
 カスタム ログ プロバイダーを作成するには、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 基本クラスを継承するクラスを作成し、新しいクラスに <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 属性を適用し、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> プロパティや <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> メソッドなど、基本クラスの重要なメソッドとプロパティをオーバーライドする必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 ここでは、カスタム ログ プロバイダーを作成、構成、およびコーディングする方法について説明します。  
  
 [カスタム ログ プロバイダーを作成します。](../../../integration-services/extending-packages-custom-objects/log-provider/creating-a-custom-log-provider.md)  
 カスタム ログ プロバイダー プロジェクト用のクラスの作成方法について説明します。  
  
 [カスタム ログ プロバイダーのコーディング](../../../integration-services/extending-packages-custom-objects/log-provider/coding-a-custom-log-provider.md)  
 基本クラスのメソッドとプロパティのオーバーライドによる、カスタム ログ プロバイダーの実装方法について説明します。  
  
 [カスタム ログ プロバイダー用ユーザー インターフェイスの開発](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-user-interface-for-a-custom-log-provider.md)  
 カスタム ログ プロバイダーのカスタム ユーザー インターフェイスがサポートされていない[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]です。  
  
## <a name="related-topics"></a>関連項目  
  
### <a name="information-common-to-all-custom-objects"></a>すべてのカスタム オブジェクトに共通の情報  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なカスタム オブジェクトのすべての種類に共通の情報については、次のトピックを参照してください。  
  
 [Integration Services 用のカスタム オブジェクトの開発](../../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)  
 カスタム オブジェクトのすべての型を実装する基本的な手順について説明します[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]です。  
  
 [カスタム オブジェクトの永続化](../../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)  
 カスタムの永続性と、それが必要な場合について説明します。  
  
 [カスタム オブジェクトのビルド、配置、デバッグ](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
 カスタム オブジェクトをビルド、署名、配置、およびデバッグする方法について説明します。  
  
### <a name="information-about-other-custom-objects"></a>その他のカスタム オブジェクトに関する情報  
 作成できるカスタム オブジェクトの他の種類について[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]、次のトピックを参照してください。  
  
 [カスタム タスクの開発](../../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)  
 カスタム タスクのプログラム方法について説明します。  
  
 [カスタム接続マネージャーの開発](../../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)  
 カスタム接続マネージャーのプログラム方法について説明します。  
  
 [カスタム ForEach 列挙子の開発](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 カスタム列挙子のプログラム方法について説明します。  
  
 [カスタム データ フロー コンポーネントの開発](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)  
 カスタム データ フローの変換元、変換、変換先のプログラム方法について説明します。  
  