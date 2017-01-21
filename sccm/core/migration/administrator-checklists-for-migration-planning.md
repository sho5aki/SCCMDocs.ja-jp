---
title: "移行チェックリスト | System Center Configuration Manager"
description: "監理者チェックリストを利用すると、System Center Configuration Manager への移行方針を計画するときに便利です。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 295fdf07-93cc-490c-acdd-ce3ee88cb36f
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: f3912de04aa3e6196137a7034753013c35180d64


---
# <a name="administrator-checklists-for-migration-planning-in-system-center-configuration-manager"></a>System Center Configuration Manager での移行計画の管理者チェックリスト

*適用対象: System Center Configuration Manager (Current Branch)*

次の監理者チェックリストを利用すると、System Center Configuration Manager への移行方針を計画するときに便利です。  

-   [移行計画の管理者チェックリスト](#Checklist_Migraiton_Planning)  

-   [階層移行の管理者チェックリスト](#Checklist_Hierarchy_for_migration)  

-   [移行の管理者チェックリスト](#Checklisit_Migration)  

##  <a name="a-namechecklistmigraitonplanninga-administrator-checklist-for-migration-planning"></a><a name="Checklist_Migraiton_Planning"></a> 移行計画の管理者チェックリスト  
 移行前の計画の手順については、次のチェックリストを使用してください。  

-   **現在の環境を評価する。**  

     ソース階層が満たしている既存の業務要件を特定し、移行先階層で引き続きそれらの要件を満たすための計画を立てます。  

-   **使用する Configuration Manager のバージョンで使用できる機能と変更内容を確認し、その情報を移行先階層の設計に役立てる。**  

    詳細については、「 [Fundamentals of System Center Configuration Manager](../../core/understand/fundamentals.md) 」および「 [What's new in System Center Configuration Manager](../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md)」をご覧ください。  


-   **役割に基づく管理に使用する管理セキュリティ モデルを決定する。**  

    詳細については、「[System Center Configuration Manager のロール ベース管理の基礎](../../core/understand/fundamentals-of-role-based-administration.md)」をご覧ください。  

-   **ネットワークと Active Directory のトポロジを評価する。**  

    既存のドメイン構造とネットワーク トポロジを見直し、これが階層の設計と移行タスクに及ぼす影響について検討します。  

-   **移行先階層の設計を完成させる。**  

    中央管理サイト、プライマリ サイト、セカンダリ サイト、およびコンテンツの配布オプションの配置について決定します。  

-   **移行先階層内のサイトとサイト サーバーに使用するコンピューターに現在の階層をマッピングする。**  

    サイトおよびサイト システム サーバーが移行先階層で使用するコンピューターを特定し、現在および将来の動作要件を満たすために十分な容量があることを確認します。  

-   **オブジェクトの移行方法を計画する。**  

    サイトの境界、コレクション、アドバタイズ、および展開を含め、複数のオブジェクトを移行するために、利用可能な移行ジョブの使用を計画します。 詳細については、「 [Plann」の「g a Migration Job Strategy 」の「 System Center Configuration Manager](../../core/migration/planning-a-migration-job-strategy.md#Types_of_Migration) 」の「 [Plann」の「g a migration job strategy 」の「 System Center Configuration Manager](../../core/migration/planning-a-migration-job-strategy.md)」を参照してください。  

    Configuration Manager は、選択したオブジェクトのみを移行します。 移行先階層に必要なオブジェクトが移行されない場合は、そのオブジェクトを移行先階層で再作成する必要があります。  

    移行ジョブの構成時に、移行可能なオブジェクトが表示されます。  

-   **クライアントの移行方法を計画する。**  

    クライアントを移行先階層に移行するときに、ネットワーク帯域幅とサーバー処理要件を制限する制御可能なアプローチを使用してクライアントを移行するように計画します。 クライアント移行戦略の計画の詳細については、「 [Planning a client migration strategy in System Center Configuration Manager](../../core/migration/planning-a-client-migration-strategy.md)」を参照してください。  

-   **インベントリとコンプライアンス データを計画する。**  

    Configuration Manager は、ハードウェア インベントリ、ソフトウェア インベントリ、ソフトウェア更新プログラムまたはクライアントに必要な構成管理のコンプライアンス対応データの移行はサポートしません。  

    この場合、クライアントが移行先階層内の新しいサイトに移行し、これらの構成に関するポリシーを受信した後に、クライアントからクライアントに割り当てられたサイトにその情報を送信します。 この操作で、移行先サイトのデータベースに現在のインベントリとコンプライアンス データが設定されます。  

-   **ソース階層からの移行完了を計画する。**  

    オブジェクトとクライアントを移行するタイミングを決定します。 移行が完了したら、ソース階層内のソース サーバーの使用停止を計画できます。  

##  <a name="a-namechecklisthierarchyformigrationa-administrator-checklist-for-hierarchy-migration"></a><a name="Checklist_Hierarchy_for_migration"></a> 階層移行の管理者チェック リスト  
移行の開始前に移行先階層を計画する際には、次のチェックリストを参考にしてください。  

-   **移行先階層で使用するコンピューターを特定する。**  

    Configuration Manager は、Configuration Manager 2007 インフラストラクチャからの一括アップグレードに対応していません。 代わりに、移行を利用し、Configuration Manager 2007 から System Center Configuration Manager にアップグレードします。 この場合はサイド バイ サイド展開を使用し、新しいコンピューターに System Center Configuration Manager をインストールする必要があります。  

    同様に、別の System Center Configuration Manager 階層から移行するときには、ソース階層への並列展開として新しい移行先階層をインストールする必要があります。  

-   **移行先階層を作成する。**  

    移行準備のために、プライマリ サイトを含む System Center Configuration Manager 移行先階層をインストールし、構成します。 たとえば、  

    -   中央管理サイトをインストールしてから、少なくとも 1 つの子プライマリをインストールする  

    -   中央管理サイトを使用する予定がない場合、スタンドアロン プライマリをインストールする  

-   **ソフトウェア更新プログラムに関連する情報を移行する場合、移行先階層内でソフトウェアの更新ポイントを構成し、ソフトウェア更新プログラムを同期する。**  

    ソース階層からソフトウェア更新プログラムの情報を移行するには、先に移行先階層内でソフトウェア更新プログラムを構成し、同期しておく必要があります。  


-   **移行先階層に追加のサイト システムの役割をインストールして構成する。**  

    追加のサイト システムの役割と必要とされるサイト システムを構成します。  

-   **移行先階層の運用機能を確認する。**  

    次の点を確認します。  

    -   移行先階層に複数のサイトが含まれる場合、サイト間のデータベース レプリケーションが機能することを確認します。 データベースのレプリケーションはスタンドアロン プライマリ サイトでは使用できません。  

    -   すべてのインストール済みサイト システムの役割が機能することを確認します。  

    -   移行先階層にインストールする Configuration Manager クライアントが、割り当て済みサイトと正常に通信できることを確認します。  


##  <a name="a-namechecklisitmigrationa-administrator-checklist-for-migration"></a><a name="Checklisit_Migration"></a> 移行の管理者チェックリスト  
ソース階層から移行先階層にデータを移行する際には、次のチェックリストを参考にしてください。  

-   **移行先階層で移行を有効にする。**  

    ソース階層の最上位サイトを指定してソース階層を構成します。 ソース サイトの指定の詳細については、「 [Planning a source hierarchy strategy in System Center Configuration Manager](../../core/migration/planning-a-source-hierarchy-strategy.md)」を参照してください。  

-   **ソース階層が Configuration Manager 2007 SP2 を実行している場合、ソース階層で追加サイトを選択し、構成する。**  

    Configuration Manager 2007 SP2 ソース階層内にデータを収集する追加サイトがある場合、各サイトでデータ収集のために資格情報を構成する必要があります。 各ソース サイトを構成すると、データ収集プロセスが直ちに開始され、移行期間中は、サイトのデータ収集を手動で停止するまで継続されます。 データ収集により、前回のデータ収集プロセス以降に更新されたオブジェクトや新しく追加されたオブジェクトが確実にソース階層から移行できるようになります。  

    > [!NOTE]  
    >  ソース階層で System Center 2012 Configuration Manager 以降が実行されている場合、追加のソース サイトを構成する必要はありません。  

-   **配布ポイントの共有を構成する。**  

    2 つの階層間で配布ポイントを共有することで、移行するオブジェクトのコンテンツを、移行先階層内のクライアントが使用できるようになります。 こうすることで、両方の階層内のクライアントが同じコンテンツを引き続き使用できるようになり、データ収集を停止して移行を完了するまで、このコンテンツを管理することができます。  

    共有配布ポイントの詳細については、「 *Share Distribution Points Between Source and Destination Hierarchies* 」トピックの「 [Planning a content deployment migration strategy in System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md) 」セクションを参照してください。  

-   **ソース階層内のクライアントと関連付けられているオブジェクトを移行するための移行ジョブを作成して実行する。**  

    階層間でオブジェクトを移行する移行ジョブを作成します。 個々の移行ジョブに必要な構成は、ジョブが移行するデータに応じて変わります。  

    たとえば、コンテンツを移行する場合、使用する移行ジョブにかかわらず、移行先階層内のサイトを、そのコンテンツの管理のために割り当てる必要があります。 この割り当てられたサイトは、コンテンツの元のソース ファイルがある場所にアクセスします。また、このサイトには、そのコンテンツを移行先階層内の配布ポイントに配布する役割があります。  

    詳細については、「 [Create and Edit Migration Jobs for System Center Configuration Manager](../../core/migration/operations-for-migration.md#create_edit_migration_jobs) 」トピックの「 [Operations for migrating to System Center Configuration Manager](../../core/migration/operations-for-migration.md) 」セクションを参照してください。  

-   **クライアントを移行先階層に移行する。**  

    クライアントの移行プロセスは、移行シナリオによって異なります。  

    -   移行先階層とクライアント バージョンが同じではないクライアントを移行する場合、クライアント ソフトウェアをアップグレードする必要があります。 アップグレードには、現在の Configuration Manager クライアントを削除してから、移行先サイトと一致する新しいクライアント バージョンをインストールする必要があります。  

    -   移行先階層のバージョンとクライアント バージョンが一致するクライアントを移行する場合、クライアントのアップグレードや再インストールは必要ありません。 この場合、クライアントは移行先階層内のプライマリ サイトに再び割り当てられます。  

    クライアントを移行先階層に移行すると、クライアントは、その移行先階層に移行済みのデータと関連付けられます。  

    詳細については、「 [Planning a client migration strategy in System Center Configuration Manager](../../core/migration/planning-a-client-migration-strategy.md)」をご覧ください。  

-   **共有配布ポイントをアップグレードするか、または再び割り当てる。**  

    ソース階層のクライアントをサポートする必要がなくなった場合、共有配布ポイントを Configuration Manager 2007 ソース サイトからアップグレードするか、共有配布ポイントを System Center 2012 Configuration Manager または System Center Configuration Manager ソース サイトから再割り当てできます。 配布ポイントをアップグレードまたは再割り当てすると、サイト システムの役割は、移行先階層内のプライマリ サイトに転送され、配布ポイントは、ソース階層内のソース サイトから削除されます。 共有配布ポイントをアップグレードまたは再割り当てする場合、コンテンツは配布ポイント コンピューターに残りますが、コンテンツを移行先階層内の新しい配布ポイントに再展開する必要はありません。  

    さらに、セカンダリ サイト サーバーに併置されている Configuration Manager 2007 の配布ポイントをアップグレードすることもできます。 この操作により、セカンダリ サイトが削除され、移行先階層の配布ポイントが唯一の配布ポイントになります。  

    共有配布ポイントの詳細については、「 [Share Distribution Points Between Source and Destination Hierarchies](../../core/migration/planning-a-content-deployment-migration-strategy.md#about_shared_dps_in_migrations) 」トピックの「 [Planning a content deployment migration strategy in System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md) 」セクションを参照してください。  

-   **移行の完了:**  

    ソース階層内のすべてのサイトからデータとクライアントを移行し、該当する配布ポイントをアップグレードしたら、移行を完了できます。 移行を完了するには、ソース階層内の各ソース サイトについてデータ収集を停止します。 次に不要な移行情報を削除し、ソース階層インフラストラクチャの使用を停止することができます。 詳細については、「 [Planning to complete migration in System Center Configuration Manager](../../core/migration/planning-to-complete-migration.md)」をご覧ください。  



<!--HONumber=Nov16_HO1-->


