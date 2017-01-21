---
title: "System Center Configuration Manager の Technical Preview 1610 の機能"
description: "System Center Configuration Manager の Technical Preview バージョン 1610 で使用できる機能について説明します。"
ms.custom: na
ms.date: 10/21/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: 8b31fd3e-875a-4a31-9498-5b050aadce32
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: c9fe6961a63495d08a3e58e3ddf46c5d316e2613
ms.openlocfilehash: 865b5078282bf240aa6a2aef5cb2662f2471fb71

---
# <a name="capabilities-in-technical-preview-1610-for-system-center-configuration-manager"></a>System Center Configuration Manager の Technical Preview 1610 の機能

*適用対象: System Center Configuration Manager (Technical Preview)*



この記事では、System Center Configuration Manager の Technical Preview バージョン 1610 で使用できる機能について説明します。 このバージョンをインストールして更新し、新機能を Configuration Manager の Technical Preview サイトに追加できます。      このバージョンの Technical Preview をインストールする前に、説明のトピック「[System Center Configuration Manager の Technical Preview](../../core/get-started/technical-preview.md)」を確認して、Technical Preview の使用に関する一般的な要件と制限、バージョン間の更新方法、および Technical Preview の機能に関するフィードバックを提供する方法について理解してください。    


**このバージョンでお試しいただける新機能を次に示します。**  
## <a name="filter-by-content-size-in-automatic-deployment-rules"></a>自動展開規則でコンテンツのサイズでフィルター処理する
自動展開規則でソフトウェア更新プログラムのコンテンツのサイズでフィルター処理できるようになりました。 たとえば、**コンテンツ サイズ (KB)** フィルターを **< 2048** に設定して、2 MB 未満のソフトウェア更新プログラムだけをダウンロードできます。 ネットワーク帯域幅が制限されている場合に、下位レベルの簡素化された Windows サービスのよりよいサポートのため、このフィルターを使用して、サイズの大きいソフトウェア更新プログラムが自動的にダウンロードされるのを防止します。 詳細については、「[Configuration Manager and Simplified Windows Servicing on Down Level Operating Systems](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/)」(Configuration Manager と下位レベルのオペレーティング システムでの簡素化された Windows サービス) を参照してください。

#### <a name="to-configure-the-content-size-field"></a>[コンテンツ サイズ] フィールドを構成するには
[**コンテンツ サイズ (KB)**] フィールドを構成するには、ADR を作成する際に、自動展開規則の作成ウィザードの [**ソフトウェアの更新**] ページに移動するか、既存の ADR のプロパティの [**ソフトウェアの更新**] タブに移動します。

![[コンテンツ サイズ] フィールド](media/contentsizefield.png)

## <a name="improved-functionality-for-required-software-dialogs"></a>必要なソフトウェア ダイアログの機能向上
ユーザーが必要なソフトウェアを受け取ったときに、[**次の時間が経過したら再通知する**] 設定で、次のドロップダウン リストから値を選択できます。
- [後で]: クライアント エージェント設定で構成されている通知の設定に基づいて通知をスケジュールすることを指定します。
- [定時]: 選択した時間後にもう一度通知を表示するように指定します。 たとえば、ユーザーが 30 分を選択した場合、その通知が 30 分後にもう一度表示されます。

![クライアント エージェント設定の [コンピューター エージェント] ページ](media/computeragentsettings.png)

最大の再通知時間は、展開のタイムラインに沿って、クライアント エージェント設定で毎回構成された値に常に基づきます。 たとえば、[コンピューター エージェント] ページで [**展開期限まで 24 時間以上の場合に、ユーザーに通知する間隔 (時間)**] 設定が 10 時間に設定されていて、ダイアログが起動する期限まで 24 時間以上ある場合は、ユーザーに最大で 10 時間以内の再通知を設定するオプションが表示されます。 期限が近づくと、展開タイムラインの各コンポーネントに関連するクライアント エージェント設定に合わせて、ダイアログに表示されるオプションが減ります。

さらに、オペレーティング システムを展開するタスク シーケンスなど、危険度の高い展開に対しては、エンドユーザー通知のエクスペリエンスがより煩わしいものになりました。 一時的なタスク バーの代わりに、重要なソフトウェア メンテナンスが必要なことがユーザーに通知されるたび、次のようなダイアログ ボックスがユーザーのコンピューターに表示されます。

![必要なソフトウェアのダイアログ](media/requiredsoftwaredialog.png)


