---
title: Upgrade Readiness | System Center Configuration Manager
description: "Upgrade Readiness と Configuration Manager を統合します。 管理コンソールでアップグレードの互換性データにアクセスします。 アップグレードまたは修復対象のデバイスを指定します。"
keywords: 
author: brenduns
ms.author: brenduns
manager: angerobe
ms.date: 3/1/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-client
ms.assetid: 68407ab8-c205-44ed-9deb-ff5714451624
ms.translationtype: Human Translation
ms.sourcegitcommit: dcbcd57b95f304f007e92ebe2b9aeefb4b579662
ms.openlocfilehash: 986d0446209f6e7eac1b681066d1b2e2305e1975
ms.contentlocale: ja-jp
ms.lasthandoff: 05/17/2017


---

# <a name="integrate-upgrade-readiness-with-system-center-configuration-manager"></a>Upgrade Readiness と System Center Configuration Manager との統合
Upgrade Readiness (旧称 Upgrade Analytics) を使用すると、デバイスの準備と Windows 10 との互換性を評価および分析して、簡単かつスムーズなアップグレードが可能になります。 Upgrade Readiness と System Center Configuration Manager を統合することで、クライアントは Configuration Manager 管理コンソールでアップグレードの互換性データにアクセスできるようになります。 その後、デバイス リストからアップグレードまたは修復対象のデバイスを指定できます。

Upgrade Readiness は、Microsoft Operations Management Suite (OMS) のソリューションの 1 つです。 Upgrade Readiness の詳細については、「[Get started with Upgrade Readiness](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness)」(Upgrade Readiness の概要) を参照してください。

## <a name="configure-clients"></a>クライアントを構成する

クライアントが Upgrade Readiness にデータを確実に提供できるようにするために実行する必要があるいくつかの構成手順を以下に示します。

-  「[組織内の Windows 利用統計情報の構成](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization)」の説明に従って、クライアントの製品利用統計情報設定を構成します。
-  「[Get started with Upgrade Readiness](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness)」 (Upgrade Readiness の概要) の「*Deploy the compatibility update and related KBs*」 (互換性更新プログラムおよび関連 KB の展開) の説明に従って、KB をインストールします。

    > [!NOTE]
    > クライアントのセットアップ タスクの多くを自動化するスクリプトをダウンロードすることができます。 スクリプトについては、「[Get started with Upgrade Readiness](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness)」 (Upgrade Readiness の概要) の「*Run the Upgrade Readiness deployment script*」 (Upgrade Readiness 展開スクリプトの実行) を参照してください。

## <a name="create-a-connection-to-upgrade-readiness"></a>Upgrade Readiness への接続を作成する

### <a name="prerequisites"></a>必要条件

