---
title: "移行ソース階層 | System Center Configuration Manager"
description: "System Center Configuration Manager 環境にデータを移行できるように、ソース階層とソース サイトを構成します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccce7cb5-e18f-4337-8adf-2018edca3c00
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 75b1515f85787cefc60d98d6f6affa3a447a39f2


---
# <a name="configuring-source-hierarchies-and-source-sites-for-migration-to-system-center-configuration-manager"></a>System Center Configuration Manager に移行するためのソース階層とソース サイトの構成

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager 環境へのデータの移行を有効にするには、移行するデータが含まれている階層内で、サポートされている Configuration Manager ソース階層と 1 つ以上のソース サイトを構成する必要があります。  

> [!NOTE]  
>  移行操作は、移行先の階層内の最上位サイトで実行されます。 プライマリ子サイトに接続されている Configuration Manager コンソールを使用して移行を構成する場合、構成が中央管理サイトにレプリケートされて、開始されてから、再び接続先のプライマリ サイトにステータスがレプリケートされるまでの時間を考慮する必要があります。  

 ソース階層を指定したりソース サイトを追加したりするときに、以下のセクションの情報と手順を参照してください。 これらの手順を完了すると、移行ジョブを作成して、ソース階層から移行先階層へのデータ移行を開始できます。  

