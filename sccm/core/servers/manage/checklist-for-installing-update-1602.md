---
title: "1602 のチェックリスト | System Center Configuration Manager"
description: "System Center Configuration Manager をバージョン 1511 からバージョン 1602 に更新する前に、実行するアクションについて説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b63ef197-01f0-4894-b929-5ef8403c5195
caps.latest.revision: 13
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 75f5ddfdc84185ee27bf60416e54d37295928156


---
# <a name="checklist-for-installing-update-1602-for-system-center-configuration-manager"></a>System Center Configuration Manager の更新プログラム 1602 をインストールするためのチェックリスト

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager をバージョン 1511 からバージョン 1602 に更新する前に、次の情報と、更新を開始する前に実行するアクションのチェックリストを確認します。  

 **更新プログラム 1602 のインストールについて:**  

 更新プログラム 1602 は、階層の最上位サイトのみにインストールすることができます。 つまり、中央管理サイトがある場合はそこからインストールを開始します。そうでない場合は、スタンドアロン プライマリ サイトからインストールを開始します。  

-   中央管理サイトで更新プログラムのインストールが完了したら、子プライマリ サイトで更新プログラムが自動的にインストールされます。 メンテナンス期間を使用して、サイトが更新プログラムをインストールするタイミングを制御できます。 1602 更新プログラムのリリース以降、メンテナンス期間はサービス時間帯に名前変更されています。 詳細については、「[Service Windows for site servers (サイト サーバーのサービス時間帯)](../../../core/servers/manage/install-in-console-updates.md#bkmk_ServiceWindow)」を参照してください。  

-   プライマリ親サイトが更新プログラムのインストールを完了したら、Configuration Manager コンソール内からセカンダリ サイトを手動で更新する必要があります。 セカンダリ サイト サーバーの自動更新はサポートされていません。  

サイト サーバーが更新プログラムをインストールすると、サイト サーバーにインストールされたサイト システムの役割と、リモート コンピューターにインストールされたサイト システムの役割が自動的に更新されます。 したがって、更新プログラムをインストールする前に、各サイト システム サーバーが新しい更新プログラムのバージョンの操作の新しい前提条件をすべて満たしていることを確認してください。  

更新の完了後に Configuration Manager コンソールを初めて使用する場合、そのコンソールの更新を求められます。  これを行うには、コンソールをホストするコンピューターで Configuration Manager セットアップを実行し、コンソールを更新するオプションを選択する必要があります。 コンソールへの更新プログラムのインストールを遅らせないことをお勧めします。  

 **チェックリスト:**  

 **すべてのサイトがサポートされているバージョンの System Center Configuration Manager を実行することを確認する:**  更新プログラム 1602 のインストールを開始するには、階層内の各サイト サーバーが、System Center Configuration Manager バージョン 1511 を実行する必要があります。  

 **サイト システム サーバーにインストールされた .NET のバージョンを確認する:** .NET Framework 4.5 以降がまだインストールされていない場合、サイトで更新プログラム 1602 がインストールされると、Configuration Manager によって、次のいずれかのサイト システムの役割をホストする各コンピューターに .NET Framework 4.5.2 が自動的にインストールされます。  

-   登録プロキシ ポイント  

-   登録ポイント  

-   管理ポイント  

-   サービス接続ポイント  

このインストールにより、サイト システム サーバーが再起動保留中の状態になり、Configuration Manager コンポーネント ステータス ビューアーにエラーが報告される場合があります。 さらに、サーバーが再起動されるまで、サーバー上の .NET アプリケーションでランダムにエラーが発生する場合があります。  

 詳細については、「[サイトとサイト システムの前提条件](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)」を参照してください。  

 **サイトと階層の状態を確認して、解決されていない問題がないことを確認する:** サイトを更新する前に、サイト サーバー、サイト データベース サーバー、リモート コンピューターにインストールされているサイト システムの役割で、運用上のすべての問題を解決します。 運用上の問題があると、サイトの更新が失敗する可能性があります。  
 詳細については、「[System Center Configuration Manager のアラートとステータス システムの使用](../../../core/servers/manage/use-alerts-and-the-status-system.md)」を参照してください。  

 **サイト間でファイルとデータのレプリケーションを確認する:**  サイト間のファイルとデータベースのレプリケーションが機能していて最新の状態であることを確認します。 遅延またはバックログにより、円滑で正常な更新が行われない場合があります。    
データベース レプリケーションには、更新プログラムを開始する前に問題を解決するために、レプリケーション リンク アナライザーを使用できます。    
 詳細については、「   
「[System Center Configuration Manager での階層とレプリケーション インフラストラクチャの監視](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA)」トピックの「[レプリケーション リンク アナライザーについて](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md)」。  

 **サイト、サイト データベース サーバー、リモートのサイト システムの役割をホストするコンピューターのオペレーティング システムに適用できる、重要な更新プログラムすべてをインストールする:** Configuration Manager に更新プログラムをインストールする前に、該当する各サイト システムの重要な更新プログラムをすべてインストールします。 更新のインストール時に再起動が必要な場合は、アップグレードを開始する前に該当するコンピューターを再起動します。  

 **プライマリ サイトで管理ポイントのデータベース レプリカを無効にする:** Configuration Manager では、有効になっている管理ポイントのデータベースのレプリカを持つプライマリ サイトを正常に更新することはできません。 次の操作を行う前に、データベースのレプリケーションを無効にしてください。  

-   データベースのアップグレードをテストするためにサイト データベースのバックアップを作成する  

-   Configuration Manager の更新プログラムをインストールする  

詳細については、次を参照してください:   
[System Center Configuration Manager の管理ポイントのデータベース レプリカ](../../../core/servers/deploy/configure/database-replicas-for-management-points.md)  

 **NLB を使うソフトウェアの更新ポイントを再構成する:** Configuration Manager では、ネットワーク負荷分散 (NLB) クラスターを使用してソフトウェアの更新ポイントをホストしているサイトを更新できません。  
ソフトウェアの更新ポイントに NLB クラスターを使用している場合、PowerShell を使用して NLB クラスターを削除してください    

 詳細については、「[System Center Configuration Manager でのソフトウェア更新プログラムの計画](../../../sum/plan-design/plan-for-software-updates.md)」を参照してください。  

 **各サイトの更新プログラムのインストールの実行中に、そのサイトのすべてのサイト メンテナンス タスクを無効にする:** 更新プログラムをインストールする前に、更新プロセスがアクティブな期間中に実行されるサイト メンテナンス タスクをすべて無効にします。 次のタスクが含まれますが、これらのタスクに限定されません。  

-   サイト サーバーのバックアップ  

-   期限切れのクライアント操作を削除  

-   期限切れの探索データの削除  

更新プログラムのインストール中にサイト データベースのメンテナンス タスクを実行すると、更新プログラムのインストールが失敗することができます。 タスクを無効にする前に、更新プログラムをインストールした後で構成を復元できるように、タスクのスケジュールを記録してください。  
 詳細については、「[System Center Configuration Manager のメンテナンス タスク](../../../core/servers/manage/maintenance-tasks.md)」および「[System Center Configuration Manager のメンテナンス タスクのリファレンス](../../../core/servers/manage/reference-for-maintenance-tasks.md)」を参照してください。  

 **中央管理サイトとプライマリ サイトでサイト データベースのバックアップを作成する:** サイトを更新する前に、サイト データベースをバックアップして、障害復旧に使用する正常なバックアップがあるようにします。   
詳細については、「 [Backup and recovery for System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md)」をご覧ください。  

 **カスタマイズされた Configuration.mof ファイルをバックアップする:** ハードウェア インベントリで使用するデータ クラスを定義するためにカスタマイズされた Configuration.mof ファイルを使用する場合は、サイトを更新する前にこのファイルのバックアップを作成します。 その後、更新の後に、バージョン 1602 サイトにこのファイルを復元します。 サイトを更新するときに、現在のファイルは、ファイルの元の (既定の) バージョンで上書きされます。 このファイルの使用の詳細については、「[System Center Configuration Manager でのハードウェア インベントリの拡張方法](../../../core/clients/manage/inventory/extend-hardware-inventory.md)」を参照してください。  

 **最新のサイト データベース バックアップのコピーで、データベースのアップグレードをテストする:** System Center Configuration Manager の中央管理サイトまたはプライマリ サイトを更新する前に、サイト データベースのコピーでサイト データベースのアップグレード処理をテストします。  

-   サイトのアップグレード時にサイト データベースが変更される可能性があるため、サイト データベースのアップグレード処理をテストしておく必要があります  

-   データベースのアップグレード テストは必須ではありませんが、テストによって、実稼働データベースが影響を受ける前に、アップグレードの問題を特定することができます  

-   サイト データベースのアップグレードに失敗すると、サイト データベースが運用不可能になり、機能を復元するにはサイトの回復が必要になることがあります  

-   サイト データベースは階層内のサイト間で共有されますが、各サイトをアップグレードする前に、該当する各サイトのデータベースをテストする計画を立ててください  

-   プライマリ サイトで管理ポイントにデータベース レプリカを使う場合、サイト データベースのバックアップを作成する前にレプリケーションを無効にします  

Configuration Manager では、セカンダリ サイトのバックアップとセカンダリ サイト データベースのテスト アップグレードのいずれもサポートされていません。   
実稼働サイト データベースでテスト データベースのアップグレードを実行することはサポートされていません。 実行するとサイト データベースが更新され、サイトが機能しなくなる可能性があります。 詳細については、「[System Center Configuration Manager へのアップグレード](../../../core/servers/deploy/install/upgrade-to-configuration-manager.md)」の「[サイト データベースのアップグレードをテストする](../../../core/servers/deploy/install/upgrade-to-configuration-manager.md#bkmk_test)」セクションを参照してください。  

 **クライアントのパイロット運用を計画する:** クライアントを更新する更新プログラムをインストールすると、すべてのアクティブなクライアントを展開してアップグレードする前に、実稼働前環境でその新しいクライアントの更新プログラムをテストできます。   
 このオプションを活用するには、更新プログラムのインストールを開始する前に、実稼働前環境の自動アップグレードをサポートするサイトを構成する必要があります。 詳細については、次を参照してください。「[System Center Configuration Manager でのクライアントのアップグレード](../../../core/clients/manage/upgrade/upgrade-clients.md)」および   
[System Center Configuration Manager で実稼働前コレクションのクライアント アップグレードをテストする方法](../../../core/clients/manage/upgrade/test-client-upgrades.md)  

 **メンテナンス期間の使用を計画**  
 **して、メンテナンス期間の使用を計画して、サイト サーバーが更新プログラムをインストールするタイミングを制御する:** メンテナンス期間を使用して、プライマリ サイト サーバーに適用される、そのサイトに対する更新プログラムをインストールできる期間を定義することができます。   
これは、階層内のサイトが更新プログラムをインストールするタイミングの制御に役立ちます。   
1602 更新プログラムのリリース以降、メンテナンス期間はサービス時間帯に名前変更されています。 詳細については、「[Service Windows for site servers (サイト サーバーのサービス時間帯)](../../../core/servers/manage/install-in-console-updates.md#bkmk_ServiceWindow)」を参照してください。  

 **セットアップ前提条件チェッカーを実行する:**  1602 更新プログラムをインストールする前に、更新プログラムのインストールとは別に前提条件チェッカーを実行することができます。 サイトへの更新プログラムのインストールド時に、前提条件チェッカーが再度実行されます。  
詳細については、「[System Center Configuration Manager の更新プログラム](../../../core/servers/manage/updates.md)」トピックの「**手順 3: 更新プログラムをインストールする前の前提条件チェッカーの実行**」を参照してください。  

> [!IMPORTANT]  
>  前提条件チェッカーを更新プログラムの一部として、または単独で実行すると、サイト メンテナンス タスクに使用される一部の製品ソース ファイルが更新されます。 このため、前提条件チェッカーを実行した後で、1602 更新プログラムをインストールする前に、サイト メンテナンス タスクを実行する必要がある場合は、サイト サーバーの CD.Latest フォルダーから **Setupwfe.exe** (Configuration Manager セットアップ) を実行する必要があります。  

 **サイトを更新する:** 階層の更新プログラムのインストールを開始する準備が整いました。  
  更新プログラムをインストールするプロセス、およびサイトのコンポーネントとサイト システムの役割を再インストールするアクションが業務に及ぼす影響が少ない場合は、各サイトの通常業務時間外に更新プログラムをインストールする計画を立てることをお勧めします。 詳細については、「[System Center Configuration Manager の更新プログラム](../../../core/servers/manage/updates.md)」を参照してください。  

## <a name="see-also"></a>関連項目  
 [System Center Configuration Manager の更新プログラム](../../../core/servers/manage/updates.md)



<!--HONumber=Nov16_HO1-->


