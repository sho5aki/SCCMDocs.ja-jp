---
title: "レポートの構成 | Microsoft Docs"
description: "SQL Server Reporting Services に関する情報を含め、Configuration Manager 階層でのレポートのセットアップ方法について説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 55ae86a7-f0ab-4c09-b4da-89cd0e7fa0e0
caps.latest.revision: 6
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: aed95333b6509b0aa7061f23969381f1ce8aff7f


---
# <a name="configuring-reporting-in-system-center-configuration-manager"></a>System Center Configuration Manager におけるレポートの構成

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager コンソールでレポートを作成、変更、および実行するには、事前にいくつかの構成タスクを実行する必要があります。 このトピックの以下のセクションは、Configuration Manager 階層でレポートを構成する場合に役立ちます。  

 階層での Reporting Services のインストールおよび構成に進む前に、次の Configuration Manager のレポートに関するトピックを参照してください。  

-   [System Center Configuration Manager のレポートの概要](../../../core/servers/manage/introduction-to-reporting.md)  

-   [System Center Configuration Manager のレポートの計画](../../../core/servers/manage/planning-for-reporting.md)  

##  <a name="a-namebkmksqlreportingservicesa-sql-server-reporting-services"></a><a name="BKMK_SQLReportingServices"></a> SQL Server Reporting Services  
 SQL Server Reporting Services は、サーバー ベースのレポート プラットフォームであり、各種のデータ リソースに包括的なレポート機能を提供します。 Configuration Manager のレポート サービス ポイントは、SQL Server Reporting Services と通信し、指定されたレポート フォルダーへの Configuration Manager レポートのコピー、Reporting Services 設定の構成、および Reporting Services のセキュリティ設定の構成を行います。 Reporting Services は、Configuration Manager のサイト データベースに接続し、レポートを実行したときに返されるデータを取得します。  

 Configuration Manager のサイトにレポート サービス ポイントをインストールする前に、レポート サービス ポイント サイト システムの役割をホストするサイト システムに、SQL Server Reporting Services をインストールして構成する必要があります。 Reporting Services のインストールの詳細については、 [SQL Server の TechNet ライブラリ](http://go.microsoft.com/fwlink/p/?LinkId=266389)を参照してください。  

 SQL Server Reporting Services がインストールされていて、正常に実行されているかどうかを確認するには、次の手順に従います。  

#### <a name="to-verify-that-sql-server-reporting-services-is-installed-and-running"></a>SQL Server Reporting Services がインストールおよび実行されていることを確認するには  

1.  デスクトップで、[スタート ****]、[すべてのプログラム ****]、[Microsoft SQL Server 2008 R2 ****]、[構成ツール ****]、[Reporting Services 構成マネージャー ****] の順にクリックします。  

2.  [ **Reporting Services の構成の接続** ] ダイアログ ボックスで SQL Server Reporting Services をホストしているサーバーの名前を指定し、メニューで、SQL Reporting Services がインストールされている SQL Server のインスタンスを選択して、[ **接続**] をクリックします。 Reporting Services 構成マネージャーが開きます。  

3.  [ **レポート サーバーの状態** ] ページで、[ **レポート サービスの状態** ] が [ **開始**] に設定されていることを確認します。 設定されていない場合は、[開始] をクリックします。 ****  

4.  [ **Web サービス URL** ] ページで、[ **レポート サービスの Web サービスの URL** ] をクリックして、レポート フォルダーへの接続をテストします。 [Windows セキュリティ] ダイアログ ボックスが開いて、セキュリティ資格情報の入力を求められることがあります。 **** 既定では、使用しているユーザー アカウントが表示されます。 パスワードを入力して、[OK] をクリックします。 **** Web ページが正常に開くことを確認します。 ブラウザー ウィンドウを閉じます。  

5.  [ **データベース** ] ページで、[ **レポート サーバー モード** ] 設定が [ **ネイティブ**] を使用して構成されていることを確認します。  

6.  [ **レポート マネージャーの URL** ] ページで、[ **レポート マネージャー サイトの識別情報** ] にある URL をクリックして、レポート マネージャーの仮想ディレクトリへの接続をテストします。 [Windows セキュリティ] ダイアログ ボックスが開いて、セキュリティ資格情報の入力を求められることがあります。 **** 既定では、使用しているユーザー アカウントが表示されます。 パスワードを入力して、[OK] をクリックします。 **** Web ページが正常に開くことを確認します。 ブラウザー ウィンドウを閉じます。  

    > [!NOTE]  
    >  Reporting Services のレポート マネージャーは、Configuration Manager のレポートには必要ありませんが、インターネット ブラウザーでレポートを実行する場合、またはレポート マネージャーを使用してレポートを管理する場合に必要となります。  

7.  **[終了]** をクリックし、Reporting Services Configuration Manager を閉じます。  

##  <a name="a-namebkmkreportbuilder3a-configure-reporting-to-use-report-builder-30"></a><a name="BKMK_ReportBuilder3"></a> レポートの操作にレポート ビルダー 3.0 を使用するように構成する  

#### <a name="to-change-the-report-builder-manifest-name-to-report-builder-30"></a>レポート ビルダーのマニフェスト名をレポート ビルダー 3.0 に変更するには  

1.  Configuration Manager コンソールを実行しているコンピューターで、Windows レジストリ エディターを開きます。  

2.  **HKEY_LOCAL_MACHINE/SOFTWARE/Wow6432Node/Microsoft/ConfigMgr10/AdminUI/Reporting**を参照します。  

3.  **ReportBuilderApplicationManifestName** キーをダブルクリックして、値データを編集します。  

4.  [ReportBuilder_2_0_0_0.application **** ] を [ReportBuilder_3_0_0_0.application ****] に変更して、[OK ****] をクリックします。  

5.  Windows レジストリ エディターを閉じます。  

##  <a name="a-namebkmkinstallreportingservicespointa-install-a-reporting-services-point"></a><a name="BKMK_InstallReportingServicesPoint"></a> レポート サービス ポイントのインストール  
 サイトでレポートを管理するには、レポート サービス ポイントをサイトにインストールする必要があります。 レポート サービス ポイントは、SQL Server Reporting Services へのレポート フォルダーとレポートのコピー、レポートとフォルダーへのセキュリティ ポリシーの適用、および Reporting Services の構成設定を行います。 Configuration Manager コンソールでのレポートの表示、および Configuration Manager でのレポートの管理を行う前に、レポート サービス ポイントを構成する必要があります。 レポート サービス ポイントは、サイト システムの役割の 1 つであり、Microsoft SQL Server Reporting Services をインストールして実行しているサーバー上に構成する必要があります。 前提条件の詳細については、「[レポートの前提条件](prerequisites-for-reporting.md)」を参照してください。  

> [!IMPORTANT]  
>  レポート サービス ポイントをインストールするサイトを選択するときは、レポートにアクセスすることになるユーザーが、レポート サービス ポイントのインストール先サイトと同じセキュリティ スコープにいなければならないことに注意してください。  

> [!IMPORTANT]  
>  サイト システムにレポート サービス ポイントをインストールした後に、レポート サーバーの URL を変更しないでください。 たとえば、レポート サービス ポイントを作成した後に、Reporting Services Configuration Manager でレポート サーバーの URL を変更すると、Configuration Manager コンソールは引き続き古い URL を使用するため、コンソールからレポートを実行、編集、または作成できません。 URL レポート サーバーを変更する必要がある場合は、レポート サービス ポイントを削除して、URL を変更し、レポート サービス ポイントを再インストールします。  

 レポート サービス ポイントをインストールするには、次の手順に従います。  

#### <a name="to-install-the-reporting-services-point-on-a-site-system"></a>サイト システムにレポート サービス ポイントをインストールするには  

1.  Configuration Manager コンソールで、[ **管理**] をクリックします。  

2.  [ **管理** ] ワークスペースで [ **サイトの構成**] を展開して、[ **サーバーとサイト システムの役割**] をクリックします。  

    > [!TIP]  
    >  レポート サービス ポイント サイトの役割をホストするサイト システムのみを一覧表示するには、[ **サーバーとサイト システムの役割** ] を右クリックして、[ **レポート サービス ポイント**] を選択します。  

3.  対応する手順を使用して、レポート サービス ポイント サイト システムの役割を新規または既存のサイト システム サーバーに追加します。  

    > [!NOTE]  
    >  サイト システムの構成の詳細については、「[System Center Configuration Manager のサイト システム役割の追加](../deploy/configure/add-site-system-roles.md)」を参照してください。  

    -   **新しいサイト システム**: **[ホーム]** タブの **[作成]** グループで、 **[サイト システム サーバーの作成]**をクリックします。 サイト システム サーバーの作成ウィザードが開きます。 ****  

    -   **既存のサイト システム**: レポート サービス ポイントのサイト システムの役割をインストールするサーバーをクリックします。 サーバーをクリックすると、サーバーに既にインストールされているサイト システムの役割の一覧が、結果ウィンドウに表示されます。  

         [ **ホーム** ] タブの [ **サーバー** ] グループで、[ **サイト システムの役割の追加**] をクリックします。 サイト システムの役割の追加ウィザードが開きます。 ****  

4.  [ **全般** ] ページで、サイト システム サーバーの全般設定を指定します。 レポート サービス ポイントを既存のサイト システム サーバーに追加する場合は、以前に構成した値を確認します。  

5.  [ **システムの役割の選択** ] ページの利用可能な役割の一覧で [ **レポート サービス ポイント** ] を選択し、[ **次へ**] をクリックします。  

6.  [レポート サービス ポイント **** ] ページで、次の設定を構成します。  

    -   **サイト データベース サーバー名**: Configuration Manager サイト データベースをホストするサーバーの名前を指定します。 通常、ウィザードはサーバーの完全修飾ドメイン名 (FQDN) を自動的に取得します。 データベース インスタンスを指定するには、&lt;*サーバー名*>\&lt;*インスタンス名*> という形式を使用します。  

    -   **データベース名**: Configuration Manager サイト データベース名を指定して、**[確認]** をクリックし、ウィザードがサイト データベースにアクセスできることを確認します。  

        > [!IMPORTANT]  
        >  レポート サービス ポイントを作成しているユーザー アカウントには、サイト データベースに対する **読み取り** アクセス許可がある必要があります。 接続テストに失敗した場合、赤色の警告アイコンが表示されます。 失敗の詳細を確認するには、このアイコンの上にカーソルを移動します。 エラーを修正し、[ **テスト** ] をもう一度クリックします。  

    -   **フォルダー名**: Reporting Services で Configuration Manager レポートをホストするために作成および使用されるフォルダー名を指定します。  

    -   **Reporting Services サーバー インスタンス**: Reporting Services の SQL Server のインスタンスの一覧から選択します。 見つかったインスタンスが 1 つのみの場合は、既定では、それが表示および選択されます。 インスタンスが見つからない場合は、SQL Server Reporting Services がインストールおよび構成されているかどうか、および SQL Server Reporting Services がサイト システム上で開始されているかどうかを確認します。  

        > [!IMPORTANT]  
        >  Configuration Manager は、現在のユーザー コンテキストで、選択したサイト システム上の Windows Management Instrumentation (WMI) に接続して、Reporting Services の SQL Server のインスタンスを取得します。 現在のユーザーには、サイト システム上の WMI に対する [読み取り **** ] アクセス許可がある必要があります。アクセス許可がない場合は、Reporting Services インスタンスを取得できません。  

    -   **レポート サービス ポイントのアカウント**: **[設定]** をクリックして、レポートに表示されるデータを取得するために、レポート サービス ポイント上の SQL Server Reporting Services が Configuration Manager サイト データベースに接続する際に使用するアカウントを選択します。 **[既存のアカウント]** を選択して、以前に Configuration Manager アカウントとして構成されている Windows ユーザー アカウントを指定するか、**[新しいアカウント]** を選択して、現在 Configuration Manager アカウントとして構成されていない Windows ユーザー アカウントを指定します。 Configuration Manager は指定したユーザーにサイト データベースへのアクセスを自動的に付与します。 [ **管理** ] ワークスペースの [ **セキュリティ** ] ノードの [ **アカウント** ] サブフォルダーに、[ **ConfigMgr レポート サービス ポイント** ] のアカウント名でユーザーが表示されます。  

         レポート サービスを実行するアカウントはドメイン ローカル セキュリティ グループ **Windows Authorization Access Group**に属し、[ **tokenGroupsGlobalAndUniversal の読み取り** ] アクセス許可が [ **許可**] に設定されている必要があります。  

         指定された Windows ユーザー アカウントとパスワードは、暗号化されて Reporting Services データベースに格納されます。 Reporting Services は、このアカウントとパスワードを使用して、サイト データベースからレポートのデータを取得します。  

        > [!IMPORTANT]  
        >  指定するアカウントは、Reporting Services データベースをホストするコンピューターに [ローカル ログオン **** ] アクセス許可がある必要があります。  

7.  [ **レポート サービス ポイント** ] ページで、[ **次へ**] をクリックします。  

8.  [ **概要** ] ページで設定を確認し、[ **次へ** ] をクリックしてレポート サービス ポイントをインストールします。  

     ウィザードが完了すると、レポート フォルダーが作成され、Configuration Manager レポートが指定されたレポート フォルダーにコピーされます。  

    > [!NOTE]  
    >  レポート フォルダーが作成され、レポートがレポート サーバーにコピーされると、Configuration Manager はそのオブジェクトに適した言語を決定します。 関連する言語パックがサイトにインストールされている場合、Configuration Manager は、サイトのレポート サーバーで実行されているオペレーティング システムと同じ言語でオブジェクトを作成します。 その言語を使用できない場合、レポートは英語で作成および表示されます。 言語パックがないサイトにレポート サービス ポイントをインストールすると、レポートは英語でインストールされます。 レポート サービス ポイントをインストールした後に言語パックをインストールする場合、レポートのレポート サービス ポイントを適切な言語パックの言語で使用できるようにするには、そのポイントをアンインストールしてから再インストールする必要があります。 言語パックの詳細については、「[System Center Configuration Manager の言語パック](../deploy/install/language-packs.md)」を参照してください。  

###  <a name="a-namebkmkfileinstallationandsecuritya-file-installation-and-report-folder-security-rights"></a><a name="BKMK_FileInstallationAndSecurity"></a> ファイルのインストールおよびレポート フォルダーのセキュリティ権限  
 Configuration Manager は次のアクションを実行して、レポート サービス ポイントをインストールし、Reporting Services を構成します。  

> [!IMPORTANT]  
>  次の一覧のアクションは、SMS_Executive サービス用に構成したアカウント (通常は、サイト サーバーのローカルのシステム アカウント) の資格情報を使用して実行します。  

-   レポート サービス ポイントのサイトの役割をインストールします。  

-   ウィザードで指定した格納されている資格情報を使用して、Reporting Services にデータ ソースを作成します。 これは、レポートを実行したときに、Reporting Services がサイト データベースに接続するために使用する Windows ユーザー アカウントとパスワードです。  

-   Reporting Services に Configuration Manager のルート フォルダーを作成します。  

-   Reporting Services に [ **ConfigMgr レポート ユーザー** ] と [ **ConfigMgr レポート管理者** ] セキュリティ ロールを追加します。  

-   サブフォルダーを作成し、%ProgramFiles%\SMS_SRSRP から Reporting Services に Configuration Manager レポートを展開します。  

-   **サイトの読み取り**権限を持つ Configuration Manager 内のすべてのユーザー アカウントに、ルート フォルダーに対する Reporting Services の **[ConfigMgr レポート ユーザー]** ロールを追加します。  

-   **サイトの変更**権限を持つ Configuration Manager 内のすべてのユーザー アカウントに、ルート フォルダーに対する Reporting Services の **[ConfigMgr レポート管理者]** ロールを追加します。  

-   レポート フォルダーと Configuration Manager の保護されているオブジェクトの種類 (Configuration Manager サイト データベースで保持されているオブジェクト) の間のマッピングを取得します。  

-   Configuration Manager の管理ユーザーに、Reporting Services の特定のレポート フォルダーに対する次の権限を構成します。  

    -   ユーザーを追加し、Configuration Manager オブジェクトの**レポートの実行**アクセス許可を持つ管理ユーザーに、関連付けられているレポート フォルダーに対する **[ConfigMgr レポート ユーザー]** ロールを割り当てます。  

    -   ユーザーを追加し、Configuration Manager オブジェクトの**レポートの変更**アクセス許可を持つ管理ユーザーに、関連付けられているレポート フォルダーに対する **[ConfigMgr レポート管理者]** ロールを割り当てます。  

     Configuration Manager は Reporting Services に接続し、Configuration Manager と Reporting Services のルート フォルダーおよび特定のレポート フォルダーに対するアクセス許可をユーザーに設定します。 レポート サービス ポイントが最初にインストールされてから、Configuration Manager は Reporting Services に 10 分間隔で接続し、レポート フォルダーに構成されているユーザー権限が Configuration Manager ユーザーに設定された関連付けられている権限であることを確認します。 Reporting Services のレポート マネージャーを使用して、レポート フォルダーへのユーザーの追加、またはユーザー権限の変更を行うと、Configuration Manager は、サイト データベースに格納されている役割に基づいた割り当てを使用して、それらの変更を上書きします。 また、Configuration Manager は、Configuration Manager でのレポート権限を持っていないユーザーを削除します。  

##  <a name="a-namebkmksecurityrolesa-reporting-services-security-roles-for-configuration-manager"></a><a name="BKMK_SecurityRoles"></a> Configuration Manager の Reporting Services のセキュリティ ロール  
 Configuration Manager がレポート サービス ポイントをインストールするときに、Reporting Services に次のセキュリティ ロールを追加します。  

-   **ConfigMgr レポート ユーザー**: このセキュリティ ロールが割り当てられたユーザーは、Configuration Manager レポートのみを実行できます。  

-   **ConfigMgr レポート管理者**: このセキュリティ ロールが割り当てられたユーザーは、Configuration Manager のレポートに関連するすべてのタスクを実行できます。  

##  <a name="a-namebkmkverifyreportingservicespointinstallationa-verify-the-reporting-services-point-installation"></a><a name="BKMK_VerifyReportingServicesPointInstallation"></a> レポート サービス ポイントのインストールの検証  
 レポート サービス ポイントのサイトの役割を追加した後に、インストールを検証するには、特定のステータス メッセージおよびログ ファイルのエントリを確認します。 レポート サービス ポイントのインストールが成功したことを確認するには、次の手順に従います。  

> [!WARNING]  
>  レポートが Configuration Manager コンソールの **[監視]** ワークスペースにある **[レポート]** ノードの **[レポート]** サブフォルダーに表示される場合は、この手順をスキップすることができます。  

#### <a name="to-verify-the-reporting-services-point-installation"></a>レポート サービス ポイントのインストールを検証するには  

1.  Configuration Manager コンソールで、[監視] をクリックします。 ****  

2.  [ **監視** ] ワークスペースで、[ **システムのステータス**] を展開してから、[ **コンポーネントのステータス**] をクリックします。  

3.  コンポーネントの一覧で [SMS_SRS_REPORTING_POINT] をクリックします。 ****  

4.  [ **ホーム** ] タブの [ **コンポーネント** ] グループで、[ **メッセージを表示する**] をクリックして、[ **すべて**] をクリックします。  

5.  レポート サービス ポイントをインストールする前の日付と時刻を指定して、[OK] をクリックします。 ****  

6.  ステータス メッセージ ID 1015 が表示されていることを確認します。これは、レポート サービス ポイントが正常にインストールされたことを示します。 または、&lt;*ConfigMgr のインストール パス*>\Logs にある Srsrp.log ファイルを開いて、"**インストールは成功しました**" というメッセージを探します。  

     Windows エクスプローラーで、&lt;*ConfigMgr のインストール パス*>\Logs に移動します。  

7.  Srsrp.log を開いて、ログ ファイルのレポート サービス ポイントが正常にインストールされた時刻からログを確認します。 レポート フォルダーが作成されたこと、レポートが展開されたこと、および各フォルダーのセキュリティ ポリシーが確認されたことを検証します。 セキュリティ ポリシーの確認の最後の行の後ろに "SRS Web サービスがサーバー上で正常であることを確認しました" というメッセージがあることを確認します。 ****  

##  <a name="a-namebkmkcertificatea-configure-a-self-signed-certificate-for-configuration-manager-console-computers"></a><a name="BKMK_Certificate"></a> Configuration Manager コンソール コンピューターの自己署名入り証明書の構成  
 SQL Server Reporting Services レポートを作成する場合、多くのオプションがあります。 Configuration Manager コンソールでレポートを作成または編集する場合、Configuration Manager はレポート ビルダーを開いて、作成環境として使用します。 Configuration Manager レポートをどのように作成するかにかかわらず、サイト データベース サーバーでのサーバー認証のために自己署名入り証明書が必要となります。 Configuration Manager は、SMS プロバイダーがインストールされているサイト サーバーとコンピューターに証明書を自動的にインストールします。 このため、これらのコンピューターのいずれかから Configuration Manager コンソールを実行する場合は、そこでレポートを作成または編集できます。 ただし、別のコンピューターにインストールされている Configuration Manager コンソールからレポートの作成または変更を行う場合、サイト サーバーから証明書をエクスポートし、Configuration Manager コンソールを実行するコンピューターの**信頼されたユーザー**証明書ストアに追加する必要があります。  

> [!NOTE]  
>  SQL Server Reporting Services のその他のレポート作成環境の詳細については、SQL Server 2008 Books Online の「 [レポート作成環境の比較](http://go.microsoft.com/fwlink/p/?LinkId=242805) 」を参照してください。  

 両方のコンピューターが Windows Server 2008 R2 を実行している場合に、自己署名入り証明書のコピーをサイト サーバーから Configuration Manager コンソールを実行する別のコンピューターに転送するには、次のような手順を使用します。 別のオペレーティング システムのバージョンを使用しているために、この手順に従うことができない場合は、使用しているオペレーティング システムのドキュメントの対応する手順を参照してください。  

#### <a name="to-transfer-a-copy-of-self-signed-certificate-from-the-site-server-to-another-computer"></a>自己署名入り証明書のコピーをサイト サーバーから別のコンピューターに転送するには  

1.  サイト サーバーで次の手順を実行して、自己署名入り証明書をエクスポートします。  

    1.  **[スタート]**、 **[実行]**の順にクリックし、「 **mmc.exe**」と入力します。 空のコンソールで、[ **ファイル**] をクリックし、次に [ **スナップインの追加と削除**] をクリックします。  

    2.  [ **スナップインの追加と削除** ] ダイアログ ボックスで、[ **利用できるスナップイン** ] リストから [ **証明書**] を選択し、[ **追加**] をクリックします。  

    3.  [ **証明書スナップイン** ] ダイアログボックスで [ **コンピューター アカウント**] を選択し、[ **次へ**] をクリックします。  

    4.  [ **コンピューターの選択** ] ダイアログ ボックスで、[ **ローカル コンピューター: (このコンソールを実行しているコンピューター)** ] が選択されていることを確認して、[ **完了**] をクリックします。  

    5.  [ **スナップインの追加と削除** ] ダイアログ ボックスで、[ **OK**] をクリックします。  

    6.  コンソールで、[ **証明書 (ローカル コンピューター)**]、[ **信頼されたユーザー**] の順に展開して、[ **証明書**] をクリックします。  

    7.  &lt;*サイト サーバーの FQDN*> というフレンドリ名が付いている証明書を右クリックし、**[すべてのタスク]** をクリックして **[エクスポート]** を選択します。  

    8.  既定のオプションを使用して、 **証明書のエクスポート ウィザード** を完了し、 **.cer** ファイル名拡張子を使用して証明書を保存します。  

2.  Configuration Manager コンソールを実行するコンピューターで次の手順を実行し、自己署名入り証明書を信頼されたユーザー証明書ストアに追加します。  

    1.  上記の手順 1.a から 1.e を繰り返し、 管理ポイントのコンピューターに [**証明書**] スナップイン MMC を構成します。  

    2.  コンソールで、[ **証明書 (ローカル コンピューター)**]、[ **信頼されたユーザー**] の順に展開し、[ **証明書**] を右クリックして、[ **すべてのタスク**]、[ **インポート** ] の順に選択して、 **証明書のインポート ウィザード**を開始します。  

    3.  [ **インポートするファイル** ] ページで、手順 1.h で保存した証明書を選択し、[ **次へ**] をクリックします。  

    4.  [ **証明書ストア** ] ページで [ **証明書をすべて次のストアに配置する**] を選択し、[ **証明書ストア** ] を [ **信頼されたユーザー**] に設定して、[ **次へ**] をクリックします。  

    5.  [完了] をクリックし、ウィザードを閉じて、コンピューターへの証明書の構成を完了します。 ****  

##  <a name="a-namebkmkmodifyreportingservicespointa-modify-reporting-services-point-settings"></a><a name="BKMK_ModifyReportingServicesPoint"></a> レポート サービス ポイントの設定の変更  
 レポート サービス ポイントをインストールしたら、サイト データベースの接続および認証の設定をレポート サービス ポイントのプロパティで変更できます。 レポート サービス ポイントの設定を変更するには、次の手順に従います。  

#### <a name="to-modify-reporting-services-point-settings"></a>レポート サービス ポイントの設定を変更するには  

1.  Configuration Manager コンソールで、[ **管理**] をクリックします。  

2.  [ **管理** ] ワークスペースで [ **サイトの構成**] を展開し、[ **サーバーとサイト システムの役割** ] をクリックして、サイト システムの一覧を表示します。  

    > [!TIP]  
    >  レポート サービス ポイント サイトの役割をホストするサイト システムのみを一覧表示するには、[ **サーバーとサイト システムの役割** ] を右クリックして、[ **レポート サービス ポイント**] を選択します。  

3.  設定を変更するレポート サービス ポイントをホストするサイト システムを選択し、[ **サイト システムの役割** ] の [ **レポート サービス ポイント**] を選択します。  

4.  [ **サイトの役割** ] タブの [ **プロパティ** ] グループで、[ **プロパティ**] をクリックします。  

5.  [レポート サービス ポイントのプロパティ] ダイアログ ボックスで、次の設定を変更できます。 ****  

    -   **サイト データベース サーバー名**: Configuration Manager サイト データベースをホストするサーバーの名前を指定します。 通常、ウィザードはサーバーの完全修飾ドメイン名 (FQDN) を自動的に取得します。 データベース インスタンスを指定するには、&lt;*サーバー名*>\&lt;*インスタンス名*> という形式を使用します。  

    -   **データベース名**: System Center 2012 Configuration Manager サイト データベース名を指定して、**[確認]** をクリックし、ウィザードがサイト データベースにアクセスできることを確認します。  

        > [!IMPORTANT]  
        >  レポート サービス ポイントを作成しているユーザー アカウントには、サイト データベースに対する読み取りアクセス許可がある必要があります。 接続テストに失敗した場合、赤色の警告アイコンが表示されます。 失敗の詳細を確認するには、このアイコンの上にカーソルを移動します。 エラーを修正し、[ **テスト** ] をもう一度クリックします。  

    -   **ユーザー アカウント**: **[設定]**をクリックして、レポートに表示されるデータを取得するために、レポート サービス ポイント上の SQL Server Reporting Services が Configuration Manager サイト データベースに接続する際に使用するアカウントを選択します。 **[既存のアカウント]** を選択して、既存の Configuration Manager 権限を持つ Windows ユーザー アカウントを指定するか、**[新しいアカウント]** を選択して、現在 Configuration Manager で権限を持っていない Windows ユーザー アカウントを指定します。 Configuration Manager は指定したユーザー アカウントにサイト データベースへのアクセスを自動的に付与します。 アカウントは、[ **管理** ] ワークスペースの [ **セキュリティ** ] ノードの [ **アカウント** ] サブフォルダーに、[ **ConfigMgr SRS レポート ポイント** ] のアカウントとして表示されます。  

         指定された Windows ユーザー アカウントとパスワードは、暗号化されて Reporting Services データベースに格納されます。 Reporting Services は、このアカウントとパスワードを使用して、サイト データベースからレポートのデータを取得します。  

        > [!IMPORTANT]  
        >  サイト データベースがリモート サイト システムにある場合は、そのコンピューターに対する [ローカル ログオン] アクセス許可が指定したアカウントにある必要があります。 ****  

6.  [ **OK** ] をクリックして、変更を保存し、ダイアログ ボックスを閉じます。  

## <a name="upgrading-sql-server"></a>SQL Server のアップグレード  
 SQL Server と、レポート サービス ポイントのデータ ソースとして使用される SQL Server Reporting Services をアップグレードした後に、Configuration Manager コンソールからレポートを実行または編集するときにエラーが発生する可能性があります。 Configuration Manager コンソールからレポートが適切に機能するには、そのサイトのレポート サービス ポイント サイト システムの役割を削除してから、再インストールする必要があります。 ただし、アップグレード後は、インターネット ブラウザーから引き続き正常にレポートの実行と編集を行うことができます。  

##  <a name="a-namebkmkconfigurereportoptionsa-configure-report-options"></a><a name="BKMK_ConfigureReportOptions"></a> レポート オプションの構成  
 レポートを管理するために使用する既定のレポート サービス ポイントを選択するには、Configuration Manager サイトのレポート オプションを使用します。 サイトでは複数のレポート サービス ポイントを持つことができますが、レポートの管理に使用されるのは、レポート オプションで選択した既定のレポート サーバーのみです。 サイトのレポート オプションを構成するには、次の手順に従います。  

#### <a name="to-configure-report-options"></a>レポート オプションを構成するには  

1.  Configuration Manager コンソールで、[監視] をクリックします。 ****  

2.  [ **監視** ] ワークスペースで、[ **レポート**] を展開し、[ **レポート**] をクリックします。  

3.  [ **ホーム** ] タブの [ **設定** ] グループで、[ **レポート オプション**] をクリックします。  

4.  一覧から既定のレポート サーバーを選択して、[OK] をクリックします。 **** 一覧にレポート サービス ポイントが表示されない場合は、レポート サービス ポイントがサイトに正常にインストールおよび構成されていることを確認します。  

## <a name="next-steps"></a>次のステップ
[レポートの操作とメンテナンス](operations-and-maintenance-for-reporting.md)



<!--HONumber=Dec16_HO3-->