-   [移行用のソース階層の指定](#BKBM_ConfigSrcHierarchy)  

-   [ソース階層の追加のソース サイトの特定](#BKBM_ConfigSrcSites)  

##  <a name="a-namebkbmconfigsrchierarchya-specify-a-source-hierarchy-for-migration"></a><a name="BKBM_ConfigSrcHierarchy"></a> 移行用のソース階層の指定  
 移行先階層にデータを移行するためには、移行するデータが含まれている、サポートされているソース階層を指定する必要があります。 既定では、その階層の最上位サイトがソース階層のソース サイトとなります。 Configuration Manager 2007 階層から移行する場合、最初のソース サイトからデータを収集した後で、移行用の追加のソース サイトを構成できます。 System Center 2012 Configuration Manager または System Center Configuration Manager 階層から移行する場合、ソース階層からデータを移行するために、追加のソース サイトを構成する必要はありません。 これは、これらのバージョンの Configuration Manager では、ソース階層の最上位サイトで使用できる共有データベースを使用するためです。 共有データベースには、移行できるすべての情報が含まれています。  

 Configuration Manager 2007 階層内で移行用のソース階層を指定して、追加のソース サイトを特定するには、次の手順を使用します。  

 移行先階層に接続されている Configuration Manager コンソールを使用して、この手順を実行します。  

#### <a name="to-configure-a-source-hierarchy"></a>ソース階層を構成するには  

1.  Configuration Manager コンソールで、[ **管理**] をクリックします。  

2.  **[管理]** ワークスペースで、 **[移行]**を展開してから **[ソース階層]**をクリックします。  

3.  [ **ホーム** ] タブの [ **移行** ] グループで、[ **ソース階層の指定**] をクリックします。  

4.  [ソース階層の指定 **** ] ダイアログ ボックスで、[ソース階層 ****] から [新しいソース階層 ****] を選択します。  

5.  **[最上位の Configuration Manager サイト サーバー]** には、サポートされているソース階層の最上位サイトの名前または IP アドレスを入力します。  

6.  次の権限を持つソース サイトのアクセス アカウントを指定します。  

    -   ソース サイトのアカウント:ソース階層の指定の最上位サイトの SMS プロバイダーの [読み取り] アクセス許可 ****  

    -   ソース サイトのデータベース アカウント:ソース階層で指定された最上位サイトの SQL Server データベースに対する [ **読み取り** ] および [ **実行** ] アクセス許可。  

     コンピューター アカウントの使用を指定した場合、Configuration Manager では、移行先階層の最上位サイトのコンピューター アカウントを使用します。 このオプションでは、このアカウントが、ソース階層の最上位サイトが存在するドメインの **Distributed COM Users** セキュリティ グループのメンバーであることを確認してください。  

7.  ソース階層と移行先階層間で配布ポイントを共有するには、[ソース サイト サーバーの配布ポイント共有を有効にする] チェック ボックスをオンにします。 **** この時点で配布ポイントの共有を有効にしない場合は、データ収集が完了した後で、ソース サイトの資格情報を編集して有効にできます。  

8.  [ **OK** ] をクリックして構成を保存します。 [データ収集のステータス] ダイアログ ボックスが開いて、データ収集が自動的に開始されます。 ****  

9. データの収集が完了したら、[ **閉じる** ] をクリックして [ **データ収集のステータス** ] ダイアログ ボックスを閉じて構成を完了します。  

##  <a name="a-namebkbmconfigsrcsitesa-identify-additional-source-sites-of-the-source-hierarchy"></a><a name="BKBM_ConfigSrcSites"></a> ソース階層の追加のソース サイトの特定  
 サポートされているソース階層の構成時に、階層の最上位サイトが自動的にソース サイトとして構成され、そのサイトから自動的にデータが収集されます。 実行する次の操作は、ソース階層で実行されている Configuration Manager のバージョンによって異なります。  

-   Configuration Manager 2007 ソース階層では、最初のソース サイトのデータ収集が終了した後で、最初のソース サイトからのみ移行を開始するか、ソース階層から追加のソース サイトを構成できます。 子サイトからのみ使用できるデータを移行するには、Configuration Manager 2007 階層の追加のソース サイトを構成します。 たとえば、子サイトで作成され、ソース階層の最上位サイトで使用できないコンテンツを移行する場合、このコンテンツに関するデータを収集するために、追加のソース サイトを構成できます。  

-   System Center 2012 Configuration Manager または System Center Configuration Manager のソース階層の場合は、追加のソース サイトを構成する必要はありません。 これは、これらのバージョンの Configuration Manager では、ソース階層の最上位サイトで使用できる共有データベースを使用するためです。 共有データベースには、ソース階層のすべてのサイトから移行できるすべての情報が含まれています。 そのため、ソース階層の最上位サイトからデータを移行できます。  

Configuration Manager 2007 ソース階層の追加のソース サイトを構成する場合、ソース階層の最上位から最下位まで、追加のソース サイトを構成する必要があります。 親サイトをソース サイトとして構成してから、その子サイトのいずれかをソース サイトとして構成する必要があります。  

Configuration Manager 2007 ソース階層の追加ソース サイトを構成するには、次の手順を使用します。  

#### <a name="to-identify-additional-source-sites-in-the-source-hierarchy"></a>ソース階層内で追加のソース サイトを特定するには  

1.  Configuration Manager コンソールで、[ **管理**] をクリックします。  

2.  **[管理]** ワークスペースで、 **[移行]**を展開してから **[ソース階層]**をクリックします。  

3.  ソース サイトとして構成するサイトをクリックします。  

4.  [ホーム **** ] タブの [ソース サイト **** ] グループで、[構成 ****  

5.  [ソース サイトの資格情報] ダイアログ ボックスで、ソース サイトのアクセス アカウントに、次のアクセス許可を持っているアカウントを指定します。 ****  

    -   ソース サイトのアカウント:ソース階層の指定の最上位サイトの SMS プロバイダーの [読み取り] アクセス許可 ****  

    -   ソース サイトのデータベース アカウント:ソース階層で指定された最上位サイトの SQL Server データベースに対する [ **読み取り** ] および [ **実行** ] アクセス許可。  

    コンピューター アカウントの使用を指定した場合、Configuration Manager では、移行先階層の最上位サイトのコンピューター アカウントを使用します。 このオプションでは、このアカウントが、ソース階層の最上位サイトが存在するドメインの **Distributed COM Users** セキュリティ グループのメンバーであることを確認してください。  

6.  ソース階層と移行先階層間で配布ポイントを共有するには、[ソース サイト サーバーの配布ポイント共有を有効にする] チェック ボックスをオンにします。 **** この時点で配布ポイントの共有を有効にしない場合は、データ収集が完了した後で、ソース サイトの資格情報を編集して有効にできます。  

7.  [ **OK** ] をクリックして構成を保存します。 [データ収集のステータス] ダイアログ ボックスが開いて、データ収集が自動的に開始されます。 ****  

8.  データ収集が終了したら、[閉じる] をクリックして構成を完了します。 ****  



<!--HONumber=Nov16_HO1-->


