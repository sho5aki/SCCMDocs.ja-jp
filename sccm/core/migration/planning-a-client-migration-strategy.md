---
title: "クライアント移行計画 | System Center Configuration Manager"
description: "ソース階層からクライアントを System Center Configuration Manager の移行先階層に移行するタスクについて説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e27b0b7-7bd3-45cd-bc99-9c991606c637
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 6044f9b8116687fca80deeea87abd4652f773db0


---
# <a name="planning-a-client-migration-strategy-in-system-center-configuration-manager"></a>System Center Configuration Manager でのクライアント移行戦略の計画

*適用対象: System Center Configuration Manager (Current Branch)*

ソース階層のクライアントを System Center Configuration Manager 移行先階層に移行するには、2 つのタスクを実行する必要があります。 クライアントに関連付けられているオブジェクトを移行してから、ソース階層のクライアントを移行先階層に再割り当てする必要があります。 クライアントを移行するときに使用できるように、まずオブジェクトを移行します。 クライアントに関連付けられているオブジェクトを移行するには、移行ジョブを使用します。 クライアントに関連付けられているオブジェクトの移行方法については、「[System Center 2012 Configuration Manager の移行ジョブ戦略の計画](../../core/migration/planning-a-migration-job-strategy.md)」を参照してください。  

 移行先階層へのクライアントの移行を計画する際には、以下のセクションを参考にしてください。  

