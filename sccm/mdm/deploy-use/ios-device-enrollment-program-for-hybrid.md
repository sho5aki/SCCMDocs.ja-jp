---
title: "Configuration Manager とのハイブリッド展開に対応する iOS Device Enrollment Program (DEP) 登録"
description: "Configuration Manager と Intune のハイブリッド展開に対応するために、iOS Device Enrollment Program (DEP) 登録を有効にします。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 78d44adc-9b1c-4bc6-b72d-e93873916ea6
caps.latest.revision: 9
author: NathBarn
ms.author: nathbarn
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 730b0e6b0ad9eb0ee3bf58c9419920c3a28a27d1

---
# <a name="ios-device-enrollment-program-dep-enrollment-for-hybrid-deployments-with-configuration-manager"></a>Configuration Manager とのハイブリッド展開に対応する iOS Device Enrollment Program (DEP) 登録

*適用対象: System Center Configuration Manager (Current Branch)*

企業は、Apple のデバイス登録プログラムで iOS デバイスを購入してから、Microsoft Intune を使用してそのデバイスを管理することができます。 Apple Device Enrollment Program (DEP) を使用して企業所有の iOS デバイスを管理するには、企業は Apple の手順を実行してプログラムに参加し、そのプログラムを使用してデバイスを取得する必要があります。 そのプロセスの詳細については、  [https://deployで管理することができます。appleで管理することができます。com](https://deploy.apple.com)で管理することができます。 このプログラムの利点として、各デバイスをコンピューターに USB 接続することなく、デバイスを楽に設定できる点があります。  

 DEP を使用して企業所有の iOS デバイスを登録するには、Apple の DEP トークンが必要です。 このトークンにより、Intune は企業所有の DEP 参加デバイスに関する情報を同期できるようになります。 また、Intune は Apple に登録プロファイルをアップロードし、デバイスをそれらのプロファイルに割り当てられるようになります。  

## <a name="apple-dep-enrollment-for-ios-devices"></a>iOS デバイスの Apple DEP 登録  
 次に、Apple DEP で購入した iOS デバイスを、Intune が管理する企業所有のデバイスに指定する手順について説明します。 ユーザーがデバイスの電源を初めて入れると、DEP 管理プロファイルを受信し、セットアップ アシスタントが実行され、管理対象になります。  

###  <a name="enable-dep-enrollment-in-configuration-manager-with-intune"></a>Configuration Manager と Intune で DEP 登録を有効にする  

1.  **Configuration Manager を使用して iOS デバイス管理を開始する**   
    iOS Device Enrollment Program (DEP) デバイスを登録する前に、[iOS の登録をサポートする手順](../deploy-use/setup-hybrid-mdm.md#ios-and-mac-enrollment-setup)を含む「[Set up Hybrid mobile device management](../../mdm/deploy-use/setup-hybrid-mdm.md)」(ハイブリッド モバイル デバイス管理のセットアップ) の手順を完了する必要があります。

2.  **DEP トークン要求の作成**   
    Configuration Manager コンソールの **[管理]** ワークスペースで、**[階層の構成]**、**[クラウド サービス]** の順に展開してから、**[Windows Intune サブスクリプション]** をクリックします。 **[ホーム]** タブの **[DEP トークン要求の作成]** 、 **[参照]** の順にクリックして、DEP トークン要求をダウンロードする場所を指定してから、 **[ダウンロード]**をクリックします。 DEP トークン要求 (.pem) ファイルをローカルに保存します。 .pem ファイルは、Apple Device Enrollment Program ポータルから信頼されたトークン (.p7m) を要求するために使用します。  

3.  **Device Enrollment Program トークンを取得する**   
     [Device Enrollment Program ポータル](https://deploy.apple.com) (https://deploy.apple.com) に移動し、会社の Apple ID でサインインします。 この Apple ID は、将来 DEP トークンを更新するために使用する必要があります。  

    1.  [Device Enrollment Program ポータル](https://deploy.apple.com)で **[Device Enrollment Program]** > **[Manage Servers] (サーバーの管理)** に移動して、**[Add MDM Server]** (MDM サーバーの追加) をクリックします。  

    2.  **MDM サーバー名**を入力し、 **[Next]**をクリックします。 サーバー名は、自分が MDM サーバーを識別できるようにするための名前です。 Intune または Configuration Manager サーバーの名前または URL ではありません。  

    3.  **[Add <サーバー名\>]** (<サーバー名> の追加) ダイアログ ボックスが開きます。 **[ファイルの選択…] をクリックして、** 前の手順で作成した .pem ファイルをアップロードしてから、**[Next]** (次へ) をクリックします。  

    4.  **[Add <サーバー名\>]** (<サーバー名> の追加) ダイアログ ボックスに、**[Your Server Token]** (サーバー トークン) リンクが表示されます。 サーバー トークン (で管理することができます。p7m) ファイルをコンピューターにダウンロードしたら、 **[完了]**で管理することができます。  

     この証明書 (.p7m) ファイルは、Intune と Apple の Device Enrollment Program サーバーとの間に信頼関係を確立するために使用されます。  

4.  **DEP トークンの Configuration Manager への追加**   
    Configuration Manager コンソールの **[管理]** ワークスペースで、**[階層の構成]** を展開してから、**[Windows Intune サブスクリプション]** をクリックします。 **[ホーム]** タブの **[プラットフォームの構成]** をクリックし、 **[iOS]**をクリックします。 **[デバイスの登録プログラムを有効にする]**を選択して、証明書 (.p7m) ファイルを参照してから、 **[開く]**、 **[アップロード]**、 **[OK]**の順にクリックします。  

#### <a name="set-up-enrollment-for-apple-device-enrollment-program-dep-ios-devices"></a>Apple Device Enrollment Program (DEP) iOS デバイスの登録をセットアップします。  

1.  **業務用デバイスの登録ポリシーを追加する**   
    Configuration Manager コンソールの **[資産とコンプライアンス]** ワークスペースで、**[概要]**、**[すべての企業所有のデバイス]**、**[iOS]** の順に展開してから、**[登録プロファイル]** をクリックします。 **[ホーム]** タブの **[プロファイルの作成]** をクリックして、プロファイルの作成ウィザードを開きます。 次の各ページで、設定を構成します。  

    1.  **[全般]** ページで、次の情報を指定してから、 **[次へ]**をクリックします。  

        -   **名前** – デバイス登録プロファイルの名前を指定します。 (この機能は、ユーザーに表示されません)  

        -   **説明** - デバイス登録プロファイルの説明。 (この機能は、ユーザーに表示されません)  

        -   **[ユーザー アフィニティ]** – デバイスの登録方法を指定します。 「[User affinity for hybrid managed devices in Configuration Manager](../../mdm/deploy-use/user-affinity-for-hybrid-managed-devices.md)」(Configuration Manager でのハイブリッド管理のデバイス向けユーザー アフィニティ) を参照してください。  

            -   **[ユーザー アフィニティの入力を求める]**: 初回セットアップ時にデバイスをユーザーに関連付ける必要があります。その後、デバイスはそのユーザーとして企業のデータや電子メールにアクセスすることが許可されます。  ユーザーに属していて (アプリケーションをインストールするために) 会社のポータルを利用する必要がある DEP 管理対象デバイスのユーザー アフィニティを構成する必要があります。  

            > [!NOTE]
            > ユーザー アフィニティが設定された DEP でユーザー トークンを要求するには、ADFS WS-Trust 1.3 Username/Mixed エンドポイントを有効にする必要があります。

            -   **[ユーザー アフィニティなし]**: デバイスは、ユーザーと関連付けられません。 このデバイス関連付け情報を使用すると、ローカルのユーザー データにアクセスしなくてもタスクを実行できます。 ユーザーへの関連付けが必要なアプリが動作しません。  

    2.  On the **[Device Enrollment Program]** ページで、以下の情報を指定してから、 **[次へ]**で管理することができます。  

        -   **部門** - アクティブ化中にユーザーが [構成について] をタップすると表示されます  

        -   **サポート電話番号** - アクティブ化中にユーザーが **[ヘルプが必要ですか]** ボタンをクリックすると表示されます  

        -   **準備モード** - この状態はアクティブ化中に設定されます。デバイスの工場出荷時設定以外では変更できません。  

            -   **監督解除済み** - 管理機能が制限されます  

            -   **監督下** - より多くの管理オプションが使用可能になり、既定で [アクティブ化ロック] は無効になります  

        -   **デバイスへの登録プロファイルのロック** - この状態はアクティブ化中に設定されます。デバイスの工場出荷時設定以外では変更できません  

            -   **無効** - **[設定]** メニューから管理プロファイルを削除できます  

            -   有効 - (**[準備モード]** = **[監督下]** にする必要があります) 管理プロファイルの削除を許可する iOS 設定を無効にします  

    3.  **[セットアップ アシスタント]** ページで、デバイスの電源が初めてオンになったときに起動する iOS セットアップ アシスタントをカスタマイズする設定を構成してから、 **[次へ]**をクリックします。 設定は次のとおりです。  

        -   **パスコード** - アクティブ化時にパスコードの入力を求めます。 デバイスがセキュリティで保護される場合や、他の何らかの方法 (デバイスを 1 つのアプリに制限するキオスク モードなど) でアクセスが制御されている場合を除き、パスコードは常に必須にしてください。  

        -   **位置情報サービス** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってサービスがプロンプトされます  

        -   **復元** - 有効にすると、アクティブ化時に、セットアップ アシスタントによって iCloud バックアップがプロンプトされます  

        -   **Apple ID** - Intune でインストールされるアプリを含め、iOS App Store アプリをダウンロードする際に Apple ID が必須になります。 有効にして、Intune で ID を指定せずにアプリをインストールしようとすると、Apple ID の入力が求められます。  

        -   **使用条件** - 有効にすると、アクティブ化時に、セットアップ アシスタントによって Apple の使用条件に同意するように求められます  

        -   **Siri** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます  

        -   **Apple に診断データを送信する** - 有効にすると、アクティブ化時に、セットアップ アシスタントによってこのサービスがプロンプトされます  

    4.  **[追加の管理]** ページで、追加の管理設定のために USB 接続の使用を許可するかどうかを指定します。 **[証明書が必要]**を選択する場合、このプロファイルに使用する Apple Configurator 管理証明書をインポートする必要があります。  **[許可しない]** に設定すると、ファイルの iTunes との同期と Apple Configurator 経由の管理が実行されなくなります。 **[許可しない]** を使用して証明書ありまたは証明書なしの手動の展開を許可するのではなく、[許可しない] を選択して、Apple Configurator からその他の構成をエクスポートし、カスタム iOS 構成プロファイルとして展開することをお勧めします。  

        -   **許可しない** - デバイスの USB 経由の通信を禁止します (ペアリングを無効にします)  

        -   **許可する** - デバイスに PC または Mac との USB 接続での通信を許可します  

        -   **証明書が必要** - 登録プロファイルにインポートされた証明書を使用した Mac とのペアリングを許可します  

2.  **DEP デバイスを管理対象にする**   
     [Device Enrollment Program ポータル](https://deploy.apple.com) (https://deploy.apple.com) に移動し、会社の Apple ID でサインインします。  **[Deployment Program]** > **[Device Enrollment Program]** > **[デバイスの管理]**で管理することができます。 **デバイスの選択**方法を指定し、デバイス情報を入力して、デバイスの **シリアル番号**、 **注文番号**、または **CSV ファイルのアップロード**で詳細を指定します。 次に、**[Assign to Server]** (サーバーに割り当て) を選択し、手順 3 で指定した <*サーバー名*> を選択して、**[OK]** をクリックします。  

3.  **DEP で管理されたデバイスの同期**   
     **[資産とコンプライアンス]** ワークスペースで、 **[すべての企業所有のデバイス]** > **[iOS]** > **[デバイス情報]**で管理することができます。 **[ホーム]** タブの **[DEP の同期]**をクリックします。 同期要求が Apple に送信されます。 同期が完了すると、DEP で管理されたデバイスが表示されます。 管理されたデバイスの **登録状態** は、デバイスの電源がオンになり、セットアップ アシスタントを実行してデバイスを登録するまでは **[未接続]** となります。  

4.  **デバイスのユーザーへの配布**   
    これで、会社が所有するデバイスをユーザーに付与できるようになりました。 iOS デバイスの電源をオンにすると、iOS デバイスが Intune の管理対象として登録されます。



<!--HONumber=Nov16_HO1-->


