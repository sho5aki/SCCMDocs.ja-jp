---
title: "探索の実行 | System Center Configuration Manager"
description: "探索プロセスおよび探索データ レコードの概要を読んでください。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 30844519-ce14-456f-bfb8-4318b578e9f6
caps.latest.revision: 20
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: d73b493318b0a1938d42265ec03369015365addb


---
# <a name="run-discovery-for-system-center-configuration-manager"></a>System Center Configuration Manager 用の探索の実行

*適用対象: System Center Configuration Manager (Current Branch)*

1 つ以上の探索方法を    
      System Center Configuration Manager で使用して、変更できるデバイスとユーザーのリソースを見つけます。 また、環境のネットワーク インフラストラクチャを識別するために探索を使用することもできます。  さまざまなものを探すために使用できるさまざまな探索方法があり、各方法に独自の構成と制限があります。  

## <a name="overview-of-discovery"></a>探索の概要  
 探索は、Configuration Manager が管理可能なリソースについての情報を得るプロセスです。 利用可能な探索方法は次のとおりです。  

-   Active Directory フォレストの探索  

-   Active Directory グループの探索  

-   Active Directory システムの探索  

-   Active Directory ユーザー検出  

-   定期探索  

-   ネットワーク探索  

-   サーバー探索  

> [!TIP]  
>  「[About discovery methods for System Center Configuration Manager (System Center Configuration Manager の探索方法について)](../../../../core/servers/deploy/configure/about-discovery-methods.md)」で個々の探索方法について学習できます。  
>   
>  階層内のどのサイトにどの方法を使用するかについては、「[Select discovery methods to use for System Center Configuration Manager (System Center Configuration Manager に使用する探索方法の選択)](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md)」をご覧ください。  

 ほとんどの探索方法を使用するには、方法をサイトで有効にして、特定のネットワークまたは Active Directory の場所を検索するように構成する必要があります。 探索方法が実行されると、Configuration Manager が管理できるデバイスまたはユーザー情報について指定場所へのクエリが実行されます。  探索方法でリソースについての情報が見つかると、その情報は探索データ レコード (DDR) と呼ばれるファイルに保存されます。このファイルは、プライマリ サイトまたは中央管理サイトで処理されます。 DDR の処理では、新たに探索されたリソースのために新しいレコードがサイト データベースに作成されるか、または既存のレコードが新しい情報で更新されます。  

 探索方法によっては、大量のネットワーク トラフィックが発生して、生成された DDR の処理に大量の CPU リソースが消費されることがあります。 したがって、目的のために必要な探索方法のみを使用することを計画してください。 始めは 1 つまたは 2 つの探索方法だけを使用するようにして、後で追加的な方法を慎重に有効にして、環境での探索レベルを拡張してください。  

 サイト データベースに追加された探索情報は、探索または処理された場所に関係なく、階層内の各サイトにレプリケートされます。 したがって、さまざまなサイトでの探索方法に対してさまざまなスケジュールと設定を構成することはできますが、重複する探索処理によるネットワーク帯域幅の使用を減らしたり、複数のサイトで重複している探索データの処理を減らしたりすために、特定の探索方法を 1 つのサイトだけで実行するようにしてください。  

 探索データを使用すると、次のような管理タスクのために、リソースを論理的にグループ化するカスタム コレクションやクエリを作成できます。  

-   クライアントのインストールまたはアップグレードをプッシュする  

-   ユーザーまたはデバイスにコンテンツを展開する  

-   クライアント設定および関連する構成を展開する  

##  <a name="a-namebkmkddrsa-about-discovery-data-records"></a><a name="BKMK_DDRs"></a> 探索データ レコードについて  
 探索データ レコード (DDR) は、探索方法によって作成されるファイルであり、Configuration Manager で管理できるリソースに関する情報を含んでいます。 この情報には、コンピューターやユーザー、ネットワーク インフラストラクチャの情報があります。 DDR は、プライマリ サイトか中央管理サイトで処理されます。 DDR にあるリソースの情報がデータベースに挿入されると、その DDR は削除され、階層内のすべてのサイトに情報がグローバル データとしてレプリケートされます。  

 DDR を処理するサイトは、DDR に含まれている情報によって異なります。  

-   今までデータベースには存在しておらず、新しく検出されたリソースの DDR は、階層の最上位サイトで処理されます。 最上位サイトのデータベースに新しいリソース レコードが作成され、固有な識別子が割り当てられます。 DDR は、最上位サイトに到達するまで、ファイルベースのレプリケーションによって転送されます。  

-   既に検出されているオブジェクトの DDR は、プライマリ サイトで処理されます。 データベースに存在するリソースに関する情報が DDR に含まれている場合は、子プライマリ サイトは DDR を中央管理サイトに転送しません。  

-   セカンダリ サイトは、探索データ レコードを処理することはなく、いつもファイルベースのレプリケーションで親プライマリ サイトに転送します。  

DDR ファイルには、.ddr という拡張子が付き、サイズは通常 1 KB ほどです。  

## <a name="get-started-with-discovery"></a>探索の概要:  
 Configuration Manager コンソールを使用して探索を構成する前に、探索方法の違い、探索方法で実行できること、および一部の探索方法にある制限について理解する必要があります。  
次のトピックに従って、探索方法を適切に使用するのに役立つ基盤を構築できます。  

-   [System Center Configuration Manager の探索方法について](../../../../core/servers/deploy/configure/about-discovery-methods.md)  

-   [System Center Configuration Manager に使用する探索方法の選択](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md)  

その後、使用しようとしている方法が理解できたら、「[Configure discovery methods for System Center Configuration Manager (System Center Configuration Manager の探索方法の構成)](../../../../core/servers/deploy/configure/configure-discovery-methods.md)」でそれぞれの方法の構成の手引きを探します。  



<!--HONumber=Nov16_HO1-->