-   [移行先階層へのクライアントの移行を計画する](#Planning_for_Client_Agent_Migration)  

-   [移行時にクライアントに保持されるデータの処理の計画](#Planning_for_Client_Data_Migration)  

-   [移行時のインベントリとコンプライアンス対応データを計画する](#Planning_for_Inventory_data_migration)  

##  <a name="a-nameplanningforclientagentmigrationa-plan-to-migrate-clients-to-the-destination-hierarchy"></a><a name="Planning_for_Client_Agent_Migration"></a> 移行先階層へのクライアントの移行を計画する  
 ソース階層からクライアントを移行すると、移行先階層の製品バージョンに一致するように、クライアント コンピューターのクライアント ソフトウェアが更新されます。  

-   **Configuration Manager 2007 のソース階層:** サポートされているバージョンの Configuration Manager を実行しているソース階層のクライアントを移行すると、クライアント ソフトウェアは移行先階層のクライアント バージョンにアップグレードされます。  

-   ** System Center 2012 Configuration Manager 以降のソース階層:** 同じ製品バージョンの階層間でクライアントを移行する場合、クライアント ソフトウェアは変更またはアップグレードされません。 代わりに、クライアントがソース階層から移行先階層内のサイトに再割り当てされます。  

    > [!NOTE]  
    >  階層の製品バージョンが、移行先階層への移行でサポートされていない場合、ソース階層のすべてのサイトとクライアントを互換性のある製品バージョンにアップグレードします。 ソース階層をサポートされる製品バージョンにアップグレードした後で、階層間の移行を実行できます。 詳細については、「[移行がサポートされている Configuration Manager のバージョン](../../core/migration/prerequisites-for-migration.md#BKMK_supportedmigrationversions)」トピックの「 [Prerequisites for migration in System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md)」(移行に必要な構成) セクションを参照してください。  

クライアントの移行を計画する際には、次の情報を参考にしてください。  

-   ソース サイトのクライアントを移行先サイトにアップグレードまたは再割り当てする場合、移行先階層でクライアント展開がサポートされているクライアント展開方法を使用できます。 標準的なクライアントの展開方法には、クライアント プッシュ インストール、ソフトウェア配布、グループ ポリシー、ソフトウェアの更新に基づいたクライアントのインストールなどがあります。 詳細については、「[System Center Configuration Manager でのクライアントのインストール方法](../../core/clients/deploy/plan/client-installation-methods.md)」を参照してください。  

-   ソース階層のクライアント ソフトウェアを実行するデバイスが、移行先階層の最小ハードウェア要件を満たし、移行先階層の Configuration Manager のバージョンでサポートされているオペレーティング システムを実行していることを確認します。  

-   クライアントを移行する前に、移行ジョブを実行して、移行先階層でクライアントによって使用される情報を移行します。  

-   移行先階層で展開が不要に再実行されないように、アップグレードするクライアントには展開の実行履歴が保持されます。  

    -   Configuration Manager 2007 クライアントには、公開通知の実行履歴が保持されます。  

    -   System Center 2012 Configuration Manager または System Center Configuration Manager のクライアントで、展開の実行履歴が保持されます。  

-   ソース階層内のサイトからクライアントを移行する際には、ユーザーが自由に順番を指定できます。 ただし、一度に多数のクライアントを移行するのではなく、段階的に少数のクライアントを移行することをお勧めします。 段階別に移行を行うことで、新たにアップグレードされた各クライアントが初期の全インベントリとコンプライアンス対応のデータを割り当てられたサイトに送信する際に、必要となるネットワーク帯域幅とサーバー処理量が低減されます。  

-   Configuration Manager 2007 クライアントを移行すると、クライアント コンピューターから既存のクライアント ソフトウェアがアンインストールされて、新しいクライアント ソフトウェアがインストールされます。  

-   Configuration Manager では、App-V クライアント バージョン4.6 SP1 以降のバージョンの App-V クライアントがインストールされた Configuration Manager 2007 クライアントは移行できません。  

クライアントの移行プロセスは、Configuration Manager コンソールの [**管理**] ワークスペースにある [**移行**] ノードで監視できます。  

クライアントを移行先階層に移行した後は、ソース階層を使用してそのデバイスを管理できなくなるため、ソース階層からクライアントを削除することを検討する必要があります。 これは階層の移行時に必須ではありませんが、移行済みクライアントがソース階層レポートに表示されたり、移行中に 2 つの階層のリソースが不正確にカウントされたりするのを防止できます。 たとえば、移行済みクライアントがソース サイトのデータベースに残っている場合、ソフトウェア更新プログラム レポートを実行すると、そのコンピューターが現在は移行先階層で管理されているにもかかわらず、誤って管理対象外リソースとして表示されることがあります。  

##  <a name="a-nameplanningforclientdatamigrationa-plan-to-handle-data-maintained-on-clients-during-migration"></a><a name="Planning_for_Client_Data_Migration"></a> 移行時にクライアントに保持されるデータの処理の計画  
ソース階層のクライアントを移行先階層に移行すると、デバイスに保持される情報と、移行後にデバイスで使用できなくなる情報があります。  

以下の情報はクライアント デバイスに保持されます。  

-   一意識別子 (GUID) - これにより、クライアントが Configuration Manager データベース内の該当情報に関連付けられます。  

-   開示通知履歴または展開履歴 - これにより、移行先階層での不要な開示情報または展開の再実行が防止されます。  

以下の情報はクライアント デバイスに保持されません。  

-   クライアントのキャッシュ内のファイル。 クライアントでソフトウェアのインストールのためにこれらのファイルが必要となる場合は、移行先階層から再度ダウンロードされます。  

-   まだ実行されていない開示通知または展開に関する、ソース階層の情報。 移行後にクライアントで開示通知または展開を実行する必要がある場合は、これらを移行先階層内のクライアントに再展開する必要があります。  

-   インベントリに関する情報。 クライアントの移行後にクライアントが、移行先階層内の割り当てられたサイトにこの情報を再送信し、新しいクライアント データが生成されます。  

-   コンプライアンス対応データ。 クライアントの移行後にクライアントが、移行先階層内の割り当てられたサイトにこの情報を再送信し、新しいクライアント データが生成されます。  

クライアントの移行時に、Configuration Manager クライアント レジストリに保存されている情報とファイル パスは保持されません。 移行後、これらの設定を再び適用します。 標準設定には以下が含まれます。  

-   電源設定  

-   ログ設定  

-   ローカル ポリシー設定  

さらに、一部のアプリケーションの再インストールが必要な場合もあります。  

##  <a name="a-nameplanningforinventorydatamigrationa-plan-for-inventory-and-compliance-data-during-migration"></a><a name="Planning_for_Inventory_data_migration"></a> 移行時のインベントリとコンプライアンス対応データを計画する  
移行先階層にクライアントを移行するときに、クライアントのインベントリとコンプライアンス対応データは保存されません。 代わりに、割り当てられたサイトにクライアントから情報が初めて送信されたときに、この情報が移行先階層で再作成されます。 必要とされるネットワーク帯域幅とサーバーの処理量を低減するため、一度に多数のクライアントを移行する代わりに、段階的に少数のクライアントを移行するよう考慮してください。  

 また、ソース階層からハードウェア インベントリのカスタム設定を移行することはできません。 これらは、移行とは別に移行先階層に導入する必要があります。 カスタム ハードウェア インベントリを拡張する方法については、「[Configuration Manager でハードウェア インベントリを構成する方法](../../core/clients/manage/inventory/configure-hardware-inventory.md)」を参照してください。  



<!--HONumber=Nov16_HO1-->


