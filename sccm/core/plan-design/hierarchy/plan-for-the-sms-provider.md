---
title: "SMS プロバイダーの計画 | System Center Configuration Manager"
description: "System Center Configuration Manager の管理に SMS プロバイダーを使用する方法について説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5d5d6273-0d8a-43c7-865a-cdb1736dcae3
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: bdf7b9b4ab9e9da25bf32891381f61c94ef28285


---
# <a name="plan-for-the-sms-provider-for-system-center-configuration-manager"></a>System Center Configuration Manager の SMS プロバイダーの計画

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager の管理には、**SMS プロバイダー**のインスタンスに接続する Configuration Manager コンソールを使用する必要があります。 既定では、SMS プロバイダーは、サイトのインストール時に中央管理サイトまたはプライマリ サイトにインストールされます。  


##  <a name="a-namebkmkplansmsprova-about-the-sms-provider"></a><a name="BKMK_PlanSMSProv"></a> SMS プロバイダーについて  
 SMS プロバイダーは、サイトで Configuration Manager データベースの**読み取り**と**書き込み**アクセス権を割り当てる、Windows Management Instrumentation (WMI) プロバイダーの 1 つです。  

-   **SMS Admins**  グループには、SMS プロバイダーへのアクセス権が備わっています。 Configuration Manager は、サイト サーバーと各 SMS プロバイダー コンピューターにこのセキュリティ グループを自動的に作成します。  

-   それぞれの中央管理サイトとプライマリ サイトには、SMS プロバイダーが少なくとも 1 つなければなりません。  必要に応じて、さらにプロバイダーをインストールできます。  

-   セカンダリ サイトでは SMS プロバイダーはサポートされていません。  


各 Configuration Manager コンソール、リソース エクスプローラー、ツール、カスタム スクリプトはそれぞれ SMS プロバイダーを使用するので、Configuration Manager 管理ユーザーはデータベースに格納されている情報にアクセスできます。 SMS プロバイダーは、Configuration Manager クライアントとは動作しません。 Configuration Manager コンソールをサイトに接続すると、Configuration Manager コンソールはサイト サーバーで WMI のクエリを実行し、使用する SMS プロバイダーのインスタンスを見つけます。  

 SMS プロバイダーは、Configuration Manager にセキュリティを強制するのを助けます。 Configuration Manager コンソールを実行している管理ユーザーが見ることのできる情報だけが、データベースから返されます。  

> [!IMPORTANT]  
>  サイトの SMS プロバイダーがインストールされているコンピューターがオフラインのときは、Configuration Manager コンソールから、そのサイトのデータベースに接続することはできません。  

 SMS プロバイダーを管理する方法については、「 [Modify your System Center Configuration Manager infrastructure](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider) 」の「 [Manage the SMS Provider](../../../core/servers/manage/modify-your-infrastructure.md)」をご覧ください。  

 **SMS プロバイダーをインストールする前提条件:**  

 SMS プロバイダーをサポートするには  

-   サイト サーバーおよびサイト データベース サーバーと双方向の信頼関係があるドメインにある。  

-   別のサイトのサイト システムの役割がインストールされていない。  

-   どのサイトの SMS プロバイダーの役割もインストールされていない。  

-   サイト サーバーによってサポートされているオペレーティング システムを実行している。  

