---
title: "サイトのアンインストール | System Center Configuration Manager"
description: "System Center Configuration Manager サイトをアンインストールする必要がある場合は、以下の詳細情報をガイドとして使用します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d466edd2-97f0-44c1-a73e-d71abbdbf4a8
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: db203f6b8b76df28b2cd03f5ebd931c520294ba6


---
# <a name="uninstall-sites-and-hierarchies-in-system-center-configuration-manager"></a>System Center Configuration Manager でのサイトと階層のアンインストール

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager サイトをアンインストールする必要がある場合は、以下の詳細情報をガイドとして使用します。  

複数のサイトが含まれる階層の使用を停止するには、削除する順序が重要です。  

-   階層の最下位のサイトから上方向へ順にアンインストールを進めます。  

-   プライマリ サイトに接続されているセカンダリ サイトを最初に削除します。  

-   その後、プライマリ サイトを削除します。  

-   すべてのプライマリ サイトを削除したら、中央管理サイトをアンインストールできます。  


##  <a name="a-namebkmkremovesecondarysitea-remove-a-secondary-site-from-a-hierarchy"></a><a name="BKMK_RemoveSecondarysite"></a> 階層からのセカンダリ サイトの削除  
セカンダリ サイトを新しい親プライマリ サイトに移動したり再割り当てしたりすることはできません。 階層からセカンダリ サイトを削除するには、直接の親サイトから削除する必要があります。 Configuration Manager コンソールのセカンダリ サイトの削除ウィザードを使用して、セカンダリ サイトを削除します。 セカンダリ サイトを削除するときに、セカンダリ サイトを削除するのかアンインストールするのかを選択する必要があります。  

-   **セカンダリ サイトのアンインストール**: ネットワークからアクセスできる、機能しているセカンダリ サイトを削除するには、このオプションを使用します。 このオプションを使用すると、セカンダリ サイト サーバーから Configuration Manager がアンインストールされてから、Configuration Manager 階層からサイトとサイト リソースのすべての情報が削除されます。 Configuration Manager によってセカンダリ サイトのインストールの一部として SQL Server Express がインストールされた場合は、セカンダリ サイトのアンインストール時に Configuration Manager によって SQL Express がアンインストールされます。 セカンダリ サイトのインストール前に SQL Server Express がインストールされた場合は、Configuration Manager によって SQL Server Express はアンインストールされません。  

-   **セカンダリ サイトの削除**: このオプションは、次のいずれかが当てはまる場合に使用します。  

    -   セカンダリ サイトのインストールが失敗した  

    -   アンインストール後に、セカンダリ サイトが引き続き Configuration Manager コンソールに表示される  

    このオプションを使用すると、Configuration Manager 階層からサイトとサイト リソースのすべての情報が削除されますが、Configuration Manager はセカンダリ サイト サイバーにインストールされたままになります。  

    > [!NOTE]  
    >  階層のメンテナンス ツールと **/DELSITE** オプションを使用して、セカンダリ サイトを削除することもできます。 詳細については、「[System Center Configuration Manager の階層のメンテナンス ツール (Preinst.exe)](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md)」を参照してください。  

#### <a name="to-uninstall-or-delete-a-secondary-site"></a>セカンダリ サイトをアンインストールまたは削除するには  

1.  セットアップを実行する管理ユーザーが次のセキュリティ権限を持っていることを確認します。  

    -   セカンダリ サイト コンピューターの管理者権限  

    -   プライマリ サイトがリモートの場合は、そのリモート サイト データベース サーバーのローカル管理者権限  

    -   親プライマリ サイトのインフラストラクチャ管理者または完全な権限を持つ管理者のセキュリティ ロール  

    -   セカンダリ サイトのサイト データベースの sysadmin 権限  

2.  Configuration Manager コンソールで、[ **管理**] をクリックします。  

3.  [ **管理** ] ワークスペースで [ **サイトの構成**] を展開して、[ **サイト**] をクリックします。  

