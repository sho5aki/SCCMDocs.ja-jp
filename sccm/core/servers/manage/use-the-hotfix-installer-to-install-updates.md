---
title: "修正プラグラム インストーラー | System Center Configuration Manager"
description: "どのような場合に、どのような方法で Configuration Manager の修正プログラム インストーラーを使用して更新プログラムをインストールするかについて説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f3058277-c597-4dac-86d1-41b6f7e62b36
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 03940a499416ce4231bda5feb8a2e323abdff578


---
# <a name="use-the-hotfix-installer-to-install-updates-for-system-center-configuration-manager"></a>Use the Hotfix Installer to install updates for System Center Configuration Manager (修正プログラム インストーラーを使用して、System Center Configuration Manager の更新プログラムをインストールする)

*適用対象: System Center Configuration Manager (Current Branch)*

一部の System Center Configuration Manager の更新プログラムは、Microsoft クラウド サービスからは使用できず、帯域外でのみ取得されます。 たとえば、特定の問題に対処する限定リリース修正プログラムです。   
マイクロソフトから受け取った更新プログラム (または修正プログラム) をインストールする必要があり、その更新プログラムのファイル名が拡張子 **.exe** で終わる場合は (ただし、**update.exe を除く**)、その修正プログラムのダウンロードに含まれている修正プログラム インストーラーを使用して、更新プログラムを Configuration Manager サイト サーバーに直接インストールします。  

 修正プログラム ファイルのファイル拡張子が **.update.exe** である場合は、「[修正プログラムを System Center Configuration Manager にインポートするには、更新登録ツールを使用します](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md)」を参照してください。  

> [!NOTE]  
>  このトピックでは、System Center Configuration Manager を更新する修正プログラムをインストールする方法に関する一般的なガイダンスを提供します。 特定の更新に関する詳細については、Microsoft サポートで、対応するサポート技術情報 (KB) 記事を参照してください。  

##  <a name="a-namebkmkoverviewa-overview-of-hotfixes-for-configuration-manager"></a><a name="bkmk_Overview"></a> Configuration Manager の修正プログラムの概要  
 Configuration Manager の修正プログラムは、SQL Server などの他の Microsoft 製品の修正プログラムに類似していて、1 つの個別の修正プログラムまたはバンドル (修正プログラムのロールアップ) のどちらかが含まれており、マイクロソフト サポート技術情報の記事で説明されています。  

 単一の更新プログラムには、Configuration Manager を更新する修正プログラムのインストール方法について一般的なガイダンスが提供されます。  
更新バンドルには、Configuration Manager の特定のバージョンを対象とする複数の更新プログラムが含まれています。  
更新がバンドルである場合は、そのバンドルから個々の更新プログラムをインストールすることはできません。  

 追加のコンピューターに更新プログラムをインストールするための展開を作成する予定なら、更新バンドルを中央管理サイト サーバーまたはプライマリ サイト サーバーにインストールする必要があります。  

 更新バンドルを実行すると、以下のことが実行されます。  

-   該当する各コンポーネント用の更新ファイルが更新バンドルから抽出されます。  

-   更新プログラムと更新プログラムの展開オプションを構成する手順を案内するウィザードが起動されます。  

-   ウィザードが完了したら、サイト サーバーに適用されるバンドル内の更新プログラムがサイト サーバーにインストールされます。  

また、このウィザードは、追加のコンピューターに更新プログラムをインストールするために使用できる展開も作成します。 追加のコンピューターに更新プログラムを展開するには、ソフトウェア展開パッケージや Microsoft System Center Updates Publisher 2011 などのサポートされている展開方法を使用します。  

 ウィザードを実行すると、Updates Publisher 2011 で使用する **.cab** ファイルがサイト サーバー上に作成されます。 必要に応じて、ソフトウェア展開用の 1 つまたは複数のパッケージを作成するようにウィザードを構成することもできます。 これらの展開を使用して、クライアントまたは Configuration Manager コンソールなどのコンポーネントに更新プログラムをインストールできます。 Configuration Manager クライアントを実行していないコンピューターに、手動で更新プログラムをインストールすることもできます。  

 Configuration Manager の次の 3 つのグループを更新できます。  