-   SMS プロバイダーと共にインストールされる Windows 自動展開キット (Windows ADK) コンポーネントをサポートするために、650 MB 以上の空きディスク領域が必要です。 Windows ADK と SMS プロバイダーの詳細については、このトピックの「 [SMS プロバイダーのオペレーティング システム展開要件](#BKMK_WAIKforSMSProv) 」を参照してください。  

##  <a name="a-namebkmklocationa-sms-provider-locations"></a><a name="bkmk_location"></a> SMS プロバイダの場所  
 サイトをインストールするときに、そのサイトの 1 つ目の SMS プロバイダーが自動的にインストールされます。 SMS プロバイダーのインストール先として、次のいずれかを指定できます。  

-   サイト サーバー コンピューター  

-   サイト データベース コンピューター  

-   SMS プロバイダーや別のサイトのサイト システムの役割がインストールされていない、サーバー向けコンピューター  


サイトにインストールされている各 SMS プロバイダーの場所を確認するには、サイトの [ **プロパティ** ] ダイアログ ボックスの [ **全般** ] タブを表示します。  

 1 つの SMS プロバイダーが同時に複数の要求を受信できます。 この同時接続は、SMS プロバイダーのコンピューターで使用できるサーバー接続の数と、接続要求を取り扱えるリソースによって制限されます。  

 サイトをインストールした後で、サイト サーバーでセットアップをもう一度実行して、既存の SMS プロバイダーの場所を変えたり、同じサイトに追加の SMS プロバイダーをインストールしたりできます。 1 台のコンピューターに、1 つだけのサイトの SMS プロバイダーを 1 つだけインストールできます。  

 次の情報に基づいて、サポートされているそれぞれの場所に SMS プロバイダーをインストールすることの長所と欠点を特定します。  


**Configuration Manager サイト サーバー**  

-   **利点:**  

    -   SMS プロバイダーは、サイト データベース コンピューターのシステム リソースを使用しません。  

    -   サイト サーバーまたはサイト データベース以外のコンピューターに SMS プロバイダーをインストールした場合より、パフォーマンスが高くなります。  

-   **欠点:**  

    -   SMS プロバイダーが、サイト サーバーで占有できるはずのシステム リソースとネットワーク リソースを使用します。  


**サイト データベースをホストする SQL Server**  

-   **利点:**  

    -   SMS プロバイダーは、サイト サーバーのサイト システム リソースを使用しません。  

    -   サーバーのリソースが十分ある場合は、3 つのインストール先のうち、一番高いパフォーマンスが得られます。  

-   **欠点:**  

    -   SMS プロバイダーが、サイト データベースで占有できるはずのシステム リソースとネットワーク リソースを使用します。  

    -   サイト データベースを SQL Server クラスターのインスタンスでホストする場合は、この場所に SMS プロバイダーをインストールすることはできません。  


**サイト サーバーまたはサイト サーバー データベース以外のコンピューター**  

-   **利点:**  

    -   SMS プロバイダーは、サイト サーバーやサイト データベースのコンピューターのリソースを使用しません。  

    -   追加の SMS プロバイダーをインストールして、接続の可用性を上げるのに便利です。  

-   **欠点:**  

    -   SMS プロバイダーがサイト サーバーおよびサイト データベース コンピューターと連携する必要があります。そのため、ネットワーク トラフィックが発生し、SMS プロバイダーのパフォーマンスが低下する可能性があります。  

    -   サイト データベース コンピューター、および Configuration Manager コンソールがインストールされているすべてのコンピューターから、常に、この場所にアクセスできなければなりません。  

    -   SMS プロバイダーが、他のサービスで占有できるはずのシステム リソースを使用します。  

##  <a name="a-namebkmksmsprovlanguagesa-about-sms-provider-languages"></a><a name="BKMK_SMSProvLanguages"></a> SMS プロバイダーの言語について  
 SMS プロバイダーは、そのインストール先のコンピューターの表示言語とは独立して動作します。  

 管理者ユーザーまたは Configuration Manager プロセスが、SMS プロバイダーでデータを要求すると、SMS プロバイダーは、要求元のコンピューターのオペレーティング システムの言語に合う形式でデータを返そうとします。 SMS プロバイダーが情報を別の言語に翻訳することはありません。 その代わり、Configuration Manager コンソールで表示するデータを返すときは、そのデータの表示言語が、オブジェクトとソースと記憶域の種類によって決まります。  

 オブジェクトのデータがどのようにデータベースに保存されたかによって、使用可能な言語が異なります。  

-   Configuration Manager で作成したオブジェクトをデータベースに保存するときは、複数の言語がサポートされています。 オブジェクトは、セットアップを実行するときにオブジェクトが作成されたサイトで構成されている言語で保存されます。 これらのオブジェクトは、要求元のコンピューターの表示言語がオブジェクトで使用できる場合は、その言語で Configuration Manager コンソールに表示されます。 要求元のコンピューターの表示言語でオブジェクトを表示できない場合は、既定の言語、つまり英語で表示されます。  

-   管理ユーザーが作成したオブジェクトは、作成時に使われた言語でデータベースに保存されます。 これらのオブジェクトが Configuration Manager コンソールに表示されるときにも、同じ言語が使われます。 SMS プロバイダーで変換することはできず、多言語のオプションもありません。  

##  <a name="a-namebkmkmultismsprova-use-multiple-sms-providers"></a><a name="BKMK_MultiSMSProv"></a> 複数の SMS プロバイダーの使用  
 サイトのインストールが完了したら、そのサイト用に追加の SMS プロバイダーをインストールすることができます。 追加の SMS プロバイダーをインストールするには、サイト サーバーで Configuration Manager のセットアップを実行します。 次の場合に、SMS プロバイダーの追加インストールを検討してください。  

-   Configuration Manager コンソールを実行する管理ユーザーが多数存在し、サイトに同時に接続することになる。  

-   SMS プロバイダーを頻繁に呼び出す可能性のある Configuration Manager SDK、または同様の製品を導入する予定である。  

-   SMS プロバイダーの可用性を高くしたい。  


サイトに複数の SMS プロバイダーをインストールした場合は、新しい接続要求が発生するたびに、インストール済みの SMS プロバイダーのいずれかに無作為に割り当てられます。 特定の接続セッションで、特定の場所にある SMS プロバイダーを使用するように指定することはできません。  

> [!NOTE]  
>  SMS プロバイダーの各インストール先の長所と欠点、および新しい接続で使用する SMS プロバイダーを制御できないということを考え合わせて、複数の SMS プロバイダーの使用を計画してください。  

たとえば、Configuration Manager コンソールをサイトに初めて接続すると、サイト サーバーで WMI のクエリが実行されて、コンソールで使用する SMS プロバイダーのインスタンスが無作為に割り当てられます。 SMS プロバイダーのこの特定のインスタンスは、Configuration Manager コンソールのセッションが終了するまで Configuration Manager コンソールで使用されたままになります。 しかし、SMS プロバイダーのコンピューターがネットワークで使用できなくなったため、セッションが終了したとします。そこで、Configuration Manager コンソールを再接続しようとすると、この新しい接続セッションに、SMS プロバイダーのコンピューターが無作為に割り当てられます。 したがって、前と同じ SMS プロバイダーのコンピューター、つまり使用できない SMS プロバイダーが、割り当てられることもあり得ます。 このような場合は、使用可能な SMS プロバイダーのコンピューターが割り当てられるまで、Configuration Manager コンソールの接続を繰り返すことになります。  

##  <a name="a-namebkmkaboutsmsadminsa-about-the-sms-admins-group"></a><a name="BKMK_AboutSMSAdmins"></a> SMS Admins グループについて  
 SMS 管理者グループは、SMS プロバイダーの管理アクセス権を持っています。 このグループは、サイトをインストールするときに、サイト サーバーおよび SMS プロバイダーの各インストール先コンピューターに自動的に作成されます。 SMS 管理者グループの特長は、次のとおりです。  

-   コンピューターがメンバー サーバーの場合は、SMS 管理者グループがローカル グループとして作成されます。  

-   コンピューターがドメイン コントローラーの場合は、SMS 管理者グループがドメイン ローカル グループとして作成されます。  

-   コンピューターから SMS プロバイダーをアンインストールしても、SMS 管理者グループは、そのコンピューターから削除されません。  


ユーザーが SMS プロバイダーに正しく接続するには、そのユーザー アカウントが SMS 管理者グループのメンバーでなければなりません。 Configuration Manager コンソールで管理ユーザーを構成すると、その管理ユーザーが、階層にある各サイト サーバーと SMS プロバイダーのコンピューターの SMS 管理者グループに自動的に追加されます。 一方、Configuration Manager コンソールで管理ユーザーを削除した場合は、その管理ユーザーが、階層にある各サイト サーバーと SMS プロバイダーのコンピューターの SMS 管理者グループから削除されます。  

ユーザーが SMS プロバイダーに正常に接続すると、そのユーザーの役割に基づいて、Configuration Manager のどのリソースにアクセスして管理できるかが決められます。  

SMS 管理者グループの権限とアクセス許可を表示して構成するには、WMI コントロールという MMC スナップインを使います。 既定では、 **Everyone** に [ **メソッドの実行**]、[ **プロバイダーによる書き込み**]、および　[ **アカウントの有効化** ] アクセス許可が割り当てられます。 ユーザーが SMS プロバイダーに接続すると、そのユーザーに Configuration Manager コンソールで定義されている、ユーザーの役割に基づいたセキュリティ権限に従って、サイト データベースのデータへのアクセス権が付与されます。 SMS Admins グループには、 **Root\SMS** 名前空間に対する [ **アカウントの有効化** ] および [ **リモートの有効化** ] が明示的に付与されます。  

> [!NOTE]  
>  リモートの Configuration Manager コンソールを使用する管理ユーザーには、サイト サーバー コンピューターと SMS プロバイダーのコンピューターの DCOM をリモートから有効にするアクセス許可が必要です。 これらの権限はどのグループにも付与することができますが、権限の管理が簡単になるように、SMS 管理者グループに付与することをお勧めします。 詳細については、「 [Configure DCOM permissions for remote Configuration Manager consoles](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ConfigDCOMforRemoteConsole) 」トピックの「 [Modify your System Center Configuration Manager infrastructure](../../../core/servers/manage/modify-your-infrastructure.md) 」セクションを参照してください。  


##  <a name="a-namebkmksmsprovnamespacea-about-the-sms-provider-namespace"></a><a name="BKMK_SMSProvNamespace"></a> SMS プロバイダーの名前空間について  
SMS プロバイダーの構造は、WMI スキーマによって決まります。 SMS プロバイダーのスキーマ内の Configuration Manager データの場所は、スキーマの名前空間で記述します。 次の表に、SMS プロバイダーで使用する一般的な名前空間をいくつか示します。  

|Namespace|説明|  
|---------------|-----------------|  
|Root \sms\site_*&lt;サイト コード\>*|Configuration Manager コンソール、リソース エクスプローラー、Configuration Manager のツール、スクリプトによって使用される SMS プロバイダー。|  
|Root\SMS\SMS_ProviderLocation|サイトの SMS プロバイダーのコンピューターの場所|  
|Root\CIMv2|ハードウェアとソフトウェアのインベントリ中に、WMI 名前空間情報がインベントリされる場所|  
|Root\CCM|Configuration Manager クライアントの構成ポリシーとクライアント データ。|  
|root\CIMv2\SMS|インベントリのクライアント エージェントによって収集されるインベントリ レポート クラスの場所。 これらの設定は、コンピューターのポリシーの評価中にクライアントによってコンパイルされ、コンピューターのクライアント設定の構成に基づいています。|  

##  <a name="a-namebkmkwaikforsmsprova-operating-system-deployment-requirements-for-the-sms-provider"></a><a name="BKMK_WAIKforSMSProv"></a> SMS プロバイダーのオペレーティング システム展開要件  
SMS プロバイダーでは、Configuration Manager コンソールを使ってオペレーティング システム展開操作機能を使用するためには、SMS プロバイダーを実行するコンピューターに次の外部依存関係をインストールしている必要があります。  

-   Windows アセスメント & デプロイメント キット 8.1  

 Windows ADK をインストールすることで、オペレーティング システムの展開を管理するときに、SMS プロバイダーで次の操作を行えるようになります。  

-   WIM ファイルの詳細を表示する  

-   既存のブート イメージにドライバー ファイルを追加する  

-   ブート用 ISO ファイルを作成する  


Windows ADK をインストールするには、SMS プロバイダーのインストール先コンピューターに 650 MB 以上の空きディスク領域が必要です。 このような大きな空きディスク領域が必要なのは、Configuration Manager によって Windows PE ブート イメージがインストールされるためです。  



<!--HONumber=Nov16_HO1-->