4.  削除するセカンダリ サイト サーバーを選択します。  

5.  [ **ホーム** ] タブの [ **サイト** ] グループで、[ **削除**] をクリックします。  

6.  [ **全般** ] ページで、セカンダリ サイトをアンインストールするのか削除するのかを選択してから、[ **次へ**] をクリックします。  

7.  [ **概要** ] ページで、設定を確認してから [ **次へ**] をクリックします。  

8.  [ **完了** ] ページで [ **閉じる** ] をクリックして、ウィザードを閉じます。  

##  <a name="a-namebkmkuninstallprimarya-uninstall-a-primary-site"></a><a name="BKMK_UninstallPrimary"></a> プライマリ サイトのアンインストール  
Configuration Manager のセットアップを実行して、セカンダリ サイトに関連付けられていないプライマリ サイトをアンインストールできます。 プライマリ サイトをアンインストールする前に、次のことを検討してください。  

-   サイトに構成された境界内に Configuration Manager クライアントが配置されており、プライマリ サイトが Configuration Manager の階層に含まれている場合、プライマリ サイトをアンインストールする前に、階層内の別のプライマリ サイトに境界を追加することを検討します。  

-   プライマリ サイト サーバーが利用できなくなっている場合、中央管理サイトで階層のメンテナンス ツールを使用して、サイト データベースからプライマリ サイトを削除する必要があります。 詳細については、「[System Center Configuration Manager の階層のメンテナンス ツール (Preinst.exe)](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md)」を参照してください。  

プライマリ サイトをアンインストールするには、次の手順に従います。  

#### <a name="to-uninstall-a-primary-site"></a>プライマリ サイトをアンインストールするには  

1.  セットアップを実行する管理ユーザーが次のセキュリティ権限を持っていることを確認します。  

    -   中央管理サイト サーバーのローカル管理者権限  

    -   中央管理サイトがリモートの場合は、そのリモート サイト データベース サーバーのローカル管理者権限  

    -   中央管理サイトのサイト データベースの sysadmin 権限  

    -   プライマリ サイト コンピューターのローカル管理者権限  

    -   プライマリ サイトがリモートの場合は、そのリモート サイト データベース サーバーのローカル管理者権限  

    -   中央管理サイトのインフラストラクチャ管理者または完全な権限を持つ管理者のセキュリティ ロールに関連付けられたユーザー名  

2.  次のいずれかの方法を使用して、プライマリ サイト サーバーで Configuration Manager のセットアップを起動します。  

    -   [ **開始**] で、[ **Configuration Manager のセットアップ**] をクリックします。  

    -   &lt;*Configuration Manager のインストール メディア*>\SMSSETUP\BIN\X64 から Setup.exe を開きます。  

    -   &lt;*Configuration Manager のインストール パス*>\BIN\X64 から Setup.exe を開きます。  

3.  [ **開始する前に** ] ページで [ **次へ**] をクリックします。  

4.  [ **はじめに** ] ページで [ **Configuration Manager サイト サーバーをアンインストールする**] を選択してから、[ **次へ**] をクリックします。  

5.  [**Configuration Manager サイトのアンインストール**] で、サイトデータベースをプライマリ サイト サーバーから削除するかどうか、および Configuration Manager コンソールから削除するかどうかを指定します。 既定では、両方の項目が削除されます。  

    > [!IMPORTANT]  
    >  セカンダリ サイトがプライマリ サイトに接続されている場合は、プライマリ サイトをアンインストールする前にセカンダリ サイトを削除する必要があります。  

6.  [**はい**] をクリックして、Configuration Manager のプライマリ サイトのアンインストールを確定します。  

##  <a name="a-namebkmkuninstallprimarydistviewsa-uninstall-a-primary-site-that-is-configured-with-distributed-views"></a><a name="BKMK_UninstallPrimaryDistViews"></a> 分散ビューで構成されたプライマリ サイトのアンインストール  
 子プライマリ サイトで中央管理サイトへのレプリケーション リンクに分散ビューが構成されている場合、この子プライマリ サイトをアンインストールする前に、階層内の分散ビューを無効にする必要があります。 プライマリ サイトをアンインストールする前に分散ビューを無効にするには、次の手順に従います。  