-   Configuration Manager には次のサーバーの役割があります。  

    -   中央管理サイト  

    -   プライマリ サイト  

    -   セカンダリ サイト  

    -   リモート SMS プロバイダー  

-   Configuration Manager コンソール  

-   Configuration Manager クライアント  

> [!NOTE]  
>  **サイト システムの役割用の更新プログラム** (サイト データベースとクラウドベースの配布ポイントの更新を含む) は、サイト コンポーネント マネージャーによってサイト サーバーおよびサービスの更新プログラムの一部としてインストールされます。  
>   
>  ただし、更新プル配布ポイントは、サイト コンポーネント マネージャーではなく、配布マネージャーによって処理されます。  

 Configuration Manager の各更新バンドルは、自己抽出型の .exe ファイル (SFX) です。このファイルには、Configuration Manager の適用対象コンポーネントに更新プログラムをインストールするために必要なファイルが含まれています。 通常、SFX ファイルには次のファイルが含まれています。  

|ファイル|説明|  
|----------|-------------|  
|&lt;製品バージョン\>-QFE-KB&lt;サポート技術情報の記事 ID\>-&lt;プラットフォーム\>-&lt;言語\>.exe|更新プログラム ファイルです。 このファイルのコマンド ラインは、Updatesetup.exe によって管理されます。<br /><br /> たとえば、<br />CM1511RTM-QFE-KB123456-X64-ENU.exe|  
|Updatesetup.exe|.msi ラッパーは、更新プログラムのバンドルのインストールを管理します。<br /><br /> 更新プログラムを実行すると、Updatesetup.exe によって、このファイルを実行するコンピューターの表示言語が検出されます。 既定では、更新プログラムのユーザー インターフェイスは英語で表示されます。 ただし、表示言語がサポートされている場合、ユーザー インターフェイスは、コンピューターのローカル言語で表示されます。|  
|License_&lt;言語\>.rtf|適用対象となる場合、各更新プログラムには、サポートされる言語の 1 つまたは複数のライセンス ファイルが含まれます。|  
|&lt;製品と更新の種類>-&lt;製品バージョン\>-&lt;サポート技術情報の記事 ID\>-&lt;プラットフォーム\>.msp|更新プログラムが Configuration Manager コンソールまたはクライアントに適用される場合、更新プログラムのバンドルには、個別の Windows インストーラー修正プログラム (.msp) ファイルが含まれます。<br /><br /> たとえば、<br /><br /> **Configuration Manager コンソールの更新プログラム:** ConfigMgr1511-AdminUI-KB1234567-i386.msp<br /><br /> **クライアントの更新プログラム:** ConfigMgr1511-client-KB1234567-i386.msp<br />ConfigMgr1511-client-KB1234567-x64.msp|  

 既定では、更新プログラムのバンドルは、サイト サーバーの .log ファイルに操作の履歴を記録します。 ログ ファイルは、更新プログラムのバンドルと同じ名前で、 **%SystemRoot%/Temp** フォルダーに保存されます。  

 更新プログラムのバンドルを実行すると、更新プログラムのバンドルと同じ名前のファイルがコンピューターの一時フォルダーに抽出され、Updatesetup.exe が実行されます。 Updatesetup.exe によって、Configuration Manager のソフトウェア更新プログラム &lt;製品バージョン\> &lt;サポート技術情報の記事番号\> のウィザードが開始されます。  

 更新プログラムのスコープに当てはまる場合は、サイト サーバーの System Center Configuration Manager インストール フォルダーに一連のフォルダーがウィザードによって作成されます。 フォルダー構造は   
 **\\\\&lt;サーバー名\>\SMS_&lt;サイト コード\>\Hotfix\\&lt;サポート技術情報の記事番号\>\\&lt;更新プログラムの種類\>\\&lt;プラットフォーム\>**です。  

 次の表に、フォルダー構造内のフォルダーに関する詳細を示します。  