- 接続を追加するために、Configuration Manager 環境で最初に[サービス接続ポイント](/sccm/core/servers/deploy/configure/about-the-service-connection-point)を[オンライン モード](https://azure.microsoft.com/en-us/documentation/articles/resource-group-create-service-principal-portal/)で構成する必要があります。 接続を環境に追加する場合、このサイト システムの役割を実行するマシンに Microsoft Monitoring Agent もインストールされます。
- "Web アプリケーションや Web API" 管理ツールとして Configuration Manager を登録し、[この登録のクライアント ID](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications/) を取得します。
- Azure Active Directory で、登録済み管理ツールのクライアント キーを作成します。
- 「[Configuration Manager に OMS へのアクセス許可を付与する](https://azure.microsoft.com/en-us/documentation/articles/log-analytics-sccm/#provide-configuration-manager-with-permissions-to-oms)」の説明に従って、Azure 管理ポータルで、登録済みの Web アプリに OMS へのアクセス権を指定します。

    > [!IMPORTANT]
    > OMS へのアクセス権を構成する場合は、必ず、**共同作成者**ロールを選択し、登録済みアプリのリソース グループへのアクセス権を割り当ててください。

### <a name="create-the-connection"></a>接続を作成する

1.  Configuration Manager コンソールで、**[管理]** > **[クラウド サービス]** > **[Upgrade Readiness コネクタ]** > **[Upgrade Analytics への接続を作成します]** の順に選択し、**[Upgrade Analytics の接続を追加ウィザード]** を起動します。
3.  **[Azure Active Directory]** 画面で、**[テナント]**、**[クライアント ID]**、**[クライアントの秘密鍵]** を指定し、**[次へ]** を選択します。
4.  **[Upgrade Readiness]** 画面で、**[Azure サブスクリプション]**、**[Azure リソース グループ]**、および **[Operations Management Suite ワークスペース]** に入力し、接続設定を指定します。
5.  **[概要]** 画面で、**[次へ]** の接続設定を確認します。

    > [!NOTE]
    > Upgrade Readiness を階層の最上位サイトに接続する必要があります。 Upgrade Readiness をスタンドアロン プライマリ サイトに接続し、環境に中央管理サイトを追加する場合は、OMS 接続を削除し、新しい階層内に OMS 接続を再作成する必要があります。

### <a name="complete-upgrade-readiness-tasks"></a>Upgrade Readiness のタスクの実行  

Configuration Manager で接続を作成したら、「[Get started with Upgrade Readiness](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness)」 (Upgrade Readiness の概要) の説明に従って、以下のタスクを実行します。  

1. OMS ワークスペースに Upgrade Readiness サービスを追加します。  
2. 商用 ID を生成します。  
3. Upgrade Readiness をサブスクライブします。   

## <a name="use-the-upgrade-readiness-deployment-script"></a>Upgrade Readiness 展開スクリプトを使用する  

Upgrade Readiness タスクの多くを自動化し、Microsoft **Upgrade Readiness 展開スクリプト**を使用してデータ共有に関する問題のトラブルシューティングを行うことができます。  
Upgrade Readiness 展開スクリプトは以下のことを行います。  

- 商用 ID キー、CommercialDataOptIn キー、RequestAllAppraiserVersions キーを設定します。  
- ユーザーのコンピューターが Microsoft にデータを送信できることを確認します。  
- コンピューターの再起動が保留されているかどうかを確認します。   
- 最新バージョンの KB パッケージ 10.0.x (10.0.14913 以降のリリースが必要) がインストールされていることを検証します。  
- 有効な場合は、トラブルシューティングの詳細モードをオンにします。  
- Microsoft が組織でのアップグレードの準備を評価するのに必要な製品利用統計情報データの収集を開始します。  
- 有効な場合は、コマンド ウィンドウにスクリプトの進行状況を表示して問題 (ステップごとの成功または失敗) を確認できるようにし、ログ ファイルへの書き込みを行います。  

### <a name="to-run-the-upgrade-readiness-deployment-script"></a>Upgrade Readiness 展開スクリプトを実行するには、次のようにします。  

1. [Upgrade Readiness 展開スクリプト](https://go.microsoft.com/fwlink/?LinkID=822966&clcid=0x409)をダウンロードし、Upgrade Readiness.zip を抽出します。 トラブルシューティング モードでスクリプトを実行する予定の場合にのみ、**診断**フォルダー内のファイルが必要になります。  
2. RunConfig.bat で以下のパラメーターを編集します。  
- ログ情報の格納場所 ( 例: %SystemDrive%\URDiagnostics ログ情報は、リモート ファイル共有またはローカル ディレクトリに格納できます。 スクリプトで指定されたパスのログ ファイルを作成できない場合は、Windows ディレクトリのドライブにログ ファイルが作成されます。  
- 商用 ID キー。  
- 既定では、スクリプトはコンソールとログ ファイルの両方にログ情報を送信します。 既定の動作を変更するには、次のオプションのいずれかを使用します。  
    - logMode = 0: コンソールにのみログを記録  
    - logMode = 1: ファイルとコンソールにログを記録  
    - logMode = 2: ファイルにのみログを記録  
    - トラブルシューティングを行う場合は、**isVerboseLogging** を **$true** に設定し、問題の診断に役立つログ情報を生成します。 既定では、**isVerboseLogging** は **$false** に設定されます。 診断フォルダーが、このモードを使用するためのスクリプトと同じディレクトリにインストールされていることを確認してください。  
    - コンピューターを再起動する必要がある場合はユーザーに通知します。 既定では、オフに設定されます。  

3. RunConfig.bat でのパラメーターの編集が終了したら、管理者としてスクリプトを実行します。  


## <a name="view-microsoft-upgrade-readiness-properties-in-configuration-manager"></a>Configuration Manager で Microsoft Upgrade Readiness プロパティを表示する  

1.  Configuration Manager コンソールで、**[クラウド サービス]** に移動し、**[OMS コネクタ]** を選択して **[OMS 接続のプロパティ]** ページを開きます。  

2.  このページには、2 つのタブがあります。
  * **[Azure Active Directory]** タブには **[テナント]**、**[クライアント ID]**、**[Client secret key expiration]** (クライアント秘密鍵の期限切れ) が表示され、期限切れになった場合に、**[クライアント秘密鍵]** を **[確認]** できます。
  * **[Upgrade Readiness]** タブには、**[Azure サブスクリプション]**、**[Azure リソース グループ]**、および **[Operations Management Suite ワークスペース]** が表示されます。

## <a name="view-and-use-the-upgrade-information"></a>アップグレード情報を表示して使用する

Upgrade Readiness と Configuration Manager を統合したら、クライアントでのアップグレード準備の分析を表示して操作を実行できます。

1. Configuration Manager コンソールで、**[監視]** > **[概要]** > **[Upgrade Readiness]** の順に選択します。
2. アップグレードの準備状態、製品利用統計情報をレポートしている Windows デバイスの割合を含むデータを確認します。
3. 特定のコレクションでデバイス用のデータを表示するためにダッシュボードをフィルター処理することができます。
4. 特定の準備状態にあるデバイスを表示し、そのデバイスの動的コレクションを作成して、準備ができている場合はデバイスをアップグレードできるようにします。また、準備状態になるように操作を実行することもできます。