#### <a name="to-uninstall-a-primary-site-that-is-configured-with-distributed-views"></a>分散ビューが構成されたプライマリ サイトをアンインストールするには  

1.  プライマリ サイトをアンインストールする前に、階層内で中央管理サイトとプライマリ サイト間の各リンクの分散ビューを無効にする必要があります。  

2.  各リンクの分散ビューを無効にしたら、中央管理サイトでプライマリ サイトのデータの再初期化が完了したことを確認します。 Configuration Manager コンソールの [**監視**] ワークスペースで、[**データベース レプリケーション**] ノード内のリンクを表示すると、データの初期化を監視できます。  

3.  中央管理サイトでデータが正常に再初期化されたら、プライマリ サイトをアンインストールできます。 プライマリ サイトをアンインストールするには、このトピックの「 [プライマリ サイトのアンインストール](#BKMK_UninstallPrimary) 」を参照してください。  

4.  プライマリ サイトが完全にアンインストールされたら、プライマリ サイトへのリンクに分散ビューを再構成できます。  

    > [!IMPORTANT]  
    >  各サイトで分散ビューを無効にする前にプライマリ サイトをアンインストールした場合や、中央管理サイトでプライマリ サイトのデータが正常に再初期化される前にプライマリ サイトをアンインストールした場合は、プライマリ サイトと中央管理サイト間のデータのレプリケーションが失敗する可能性があります。 この場合は、階層内の各リンクの分散ビューを無効にしてから、中央管理サイトとデータを再初期化した後で、分散ビューを再構成できます。  

##  <a name="a-namebkmkuninstallcasa-uninstall-the-central-administration-site"></a><a name="BKMK_UninstallCAS"></a> 中央管理サイトのアンインストール  
 Configuration Manager のセットアップを実行して、子プライマリ サイトが含まれていない中央管理サイトをアンインストールできます。 中央管理サイトをアンインストールするには、次の手順に従います。  

#### <a name="to-uninstall-a-central-administration-site"></a>中央管理サイトをアンインストールするには  

1.  セットアップを実行する管理ユーザーが、次のセキュリティ権限を持っていることを確認します。  

    -   中央管理サイト サーバーのローカル管理者権限  

    -   サイト データベース サーバーがサイト サーバーにインストールされていない場合は、中央管理サイト用のサイト データベース サーバーのローカル管理者権限  

2.  次のいずれかの方法を使用して、中央管理サイト サーバーで Configuration Manager のセットアップを起動します。  

    -   [ **開始**] で、[ **Configuration Manager のセットアップ**] をクリックします。  

    -   &lt;*Configuration Manager のインストール メディア*>\SMSSETUP\BIN\X64 から Setup.exe を開きます。  

    -   &lt;*Configuration Manager のインストール パス*>\BIN\X64 から Setup.exe を開きます。  

3.  [ **開始する前に** ] ページで [ **次へ**] をクリックします。  

4.  [ **はじめに** ] ページで [ **Configuration Manager サイト サーバーをアンインストールする**] を選択してから、[ **次へ**] をクリックします。  

5.  [**Configuration Manager サイトのアンインストール**] で、サイト データベースを中央管理サイト サーバーから削除するかどうか、および Configuration Manager コンソールから削除するかどうかを指定します。 既定では、両方の項目が削除されます。  

    > [!IMPORTANT]  
    >  プライマリ サイトが中央管理サイトに接続されている場合は、中央管理サイトをアンインストールする前にプライマリ サイトをアンインストールする必要があります。  

6.  [**はい**] をクリックして、Configuration Manager の中央管理サイトのアンインストールを確定します。  



<!--HONumber=Nov16_HO1-->