|フォルダー名|説明|  
|-----------------|----------------------|  
|&lt;サーバー名\>|更新プログラムのバンドルを実行するサイト サーバーの名前です。|  
|SMS_&lt;サイト コード\>|Configuration Manager インストール フォルダーの共有名です。|  
|&lt;サポート技術情報の記事番号\>|この更新プログラムのバンドルのサポート技術情報記事の ID 番号です。|  
|&lt;更新プログラムの種類\>|Configuration Manager の更新プログラムの種類です。 ウィザードによって、更新プログラムのバンドルに含まれる更新プログラムの種類ごとに、個別のフォルダーが作成されます。 フォルダー名は、更新プログラムの種類を表します。 フォルダーには次のようなものがあります。<br /><br /> **サーバー**:サイト サーバー、サイト データベース サーバー、SMS プロバイダーを実行するコンピューターの更新プログラムが格納されます。<br /><br /> **クライアント**: Configuration Manager クライアントの更新プログラムが含まれています。<br /><br /> **AdminConsole**: Configuration Manager コンソールの更新プログラムが含まれています。<br /><br /> 前述の更新の種類に加えて、ウィザードでは **SCUP**という名前のフォルダーが作成されます。 このフォルダーは更新プログラムの種類を表していません。Updates Publisher の .cab ファイルが格納されます。|  
|&lt;プラットフォーム\>|プラットフォーム別のフォルダーです。 プロセッサの種類固有の更新プログラム ファイルが格納されます。  フォルダーには次のようなものがあります。<br /><br />- x64<br /><br /> - I386|  

##  <a name="a-namebkmkinstalla-how-to-install-updates"></a><a name="bkmk_Install"></a> 更新プログラムのインストール方法  
 更新プログラムをインストールするには、最初に、サイト サーバーに更新プログラムのバンドルをインストールする必要があります。 更新バンドルをインストールすると、その更新プログラムのインストール ウィザードが開始されます。 ウィザードでは次の操作が実行されます。  

-   更新プログラム ファイルの抽出  

-   展開の構成のサポート  

-   ローカル コンピューターのサーバー コンポーネントへの適用対象の更新プログラムのインストール  

サイト サーバーに更新プログラムのバンドルをインストールした後で、Configuration Manager を更新する修正プログラムのインストール方法について一般的なガイダンスを提供します。 次の表では、これらのさまざまなコンポーネントに対する更新操作について説明します。  

|コンポーネント|手順|  
|---------------|------------------|  
|サイト サーバー|リモート サイト サーバーに更新プログラムのバンドルを直接インストールしない場合、リモート サイト サーバーに更新プログラムを展開します。|  
|サイト データベース|リモート サイト サーバーに更新プログラムのバンドルを直接インストールしない場合、リモート サイト サーバー用に、サイト データベースに対する更新プログラムが含まれるサーバー更新プログラムを展開します。|  
|Configuration Manager コンソール|Configuration Manager コンソールの最初のインストール後、コンソールを実行する各コンピューターに Configuration Manager コンソールの更新プログラムをインストールできます。 Configuration Manager コンソールのインストール ファイルを変更して、コンソールの最初のインストール中に更新プログラムを適用することはできません。|  
|リモート SMS プロバイダー|更新プログラムのバンドルをインストールしたサイト サーバーとは別のコンピューターで実行する、SMS プロバイダーの各インスタンス用の更新プログラムをインストールします。|  
|Configuration Manager クライアント|Configuration Manager クライアントの最初のインストール後、クライアントを実行する各コンピューターに Configuration Manager クライアントの更新プログラムをインストールできます。|  

> [!NOTE]  
>  更新プログラムは、Configuration Manager クライアントを実行しているコンピューターのみに展開できます。  

 クライアント、Configuration Manager コンソール、または SMS プロバイダーを再インストールする場合、これらのコンポーネントの更新プログラムも再インストールする必要があります。  

 Configuration Manager の各コンポーネントに更新プログラムをインストールする詳細については、以下のセクションの情報を参照してください。  

