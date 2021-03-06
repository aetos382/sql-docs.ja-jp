---
title: メモリ最適化ファイルグループ | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 14106cc9-816b-493a-bcb9-fe66a1cd4630
caps.latest.revision: 12
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6b18989012a733d39dca843f475ec23e99893d0c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246918"
---
# <a name="the-memory-optimized-filegroup"></a>メモリ最適化ファイルグループ
  メモリ最適化テーブルを作成するには、まずメモリ最適化ファイルグループを作成する必要があります。 メモリ最適化ファイル グループには 1 つ以上のコンテナーが含まれています。 各コンテナーには、データ ファイルかデルタ ファイル、あるいはその両方が含まれています。  
  
 SCHEMA_ONLY テーブルから取得したデータ行は持続的ではなく、メモリ最適化テーブルに対応するメタデータおよびネイティブ コンパイル ストアド プロシージャは従来型のカタログに格納されますが、メモリ最適化テーブルを含むデータベースを一貫した環境で提供できるように、 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] エンジンでは引き続き、SCHEMA_ONLY メモリ最適化テーブルに対応するメモリ最適化ファイルグループが必要です。  
  
 メモリ最適化ファイルグループは FILESTREAM ファイルグループをベースとしていますが、次の違いがあります。  
  
-   メモリ最適化ファイルグループは、データベースごとに 1 つだけ作成できます。 memory_optimized_data を含めることにより、このファイルグループに明示的にマークを付ける必要があります。 データベースを作成するときにファイルグループを作成することも、後でファイルグループを追加することもできます。  
  
    ```  
    ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA  
    ```  
  
-   MEMORY_OPTIMIZED_DATA ファイルグループに対して、1 つ以上のコンテナーを追加する必要があります。 以下に例を示します。  
  
    ```  
    ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod  
    ```  
  
-   メモリ最適化ファイルグループを作成するために、ファイルストリームを有効にする必要はありません ([FILESTREAM の有効化と構成](../blob/enable-and-configure-filestream.md))。 ファイルストリームへのマッピングは、 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] エンジンによって実行されます。  
  
-   メモリ最適化ファイルグループに対して、新しいコンテナーを追加することができます。 持続性のあるメモリ最適化テーブルのために必要な記憶域を拡張するため、および複数のコンテナーにまたがって IO を分散するために、新しいコンテナーが必要になることがあります。  
  
-   メモリ最適化ファイルグループでのデータの移動は、AlwaysOn 可用性グループ構成によって最適化されます。 セカンダリ レプリカに送信されるファイルストリームのファイルとは異なり、メモリ最適化ファイルグループ内のチェックポイント ファイル (データとデルタの両方) は、セカンダリ レプリカには送信されません。 データ ファイルとデルタ ファイルは、セカンダリ レプリカのトランザクション ログを使用して作成されます。  
  
 メモリ最適化ファイルグループには、次の制限が適用されます。  
  
-   メモリ最適化ファイルグループを作成した後、それを削除する唯一の方法はデータベースを削除することです。 運用環境において、メモリ最適化ファイルグループの削除が必要になることはほとんどありません。  
  
-   空ではないコンテナーを削除することや、メモリ最適化ファイルグループ内でデータ ファイルとデルタ ファイルのペアを別のコンテナーに移動することはできません。  
  
-   コンテナーに対して MAXSIZE を指定することはできません。  
  
## <a name="configuring-a-memory-optimized-filegroup"></a>メモリ最適化ファイルグループの構成  
 メモリ最適化ファイルグループ内で複数のコンテナーを作成し、それらを複数のドライブに分散して、データをメモリにストリーミングするための帯域幅をより多く確保することを考慮する必要があります。  
  
 記憶域を構成する場合には、持続性のあるメモリ最適化テーブルの 4 倍のサイズの空きディスク領域を指定する必要があります。 また、IO サブシステムが、対象のワークロードで必要な IOPS をサポートしていることを確認する必要もあります。 データ ファイルとデルタ ファイルのペアが特定の IOPS で作成される場合は、格納操作とマージ操作のために、3 倍の IOPS が必要です。 メモリ最適化ファイルグループに 1 つ以上のコンテナーを追加する方法で、記憶域容量と IOPS を追加できます。  
  
 複数のコンテナーと複数のドライブを使用するシナリオでは、データ ファイルとデルタ ファイルはラウンドロビン方式でコンテナーに割り当てられます。 最初のデータ ファイルは最初のコンテナーから割り当てられ、デルタ ファイルは次のコンテナーから割り当てられ、というように、この割り当てパターンが繰り返されます。 奇数個のドライブがあり、それぞれを 1 個のコンテナーにマップした場合は、この割り当て方法により、データ ファイルとデルタ ファイルが複数のコンテナーに対して均等に分散されます。 一方、偶数個のドライブがあり、それぞれを 1 個のコンテナーにマップした場合は、データ ファイルが奇数番目のドライブにマップされ、デルタ ファイルが偶数番目のドライブにマップされて不均等な記憶域という結果になる可能性があります。 復旧時に、均等な IO のストリームを取得するには、次の例で説明するように、データ ファイルとデルタ ファイルのペアを同じスピンドル/記憶域に配置することを検討してください。  
  
 **例:** メモリ最適化ファイル グループ コンテナーを 2 つを検討してください。 ドライブ X と Y ドライブ コンテナー 2 では、コンテナー 1。ラウンド ロビン方式でデータとデルタ ファイルの割り当てが完了するためコンテナー 1 はデータ ファイルのみを持つ、コンテナー 2 のみがデルタ ファイルでは、データ ファイルと、1 秒あたりの入力/出力操作だけでなく、ストレージの不均衡の持続性につながるデルタ ファイルよりも大幅に大きくなります。 X と Y のドライブで一様にデータとデルタ ファイルを配布するには、2 つではなく 4 つのコンテナーを作成し、最初の 2 つのコンテナーをドライブ X と Y ドライブに次の 2 つのコンテナーにマップします。ラウンド ロビン割り当てられる最初のデータとデルタ ファイルの最初が割り当てられますコンテナー 1 とコンテナー 2 からそれぞれどちら X ドライブにマップされます。同様に、次のデータとデルタ ファイルがコンテナー 3 と Y ドライブにマップするコンテナー 4 から割り当てられます。これにより、2 つのドライブで一様にデータとデルタ ファイルを配布できます。  
  
## <a name="see-also"></a>参照  
 [メモリ最適化オブジェクト用ストレージの作成と管理](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