詳細情報:
- [危険度の高い展開を管理するための設定](../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [クライアント設定を構成する方法](../clients/deploy/configure-client-settings.md)

## <a name="deny-previously-approved-application-requests"></a>以前に承認されたアプリケーションの要求を拒否する

管理者として、以前に承認されたアプリケーションの要求を拒否できるようになりました。 一度拒否したアプリケーションを後からインストールするには、ユーザーが要求を再送信する必要があります。 拒否はアプリケーションをアンインストールするのではなく、そのユーザーからそのアプリケーションの新たな要求に対して再承認を強制します。 以前は、アプリケーション要求の拒否は、承認されていないアプリケーションの要求に対してのみ可能でした。

#### <a name="try-it-out"></a>試してみましょう
承認されたアプリケーション要求を拒否するには:

1.  Configuration Manager コンソールで、承認を必要とする[アプリケーションを作成して展開します](https://docs.microsoft.com/en-us/sccm/apps/deploy-use/create-applications)。
2.  クライアント コンピューターで、ソフトウェア センターを開き、アプリケーションの要求を送信します。
3.  Configuration Manager コンソールで、アプリケーションの要求を承認します。
4.  承認されたアプリケーションの要求を拒否する: Configuration Manager コンソールで [**ソフトウェア ライブラリ**] > [**概要**] > [**アプリケーション管理**] > [**承認依頼**] に移動し、拒否するアプリケーション要求を選択します。  リボンで [**拒否**] をクリックします。

## <a name="exclude-clients-from-automatic-upgrade"></a>自動アップグレードからクライアントを除外する
Technical Preview 1610 では、クライアントのコレクションを更新されたクライアントのバージョンの自動インストールから除外するために使用できる新しい設定が導入されています。  これは、ソフトウェアの更新に基づいたアップグレード、ログオン スクリプト、およびグループ ポリシーなどのその他の方法とともに、自動アップグレードに適用されます。 これは、クライアントをアップグレードする際により注意が必要なコンピューターのコレクションに使用できます。 除外されるコレクション内にあるクライアントは、更新されたクライアント ソフトウェアのインストールの要求を無視します。

### <a name="configure-exclusion-from-automatic-upgrade"></a>自動アップグレードからの除外を構成する
自動アップグレードの除外を構成するには:
1.  Configuration Manager コンソールで、**[管理] > [サイトの構成] > [サイト]** の下で [**階層設定**] を開き、[**クライアント アップグレード**] タブをクリックします。
2.  [**指定したクライアントをアップグレードから除外する**] チェック ボックスをオンにして、[**除外コレクション**] で除外するコレクションを選択します。 除外するコレクションを 1 つだけ選択できます。
3.  [**OK**] をクリックしてコンソールを閉じ、構成を保存します。 クライアントがポリシーを更新すると、除外されるコレクション内のクライアントに、クライアント ソフトウェアの更新プログラムが自動的にインストールされなくなります。

  ![自動アップグレード除外の設定](media/automatic_upgrade_exclusion.png)

> [!NOTE]
> ユーザー インターフェイスにどの方法でもクライアントがアップグレードされないことが示されますが、これらの設定を無効にするために使用できる 2 つの方法があります。 クライアント プッシュ インストールと手動クライアント インストールを使用すると、この設定を無効にできます。 詳細については、次のセクションを参照してください。


### <a name="how-to-upgrade-a-client-that-is-in-an-excluded-collection"></a>除外されるコレクション内にあるクライアントをアップグレードする方法
コレクションが除外されるように設定されている限り、そのコレクションのメンバーは、除外を無効にする 2 つの方法のいずれかでクライアント ソフトウェアを更新することしかできません。
 - **クライアント プッシュ インストール**: クライアント プッシュ インストールを使用して、除外されるコレクション内にあるクライアントをアップグレードすることができます。 これは管理者の意図と見なされるために許可され、除外からコレクション全体を削除しなくてもクライアントをアップグレードすることができます。       
 - **手動クライアント インストール**: ccmsetup で、コマンド ライン スイッチ ***/ignoreskipupgrade*** を使用すると、除外されるコレクション内のクライアントを手動でアップグレードすることができます。

  このスイッチを使用しないで除外されるコレクションのメンバーであるクライアントを手動でアップグレードしようとすると、クライアントに新しいクライアント ソフトウェアがインストールされません。 詳細については、「[Configuration Manager クライアントの手動インストール方法](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-configuration-manager-clients-manually)」をご覧ください。

クライアント インストール方法の詳細については、「[System Center Configuration Manager でクライアントを Windows コンピューターに展開する方法](/sccm/core/clients/deploy/deploy-clients-to-windows-computers)」をご覧ください。


## <a name="see-also"></a>関連項目
[System Center Configuration Manager の Technical Preview](../../core/get-started/technical-preview.md)



<!--HONumber=Nov16_HO1-->