###  <a name="a-namebkmkserversa-update-servers"></a><a name="bkmk_servers"></a> サーバーの更新  
 サーバーの更新には、構成に応じて、 **サイト**、 **site database**、 **SMS プロバイダー**のインスタンスを実行するコンピューターの更新が含まれます。  

####  <a name="a-namebkmksitea-update-a-site"></a><a name="bkmk_site"></a> サイトの更新  
 Configuration Manager サイトを更新するには、サイト サーバーに更新プログラムのバンドルを直接インストールするか、別のサイトに更新プログラムのバンドルをインストールした後で、サイト サーバーに更新プログラムを展開するかを選べます。  

 サイト サーバーに更新プログラムをインストールする場合、更新プログラムのインストール処理で、サイト システムの役割の更新など、更新プログラムの適用に必要な追加の操作が管理されます。 例外はサイト データベースです。 次のセクションで、サイト データベースの更新方法について説明します。  

####  <a name="a-namebkmkdatabasea-update-a-site-database"></a><a name="bkmk_database"></a> サイト データベースの更新  
 サイト データベースを更新する場合、インストール処理によって、サイト データベースで **update.sql** という名前のファイルが実行されます。 サイト データベースを自動的に更新する、または、後でサイト データベースを手動で更新するように、更新処理を構成できます。  

 **サイト データベースの自動更新**  

 サイト サーバーに更新プログラムのバンドルをインストールする場合、サーバーの更新プログラムをインストールするときにサイト データベースを自動的に更新できます。 この指定は、更新プログラムのバンドルをインストールするサイト サーバーにのみ適用され、リモート サイト サーバーに更新プログラムをインストールするために作成される展開には適用されません。  

> [!NOTE]  
>  サイト データベースを自動的に更新する場合、データベースがサイト サーバーとリモート コンピューターのどちらにあるかに関係なく、データベースが更新されます。  

> [!IMPORTANT]  
>  サイト データベースを更新する前に、サイト データベースのバックアップを作成します。 サイト データベースに対する更新プログラムをアンインストールすることはできません。 Configuration Manager のバックアップを作成する方法の詳細については、「[System Center Configuration Manager のバックアップと回復](../../../protect/understand/backup-and-recovery.md)」を参照してください。  

 **サイト データベースの手動更新**  

 サイト サーバーに更新プログラムのバンドルをインストールするときに、サイト データベースを自動的に更新しない場合、サーバーの更新プログラムによって、更新プログラムのバンドルを実行するサイト サーバーのデータベースは変更されません。 ただし、ソフトウェアの展開用に作成されたパッケージやインストールするパッケージを使用する展開では、常にサイト データベースが更新されます。  

> [!WARNING]  
>  更新プログラムに、サイト サーバーとサイト データベースの両方に対する更新プログラムが含まれている場合、サイト サーバーとサイト データベースの両方に対する更新が完了するまで、更新内容は機能しません。 更新プログラムがサイト データベースに適用されるまで、サイトがサポートされていない状態です。  

 **サイト データベースを手動で更新するには:**  

1.  サイト サーバーで、SMS_SITE_COMPONENT_MANAGER サービスを停止してから、SMS_EXECUTIVE サービスを停止します。  

2.  Configuration Manager コンソールを閉じます。  

3.  そのサイトのデータベースに対して **update.sql** という名前の更新スクリプトを実行します。 スクリプトを実行して SQL Server データベースを更新する方法の詳細については、サイト データベース サーバーで使用する SQL Server のバージョンに対応するドキュメントを参照してください。  

4.  前の手順で停止されたサービスを再起動します。  

5.  更新プログラムのバンドルをインストールすると、サイト サーバーの場所 **\\\\&lt;サーバー名\>\SMS_&lt;サイト コード\>\Hotfix\\&lt;サポート技術情報の記事\>\update.sql** に **update.sql** が抽出されます。  

