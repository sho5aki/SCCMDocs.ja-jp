---
title: "移行の完了 | System Center Configuration Manager"
description: "ソース階層にデータが含まれなくなった後で、System Center Configuration Manager の移行先階層への移行を完了する方法について説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4854b50-2e8c-414c-a872-9579554dca98
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 862a039ada302c9432fc86d68f5ba9aad360f69b


---
# <a name="planning-to-complete-migration-in-system-center-configuration-manager"></a>System Center Configuration Manager での移行完了の計画

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager では、移行先階層に移行するデータがソース階層に含まれない場合、移行プロセスを完了できます。 一般的に、移行の完了には次の手順が含まれます。  

-   必要なデータが移行されたことを確認します。 ソース階層からの移行を完了する前に、移行先階層に必要なすべてのリソースがソース階層から正常に移行されたことを確認します。 これには、データとクライアントも含まれます。  

-   ソース サイトからのデータ収集を停止します。 ソース階層からの移行を完了するには、まずソース サイトからのデータ収集を停止する必要があります。  

-   移行データをクリーンアップします。 ソース階層内にあるすべてのソース サイトからのデータ収集を停止したら、移行先階層のデータベースから、移行プロセスとソース階層に関するデータを削除します。  

-   ソース階層の使用を停止します。 ソース階層からの移行を完了し、ソース階層に管理対象のリソースが含まれていないことを確認したら、ソース階層内のサイトの使用を停止し、環境から関連するインフラストラクチャを削除できます。 サイトとソース階層の使用停止方法の詳細については、使用しているバージョンの Configuration Manager のドキュメントを参照してください。  

データ収集を停止し、移行データをクリーンアップしてソース階層からの移行を完了する方法を計画する際には、次のサイトを参照してください。  

-   [データ収集の停止を計画する](#Plan_to_Stop_Data_Gath)  

-   [移行データのクリーンアップを計画する](#Plan_to_clean_up)  

##  <a name="a-nameplantostopdatagatha-plan-to-stop-gathering-data"></a><a name="Plan_to_Stop_Data_Gath"></a> データ収集の停止を計画する  
 移行を完了して移行データをクリーンアップする前に、ソース階層内の各ソース サイトからのデータ収集を停止する必要があります。 各ソース サイトからのデータ収集を停止するには、最下位のソースサイトで [データ収集の停止] コマンドを実行してから、各親サイトごとにそのプロセスを繰り返し実行する必要があります。 **** ソース階層の最上位サイトは、データ収集を停止する最後のサイトにする必要があります。 親サイトでデータ収集の停止コマンドを実行する前に、各子サイトでデータ収集を停止する必要があります。 通常、移行処理を完了する準備ができた時点でデータ収集を停止します。  

 ソース サイトからのデータ収集を停止すると、移行先階層内のクライアントは、コンテンツの場所としてソース サイトの共有配布ポイントを使用できなくなります。 そのため、移行先階層のクライアントで必要な移行済みコンテンツを引き続き使用できるようにするには、次のいずれかの方法を実行してください。  

-   移行先階層で、少なくとも 1 つの配布ポイントにコンテンツを配布する。  

-   ソース サイトからのデータの収集を停止する前に、必要なコンテンツがある共有配布ポイントをアップグレードまたは再割り当てする。 共有配布ポイントのアップグレードまたは再割り当ての詳細については、「[System Center Configuration Manager のコンテンツ展開移行戦略の計画](../../core/migration/planning-a-content-deployment-migration-strategy.md) 」トピックの該当するセクションを参照してください。  

ソース階層内の各ソース サイトからのデータ収集を停止した後で、移行データをクリーンアップできます。 移行データをクリーンアップするまで、実行済み、または実行予定の各移行ジョブは Configuration Manager コンソール内でアクセス可能な状態のままになります。  

ソース サイトとデータ収集の詳細については、「[Planning a source hierarchy strategy in System Center Configuration Manager](../../core/migration/planning-a-source-hierarchy-strategy.md)」(System Center Configuration Manager のソース階層戦略の計画) を参照してください。  

##  <a name="a-nameplantocleanupa-plan-to-clean-up-migration-data"></a><a name="Plan_to_clean_up"></a> 移行データのクリーンアップを計画する  
 移行完了の最終手順は、移行データのクリーンアップです。 ソース階層の各ソース サイトのデータ収集を停止した後で、[移行データのクリーン アップ **** ] コマンドを使用できます。 クリーンアップは任意ですが、実行すると、移行先階層のデータベースから現在のソース階層に関するデータが削除されます。  

 移行データをクリーンアップすると、移行に関するほとんどのデータが移行先階層のデータベースから削除されます。 ただし、移行済みオブジェクトに関する詳細は維持されます。 これらの詳細を基に、[移行 **** ] ワークスペースを使用して、移行したデータを含むソース階層を再構成することで、そのソース階層から移行を再開したり、以前に移行したオブジェクトとオブジェクトのサイト所有権を確認したりできます。  



<!--HONumber=Nov16_HO1-->