####  <a name="a-namebkmkprovidera-update-a-computer-that-runs-the-sms-provider"></a><a name="bkmk_provider"></a> SMS プロバイダーを実行するコンピューターの更新  
 SMS プロバイダーの更新プログラムが含まれた更新バンドルをインストールした後で、SMS プロバイダーを実行する各コンピューターに更新プログラムを展開する必要があります。 この唯一の例外は、更新バンドルをインストールしたサイト サーバーに以前にインストールされた SMS プロバイダーのインスタンスです。 サイト サーバーの SMS プロバイダーのローカル インスタンスは、更新バンドルをインストールすると更新されます。  

 SMS プロバイダーを削除してからコンピューターに再インストールする場合は、次に、そのコンピューターに SMS プロバイダーの更新プログラムを再インストールする必要があります。  

###  <a name="a-namebkmkclientsa-update-clients"></a><a name="BKMK_clients"></a> クライアントの更新  
 Configuration Manager の更新プログラムを含む更新プログラムをインストールするときには、更新のインストールでクライアントを自動的にアップグレードするオプション、または後でクライアントを手動でアップグレードするオプションが表示されます。 自動クライアント アップグレードの詳細については、「 [Windows コンピューター用クライアントをアップグレードする方法](https://technet.microsoft.com/library/mt627885.aspx)を更新する修正プログラムのインストール方法について一般的なガイダンスを提供します。  

 Updates Publisher またはソフトウェア展開パッケージを使って更新プログラムを展開したり、クライアントごとに更新プログラムを手動でインストールしたりすることもできます。 展開を使用して更新プログラムをインストールする方法については、このトピックの「 [Configuration Manager の更新プログラムの展開](#BKMK_Deploy) 」セクションを参照してください。  

> [!IMPORTANT]  
>  クライアントの更新プログラムと、サーバーの更新プログラムが含まれた更新バンドルをインストールするときには、クライアントが割り当てられているプライマリ サイトにもサーバーの更新プログラムをインストールしてください。  

クライアントの更新プログラムを手動でインストールするには、各 Configuration Manager クライアントで **Msiexec.exe** を実行し、プラットフォーム固有のクライアントの更新プログラム .msp ファイルを参照する必要があります。  

 たとえば、クライアントの更新プログラムに次のコマンド ラインを使用できます。 このコマンド ラインは、クライアント コンピューターで MSIEXEC を実行し、サイト サーバーで更新プログラムのバンドルから抽出された .msp ファイルを参照します。**msiexec.exe /p \\\\&lt;サーバー名\>\SMS_&lt;サイトコード\>\Hotfix\\&lt;サポート技術情報の記事番号\>\Client\\&lt;プラットフォーム\>\\&lt;msp\> /L\*v &lt;ログ ファイル\>REINSTALLMODE=mous REINSTALL=ALL**  

###  <a name="a-namebkmkconsolea-update-configuration-manager-consoles"></a><a name="BKMK_console"></a> Configuration Manager コンソールの更新  
 Configuration Manager コンソールを更新するには、コンソールのインストールが終了した後で、コンソールを実行するコンピューターに更新プログラムをインストールする必要があります。  

> [!IMPORTANT]  
>  Configuration Manager コンソールの更新プログラムと、サーバーの更新プログラムが含まれた更新バンドルをインストールするときに、Configuration Manager コンソールなどのコンポーネントに更新プログラムをインストールできます。  

更新するコンピューターで Configuration Manager クライアントを実行している場合:  

-   展開を使用して更新プログラムをインストールできます。 展開を使用して更新プログラムをインストールする方法については、このトピックの「 [Configuration Manager の更新プログラムの展開](#BKMK_Deploy) 」セクションを参照してください。  

-   クライアント コンピューターに直接ログオンしている場合は、インストールを対話的に実行することができます。  

-   コンピューターごとに更新プログラムを手動でインストールできます。 Configuration Manager コンソールの更新プログラムを手動でインストールするには、Configuration Manager コンソールを実行する各コンピューターで Msiexec.exe を実行して、Configuration Manager コンソール更新プログラムの .msp ファイルを参照する必要があります。  

たとえば、次のコマンド ラインを使用して Configuration Manager コンソールを更新できます。 このコマンド ラインは、クライアント コンピューターで MSIEXEC を実行し、サイト サーバーで更新プログラムのバンドルから抽出された .msp ファイルを参照します。**msiexec.exe /p \\\\&lt;サーバー名\>\SMS_&lt;サイト コード\>\Hotfix\\&lt;サポート技術情報の記事番号\>\AdminConsole\\&lt;プラットフォーム\>\\&lt;msp\> /L\*v &lt;ログ ファイル\>REINSTALLMODE=mous REINSTALL=ALL**  

##  <a name="a-namebkmkdeploya-deploy-updates-for-configuration-manager"></a><a name="BKMK_Deploy"></a> Configuration Manager の更新プログラムの展開  
 サイト サーバーに更新バンドルをインストールしたら、以下の 3 つの方法のいずれかで他のコンピューターに更新プログラムを展開できます。  

###  <a name="a-namebkmkdeployscupa-use-updates-publisher-2011-to-install-updates"></a><a name="BKMK_DeploySCUP"></a> Updates Publisher 2011 を使用した更新プログラムのインストール  
 サイト サーバーに更新バンドルをインストールすると、対象コンピューターに更新プログラムを展開するのに使用できる Updates Publisher のカタログ ファイルがインストール ウィザードによって作成されます。 オプション **[パッケージとプログラムを使用して、この更新プログラムを展開する]**を更新する修正プログラムのインストール方法について一般的なガイダンスを提供します。  

 Updates Publisher のカタログは **SCUPCatalog.cab** という名前で、更新バンドルを実行しているコンピューター上の場所 **\\\\&lt;サーバー名\>\SMS_&lt;サイト コード\>\Hotfix\\&lt;サポート技術情報の記事番号\>\SCUP\SCUPCatalog.cab** にあります。  

> [!IMPORTANT]  
>  SCUPCatalog.cab ファイルは、更新バンドルがインストールされているサイト サーバー固有のパスを使用して作成されるため、他のサイト サーバーで使用することはできません。  

 ウィザードが終了したら、Updates Publisher にカタログをインポートしてから、Configuration Manager のソフトウェア更新プログラムを使用して更新プログラムを展開できます。 Updates Publisher の詳細については、System Center 2012 の TechNet ライブラリの「[Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkID=83449)」を参照してください。  

 Updates Publisher に SCUPCatalog.cab ファイルをインポートして更新プログラムを発行するには、次の手順に従います。  

##### <a name="to-import-the-updates-to-updates-publisher-2011"></a>Updates Publisher 2011 に更新プログラムをインポートするには  

1.  Updates Publisher コンソールを起動し、**[インポート]** をクリックします。  

2.  ソフトウェア更新プログラム カタログのインポート ウィザードの [ **インポートの種類** ] ページで、[ **インポートするカタログへのパスを指定**] を選択してから、SCUPCatalog.cab ファイルを指定します。  

3.  [ **次へ**] をクリックしてから、もう一度 [ **次へ** ] をクリックします。  

4.  [ **セキュリティ警告 - カタログ検証** ] ダイアログ ボックスで、[ **同意する**] をクリックします。 終了したら、ウィザードを閉じます。  

5.  Updates Publisher コンソールで、展開する更新プログラムを選んでから、**[発行]** をクリックします。  

6.  ソフトウェア更新プログラムの発行ウィザードの [ **発行オプション** ] ページで、[ **完全なコンテンツ**] を選択してから、[ **次へ**] をクリックします。  

7.  ウィザードを完了して更新プログラムを発行します。  

###  <a name="a-namebkmkdeployswdista-use-software-deployment-to-install-updates"></a><a name="BKMK_DeploySWDist"></a> ソフトウェア展開を使用した更新プログラムのインストール  
 プライマリ サイトまたは中央管理サイトのサイト サーバーに更新バンドルをインストールするときに、ソフトウェア展開の更新プログラム パッケージを作成するようにインストール ウィザードを構成できます。 その後で、更新するコンピューターのコレクションに各パッケージを展開できます。  

 ソフトウェア展開パッケージを作成するには、ウィザードの [ソフトウェア更新プログラムの展開の構成] ページで、更新する更新プログラム パッケージの各種類のチェック ボックスをオンにします。 **** 使用可能な種類には、サーバー、Configuration Manager コンソール、クライアントを含めることができます。 選択した更新プログラムの種類ごとに、別々のパッケージが作成されます。  

> [!NOTE]  
>  サーバーのパッケージには、次のコンポーネントの更新プログラムが含まれます。  
>   
>  -   サイト サーバー  
>  -   SMS プロバイダー  
>  -   サイト データベース  

 次に、ウィザードの [ **ソフトウェア更新プログラムの展開方法の構成** ] ページで、オプション [ **ソフトウェア配布を使用する**] を選択します。 選択すると、ウィザードによってソフトウェア展開パッケージが作成されます。  

 ウィザードが完了したら、Configuration Manager コンソールで作成したパッケージを **[ソフトウェア ライブラリ]** ワークスペースの **[パッケージ]** ノードに表示することができます。 その後、標準のプロセスを使用して Configuration Manager クライアントにソフトウェア パッケージを展開できます。 クライアントでパッケージを実行すると、クライアント コンピューターの Configuration Manager の該当するコンポーネントに更新プログラムがインストールされます。  

 Configuration Manager クライアントへのパッケージの展開方法については、「[Packages and programs in System Center Configuration Manager](../../../apps/deploy-use/packages-and-programs.md)」(System Center Configuration Manager のパッケージとプログラム) を参照してください。  

###  <a name="a-namebkmkdeploycollectionsa-create-collections-for-deploying-updates-to-configuration-manager"></a><a name="BKMK_DeployCollections"></a> Configuration Manager に更新プログラムを展開するためのコレクションの作成  
 該当するクライアントに特定の更新プログラムを展開できます。 Configuration Manager の複数の異なるコンポーネントのデバイス コレクションを作成するときに、以下の情報をご参照ください。  

|Configuration Manager のコンポーネント|手順|  
|----------------------------------------|------------------|  
|中央管理サイト サーバー|ダイレクト メンバーシップのクエリを作成して、中央管理サイト サーバー コンピューターを追加します。|  
|すべてのプライマリ サイト サーバー|ダイレクト メンバーシップのクエリを作成して、各プライマリ サイト サーバー コンピューターを追加します。|  
|すべてのセカンダリ サイト サーバー|ダイレクト メンバーシップのクエリを作成して、各セカンダリ サイト サーバー コンピューターを追加します。|  
|すべての x86 クライアント|次のクエリ条件でコレクションを作成します。<br /><br /> **Select \* from SMS_R_System inner join SMS_G_System_SYSTEM on SMS_G_System_SYSTEM.ResourceID = SMS_R_System.ResourceId where SMS_G_System_SYSTEM.SystemType = "X86-based PC"**|  
|すべての x64 クライアント|次のクエリ条件でコレクションを作成します。<br /><br /> **Select \* from SMS_R_System inner join SMS_G_System_SYSTEM on SMS_G_System_SYSTEM.ResourceID = SMS_R_System.ResourceId where SMS_G_System_SYSTEM.SystemType = "X64-based PC"**|  
|Configuration Manager コンソールを実行しているすべてのコンピューター|ダイレクト メンバーシップのクエリを作成して、各コンピューターを追加します。|  
|SMS プロバイダーのインスタンスを実行するリモート コンピューター|ダイレクト メンバーシップのクエリを作成して、各コンピューターを追加します。|  

> [!NOTE]  
>  サイト データベースを更新するには、そのサイトのサイト サーバーに更新プログラムを展開します。  

 コレクションを作成する方法については、「[System Center Configuration Manager でコレクションを作成する方法](../../../core/clients/manage/collections/create-collections.md)」を参照してください。  



<!--HONumber=Nov16_HO1-->


