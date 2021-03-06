---
title: "配布ポイントの管理 | Microsoft Docs"
description: "配布ポイントを利用し、デバイスやユーザーに展開するコンテンツ (ファイルとソフトウェア) をホストします。 インストール方法と構成方法は次のようになります。"
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aebafaf9-b3d5-4a0f-9ee5-685758c037a1
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 8728d9f2ae63282a8f58b20105e488fb1a5ef55b
ms.openlocfilehash: 4c94e4de5bbfe621492e8682c9424a48eb38196d
ms.contentlocale: ja-jp
ms.lasthandoff: 05/17/2017

---
# <a name="install-and-configure-distribution-points-for-system-center-configuration-manager"></a>System Center Configuration Manager の配布ポイントのインストールと構成

*適用対象: System Center Configuration Manager (Current Branch)*
 
System Center Configuration Manager 配布ポイントをインストールし、デバイスやユーザーに展開するコンテンツ (ファイルとソフトウェア) をホストします。 配布ポイント グループを作成することもできます。配布ポイントの管理と配布ポイントへのコンテンツの配布が簡単になります。  

 "*新しい配布ポイントをインストールする*" とき (インストール ウィザードを利用して)、あるいは "*既存の配布ポイントのプロパティを管理する*" とき (配布ポイントのプロパティを編集して)、ほとんどの配布ポイントの設定を構成できます。 インストールまたは編集のいずれか一方を行うときに使用可能な設定はいくつか用意されていますが、両方を行う設定はありません。  

-   配布ポイントをインストールするときにのみ使用可能な設定:  

    -   **Configuration Manager が配布ポイントのコンピューターに IIS をインストールすることを許可する**

    -   **配布ポイントのドライブ容量の設定を構成する**  

-   配布ポイントのプロパティを編集するときにのみ使用可能な設定:  

    -   **配布ポイント グループの関係を管理する**  

    -   **配布ポイントに展開されているコンテンツを表示する**  

    -   **配布ポイントへのデータ転送の転送率の制限を構成する**  

    -   **配布ポイントへのデータ転送のスケジュールを構成する**  

##  <a name="bkmk_install"></a> 配布ポイントをインストールする  
 クライアント コンピューターでコンテンツを使用できるようにする前に、サイト システム サーバーを配布ポイントとして指定する必要があります。 配布ポイント サイトの役割を新しいサイト システム サーバーに追加するか、サイトの役割を既存のサイト システム サーバーに追加できます。  

 新しい配布ポイントをインストールするとき、インストール ウィザードを利用します。利用可能な設定を段階的に実行できます。 開始する前に、次の点を考慮してください。  

-   配布ポイントを作成して構成するには、次のセキュリティ権限が必要です。  

    -   **配布ポイント** オブジェクトの **読み取り**  

    -   **配布ポイント** オブジェクトの **配布ポイントにコピー**  

    -   **サイト** オブジェクトの **変更**  

    -   **サイト** オブジェクトの **オペレーティング システム展開の証明書の管理**  

-   配布ポイントをホストするサーバーにインターネット インフォメーション サービス (IIS) をインストールする必要があります。 サイト システムの役割をインストールするとき、Configuration Manager によって IIS をインストールし、構成することができます。  

配布ポイントをインストールまたは変更するには、次の基本的な手順を使用します。 使用可能な構成オプションについて詳しくは、このトピックの「[配布ポイントの構成](#bkmk_configs)」セクションをご覧ください。  

#### <a name="to-install-a-distribution-point"></a>配布ポイントをインストールするには  

1.  Configuration Manager コンソールで、**[管理]**、**[サイトの構成]**、**[サーバーとサイト システムの役割]** の順に選択します。  

2.  配布ポイント サイト システムの役割を新規または既存のサイト システム サーバーに追加します。  

    -   **新しいサイト システム サーバー**: **[ホーム]** タブの **[作成]** グループで、**[サイト システム サーバーの作成]** を選択します。 サイト システム サーバーの作成ウィザードが開きます。  

    -   **既存のサイト システム サーバー**:配布ポイントのサイト システムの役割をインストールするサーバーを選択します。 サーバーを選択すると、サーバーに既にインストールされているサイト システムの役割の一覧が、結果ウィンドウに表示されます。  

         **[ホーム]** タブの **[サーバー]** グループで、**[サイト システムの役割の追加]** を選択します。 サイト システムの役割の追加ウィザードが開きます。  

3.  [ **全般** ] ページで、サイト システム サーバーの全般設定を指定します。 配布ポイントを既存のサイト システム サーバーに追加する場合は、以前に構成した値を確認します。  

4.  **[システムの役割の選択]** ページで、利用可能な役割の一覧から **[配布ポイント]** を選択してから、**[次へ]** を選択します。  

5.  ウィザードの後続のページについては、「[配布ポイントの構成](#bkmk_configs)」セクションの情報をご覧ください。  

     たとえば、配布ポイントをプル配布ポイントとしてインストールする場合は、**[この配布ポイントで他の配布ポイントからのコンテンツのプルを有効にする]** を選択し、プル配布ポイントに必要な追加の構成を作成します。  

6.  ウィザードを完了した後、配布ポイント サイトの役割がサイト システム サーバーに追加されます。  

#### <a name="to-change-a-distribution-point"></a>配布ポイントを変更するには  

1.  Configuration Manager コンソールで、**[管理]**、**[配布ポイント]** の順に選択して、構成する配布ポイントを選択します。  

2.  **[ホーム]** タブの **[プロパティ]** グループで、**[プロパティ]** を選択します。  

3.  「[配布ポイントの構成](#bkmk_configs)」セクションの情報を参考に、配布ポイントのプロパティを編集します。  

4.  必要な変更を行った後は、設定を保存して配布ポイントのプロパティを閉じます。  

##  <a name="bkmk_manage"></a> 配布ポイント グループの管理  
 配布ポイントを論理的な "配布ポイント グループ" に分けることができます。 これらのグループを使用して、複数のサイトに配置されている配布ポイントのコンテンツを 1 か所で管理および監視することができます。 次のことに注意してください。

-   階層内の任意のサイトから 1 つまたは複数の配布ポイントを配布ポイント グループに追加できます。  

-   1 つの配布ポイントを、複数の配布ポイント グループに追加することもできます。  

-   配布ポイント グループにコンテンツを配布すると、Configuration Manager がその配布ポイント グループに属するすべての配布ポイントにコンテンツを配布します。  

-   最初にコンテンツを配布した後に、配布ポイント グループに配布ポイントを追加すると、Configuration Manager が新しい配布ポイント メンバーにコンテンツを自動的に配布します。  

-   コレクションを配布ポイント グループに関連付けることができます。 コンテンツをそのコレクションに配布すると、Configuration Manager がコレクションに関連付けられている配布ポイント グループを特定します。 その後、コンテンツは、それらの配布ポイント グループのメンバーであるすべての配布ポイントに配布されます。  

    > [!NOTE]  
    >  コンテンツをコレクションに配布した後でコレクションを新しい配布ポイント グループに関連付けた場合は、コンテンツが新しい配布ポイント グループに配布される前に、コンテンツをコレクションに再配布する必要があります。  

#### <a name="to-create-and-configure-a-new-distribution-point-group"></a>新しい配布ポイント グループを作成して構成するには  

1.  Configuration Manager コンソールで、**[管理]**、**[配布ポイント グループ]** の順に選択します。  

2.  **[ホーム]** タブの **[作成]** グループで **[グループの作成]** を選択します。  

3.  配布ポイント グループの名前と説明を入力します。  

4.  **[コレクション]** タブで **[追加]** を選択し、配布ポイント グループに関連付けるコレクションを選択してから、**[OK]** を選択します。  

5.  **[メンバー]** タブで **[追加]** を選択し、配布ポイント グループのメンバーとして追加する配布ポイントを選択してから、**[OK]** を選択します。  

6.  **[OK]** を選択して配布ポイント グループを作成します。  

#### <a name="to-add-distribution-points-and-associate-collections-with-an-existing-distribution-point-group"></a>配布ポイントを追加して既存の配布ポイント グループにコレクションを関連付けるには  

1.  Configuration Manager コンソールで、**[管理]**、**[配布ポイント グループ]** の順に選択します。  

2.  **[ホーム]** タブの **[プロパティ]** グループで、**[プロパティ]** を選択します。  

3.  **[コレクション]** タブで **[追加]** を選択し、配布ポイント グループに関連付けるコレクションを選択してから、**[OK]** を選択します。  

4.  **[メンバー]** タブで **[追加]** を選択し、配布ポイント グループのメンバーとして追加する配布ポイントを選択してから、**[OK]** を選択します。  

5.  **[OK]** をクリックして配布ポイント グループに加えた変更を保存します。  

#### <a name="to-add-selected-distribution-points-to-a-new-distribution-point-group"></a>選択した配布ポイント グループを新しい配布ポイント グループに追加するには  

1.  Configuration Manager コンソールで、**[管理]**、**[配布ポイント]** の順に選択して、新しい配布ポイント グループに追加する配布ポイントを選択します。  

2.  **[ホーム]** タブの **[配布ポイント]** グループで、**[選択された項目の追加]** を展開し、**[選択した項目を新しい配布ポイント グループに追加]** を選択します。  

3.  配布ポイント グループの名前と説明を入力します。  

4.  **[コレクション]** タブで **[追加]** を選択し、配布ポイント グループに関連付けるコレクションを選択してから、**[OK]** を選択します。  

5.  **[メンバー]** タブで、配布ポイント グループのメンバーとして一覧に表示された配布ポイントを Configuration Manager で追加するかどうかを確認します。 **[追加]** を選択して配布ポイントを追加してから、**[OK]** を選択します。  

6.  **[OK]** を選択して配布ポイント グループを作成します。  

#### <a name="to-add-selected-distribution-points-to-existing-distribution-point-groups"></a>選択した配布ポイント グループを既存の配布ポイント グループに追加するには  

1.  Configuration Manager コンソールで、**[管理]**、**[配布ポイント]** の順に選択して、新しい配布ポイント グループに追加する配布ポイントを選択します。  

2.  **[ホーム]** タブの **[配布ポイント]** グループで、**[選択された項目の追加]** を展開し、**[選択した項目を既存の配布ポイント グループに追加]** を選択します。  

3.  **[利用可能な配布ポイント グループ]** で、選択した配布ポイントがメンバーとして追加される配布ポイント グループを選択してから、**[OK]** を選択します。  

##  <a name="bkmk_configs"></a> 配布ポイントの構成  
 それぞれの配布ポイントは、さまざまな構成をサポートします。 ただし、すべての配布ポイントの種類ですべての構成がサポートされるわけではありません。 たとえば、クラウドベースの配布ポイントでは、PXE やマルチキャストが有効なコンテンツの展開はサポートされません。 具体的な制限事項に関する情報については、次のトピックを参照してください。  

-   [System Center Configuration Manager でのクラウド ベースの配布ポイントの使用](../../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md)  

-   [System Center Configuration Manager でのプル配布ポイントの使用](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point)  

次のセクションでは、新しい配布ポイントをインストールするとき、または既存の配布ポイントのプロパティを編集するときに選べる構成を示します。  

### <a name="general"></a>全般  
 一般的な配布ポイント設定の構成:  

-   **Configuration Manager で必要な場合は IIS をインストールして構成する**: この設定を選択すると、IIS がまだサーバーにインストールされていない場合に、Configuration Manager で IIS をインストールおよび構成することができます。 IIS はすべての配布ポイントにインストールされなければなりません。 サーバーに IIS がインストールされていない状況でこの設定を選択しない場合、配布ポイントを正常にインストールするにはまず IIS をインストールする必要があります。  

    > [!NOTE]  
    >  このオプションは、新しい配布ポイントをインストールするときにのみ使用できます。  

- **この配布ポイントの BranchCache を有効にして構成する**: この設定を選択すると、Configuration Manager で、配布ポイント サーバーに対して Windows BranchCache を構成することができます。 System Center Configuration Manager で Windows BranchCache を使用する方法については、「*System Center Configuration Manager での Windows 機能とネットワークのサポート*」の「[BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#a-namebkmkbranchcachea-branchcache)」を参照してください。

-   **クライアント デバイスがどのように配布ポイントと通信するかを構成する**: HTTP 接続と HTTPS 接続には、それぞれ長所と欠点があります。 詳しくは、「[System Center Configuration Manager でのコンテンツ管理の基本的な概念](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md)」の「コンテンツ管理に関するセキュリティのベスト プラクティス」をご覧ください。  

-   **クライアントに匿名接続を許可する**: 配布ポイントのコンテンツ ライブラリに、Configuration Manager クライアントから匿名で接続できるようにするかどうかを指定します。  

    > [!IMPORTANT]  
    >  この設定を使用しない場合、Windows インストーラー アプリケーションの修復がクライアントで失敗する可能性があります。  
    >   
    >  Configuration Manager クライアントに Windows インストーラー アプリケーションを展開すると、Configuration Manager ではファイルがクライアントのローカル キャッシュにダウンロードされます。 最終的にはインストール完了後にそのファイルが削除されます。
    >  
    >  Configuration Manager クライアントは、インストールされた Windows インストーラー アプリケーションの Windows インストーラー ソース リストを、関連付けられた配布ポイントのコンテンツ ライブラリのコンテンツ パスで更新します。 その後、Configuration Manager クライアントで [プログラムの追加と削除] を使って修復インストールを開始すると、MSIExec は匿名ユーザーとしてコンテンツ パスにアクセスしようとします。  
    >   
    >  ただし、Microsoft サポート技術情報の記事 [2619572](http://go.microsoft.com/fwlink/?LinkId=279699) で説明されている更新プログラムをインストールした後でレジストリ キーを変更して、この動作を変更することができます。  
    >   
    >  更新プログラムをクライアントにインストール後、**[クライアントに匿名接続を許可する]** 設定を選択しない場合、MSIExec はログオンしたユーザー アカウントを使用してコンテンツ パスにアクセスします。  

-   **配布ポイントの自己署名入り証明書を作成するか、公開キー基盤 (PKI) クライアント証明書をインポートする**: 証明書には次の目的があります。  

    -   配布ポイントがステータス メッセージを管理ポイントに送信する前に、管理ポイントから認証を受けるようにします。  

    -   **[PXE 設定]** ページで **[クライアントの PXE サポートを有効にする]** チェック ボックスをオンにすると、PXE ブートを実行するコンピューターに証明書が送信され、オペレーティング システムを展開するときに、そのコンピューターから管理ポイントに接続できるようになります。  

    サイトのすべての管理ポイントが HTTP 用に構成されている場合は、自己署名入り証明書を作成します。 管理ポイントが HTTPS 用に構成されている場合は、PKI クライアント証明書をインポートします。  

    証明書をインポートするには、次の Configuration Manager の要件を満たす PKI 証明書を含む公開キー暗号化標準 (PKCS #12) ファイルを見つけます。  

    -   使用目的にクライアント認証が含まれている。  

    -   秘密キーがエクスポート可能である。  

    > [!TIP]  
    >  証明書のサブジェクトやサブジェクトの別名 (SAN) には、特定の要件はありません。複数の配布ポイントで同じ証明書を使用することができます。  

     証明書の要件の詳細については、「[System Center Configuration Manager での PKI 証明書の要件](../../../../core/plan-design/network/pki-certificate-requirements.md)」を参照してください。  

     この証明書の展開の例については、「[System Center Configuration Manager PKI 証明書の展開手順の例: Windows Server 2008 証明機関](/sccm/core/plan-design/network/example-deployment-of-pki-certificates)」の「配布ポイント用のクライアント証明書の展開」セクションをご覧ください。  

-   **事前設定されたコンテンツ用にこの配布ポイントを有効にする**: この設定を選択すると、配布ポイントでコンテンツを事前設定できるようになります。 この設定を選択すると、コンテンツを配布するときの動作を構成できます。 次のいずれかを常に実行するように選択できます。

 - 配布ポイントのコンテンツを事前設定する。
 - パッケージの初期コンテンツを事前設定するが、コンテンツの更新があるときは通常のコンテンツ配布プロセスを使用する。
 - パッケージのコンテンツに対して、通常のコンテンツ配布プロセスを使用する。  

### <a name="drive-settings"></a>ドライブ設定  

> [!NOTE]  
>  これらのオプションは、新しい配布ポイントをインストールするときにのみ使用できます。  

配布ポイントのドライブ設定を指定します。 最大でコンテンツ ライブラリ用に 2 つのディスク ドライブ、パッケージ共有用に 2 つのディスク ドライブを構成できます。 Configuration Manager は、最初の 2 つが構成されたドライブの予約領域に達すると、追加のドライブを使用できます。 [ **ドライブ設定** ] ページで、ディスク ドライブの優先度と各ディスク ドライブに残しておく空き容量を構成します。  

-   **ドライブの予約領域 (MB)**: ドライブにどの程度空き領域を残しておくかを指定します。空き領域がこの値に達すると、Configuration Manager が別のドライブを選択して、そのドライブへのコピーを続けます。 コンテンツ ファイルは、複数のドライブにまたがって保存されます。  

-   **コンテンツの場所**:コンテンツ ライブラリとパッケージの共有のコンテンツの場所を指定します。 Configuration Manager は、ドライブの空き領域が **[ドライブの予約領域 (MB)]** で指定した値になるまで、コンテンツの第 1 の場所にコンテンツをコピーします。 既定では、コンテンツの場所は [ **自動**] に設定されています。 第 1 の場所は、インストール時に空き領域の最も大きいディスク ドライブに、第 2 の場所は、2 番目に空き領域の大きいディスク ドライブに割り当てられます。 第 1 と第 2 のドライブが予約領域に達すると、Configuration Manager は、使用可能なドライブのうち、空き領域が最も大きなドライブを選択してコピーを続けます。  

> [!NOTE]  
>  Configuration Manager が特定のドライブにインストールされないようにするには、配布ポイントをインストールする前に、**no_sms_on_drive.sms** という名前の空のファイルを作成して、ドライブのルート フォルダーにコピーしておきます。  

### <a name="pull-distribution-point"></a>プル配布ポイント  
**[この配布ポイントで他の配布ポイントからのコンテンツのプルを有効にする]** を選択すると、配布ポイントに配布されたコンテンツをコンピューターが取得する動作を変更できます。 この配布ポイントがプル配布ポイントになります。  

構成するそれぞれのプル配布ポイントに対して、プル配布ポイントがコンテンツを取得するソース配布ポイントを 1 つまたは複数指定する必要があります。  

-   **[追加]** をクリックし、1 つまたは複数の使用できる配布ポイントをソース配布ポイントとして選択します。  

-   **[削除]** をクリックして、ソース配布ポイントとして選択した配布ポイントを削除します。  

-   矢印ボタンを使用して、プル配布ポイントがコンテンツへの転送を試行するときに、プル配布ポイントがソース配布ポイントに接続する順序を調整します。 最初に接続するのは、最も小さい値の配布ポイントです。  

### <a name="pxe"></a>PXE  
配布ポイントで PXE を有効にするかどうかを指定します。 PXE を有効にすると、必要に応じて、Configuration Manager がサーバー上に Windows 展開サービスをインストールします。 Windows 展開サービスは、PXE ブートを実行してオペレーティング システムをインストールするサービスです。 配布ポイントを作成するウィザードを完了した後、Configuration Manager は PXE ブート機能を使用する Windows 展開サービスのプロバイダーをインストールします。  

**[クライアントの PXE サポートを有効にする]** をオンにした場合は、次の設定を構成します。  

-   **この配布ポイントが受信 PXE 要求に応答できるようにする**: PXE サービス要求に対応するように Windows 展開サービスを有効にするかどうかを指定します。 このボックスを使用して、配布ポイントから PXE 機能を削除せずにサービスを有効/無効にします。  

-   **不明なコンピューターのサポートを有効にする**: Configuration Manager で管理されていないコンピューターのサポートを有効にするかどうかを指定します。  

-   **PXE コンピューターで PXE を使用する場合にパスワードを要求する**:PXE 展開のセキュリティを強化するには、強力なパスワードを指定します。  

-   **ユーザーとデバイスのアフィニティ**:配布ポイントがどのようにユーザーと PXE 展開の展開先コンピューターを関連付けるのかを指定します。 次のいずれかのオプションを選択します。  

    -   **ユーザーとデバイスのアフィニティを自動的に承認する**: この設定を選択すると、承認を待機せずに自動的にユーザーと展開先コンピューターを関連付けます。  

    -   **ユーザーとデバイスのアフィニティを管理者の承認待ちにする**: この設定を選択すると、管理者ユーザーからの承認を待って、ユーザーと展開先コンピューターを関連付けます。  

    -   **ユーザーとデバイスのアフィニティを許可しない**: この設定を選択すると、ユーザーと展開先コンピューターを関連付けません。  

     ユーザーとデバイスのアフィニティの詳細については、「[System Center Configuration Manager でのユーザーとデバイスのアフィニティへのユーザーとデバイスの関連付け](../../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)」を参照してください。  

-   **ネットワーク インターフェイス**:配布ポイントがすべてのネットワーク インターフェイスまたは特定のネットワーク インターフェイスからの PXE 要求に応答することを指定します。 配布ポイントが特定のネットワーク インターフェイスに応答する場合は、各ネットワーク インターフェイスの MAC アドレスを指定する必要があります。  

-   **PXE サーバーの応答待機時間の指定 (秒)**: PXE 対応配布ポイントが複数ある場合に、コンピューターの要求に応答するまでにこの配布ポイントが待機する秒数を指定します。 既定では、Configuration Manager の PXE サービス ポイントは、最初にネットワーク PXE 要求に応答します。  

> [!NOTE]  
>  PXE プロトコルを使用して、Configuration Manager クライアント コンピューターへのオペレーティング システムの展開を開始できます。 Configuration Manager は、PXE 対応配布ポイント サイトの役割を使用して、オペレーティング システムの展開プロセスを開始します。 PXE 対応配布ポイントは、次のように構成する必要があります。
>
> 1. Configuration Manager クライアントからネットワークに対する PXE ブート要求に応答する。
> 2. Configuration Manager インフラストラクチャと対話して実行する適切な展開アクションを決定する。  

### <a name="multicast"></a>マルチキャスト  
配布ポイントでマルチキャストを有効にするかどうかを指定します。 マルチキャストを有効にすると、必要に応じて、Configuration Manager がサーバー上に Windows 展開サービスをインストールします。  

**[複数のクライアントに同時にデータを送信するマルチキャストを有効にする]** をオンにした場合は、次の設定を構成します。  

-   **マルチキャスト接続アカウント**: マルチキャストの Configuration Manager データベース接続を構成するときに使用するアカウントを指定します。  

-   **マルチキャスト アドレス設定**: 展開先のコンピューターにデータを送信するための IP アドレスを指定します。 既定では、マルチキャスト アドレスの配布が有効になっている DHCP サーバーから IP アドレスを取得します。 ネットワーク環境によって、239.0.0.0 ～ 239.255.255.255 の範囲の IP アドレスを指定できます。  

    > [!IMPORTANT]  
    >  オペレーティング システム イメージを要求する展開先コンピューターは、構成する IP アドレスにアクセスできる必要があります。 ルーターとファイアウォールが、展開先コンピューターとサイト サーバー間のマルチキャスト トラフィックを許可していることを確認してください。  

-   **マルチキャストの UDP ポートの範囲**: 展開先コンピューターにデータを送信するために使用されるユーザー データグラム プロトコル (UDP) ポートの範囲を指定します。  

    > [!IMPORTANT]  
    >  オペレーティング システム イメージを要求する展開先コンピューターは、UDP ポートにアクセスできる必要があります。 ルーターとファイアウォールが、展開先コンピューターとサイト サーバー間のマルチキャスト トラフィックを許可していることを確認してください。  

-   **クライアントの転送速度**:展開先コンピューターへのデータのダウンロードに使用される転送速度を選択します。  

-   **最大クライアント数**: この配布ポイントからオペレーティング システムをダウンロードできる展開先のコンピューターの最大数を指定します。  

-   **スケジュールされたマルチキャストを有効にする**: Configuration Manager がどのように展開先コンピューターへのオペレーティング システムの展開開始日時を制御するかを指定します。 次のオプションを構成します。  

    -   **セッション開始の待ち時間 (分)**: 最初の展開要求に応答する前に Configuration Manager が待機する時間 (分) を指定します。  

    -   **最小セッション サイズ (クライアント数)**: Configuration Manager がオペレーティング システムの展開を開始する前に受信しなければならない要求数を指定します。  

> [!NOTE]  
>  マルチキャスト展開では、別々の接続で各クライアントにデータのコピーを送信する代わりに、複数の Configuration Manager クライアントに同時にデータを送信することで、ネットワークの帯域幅を節約します。 マルチキャストを使用してオペレーティング システムを展開する方法の詳細については、「[System Center Configuration Manager でマルチキャストを使用してネットワーク経由で Windows を展開する](../../../../osd/deploy-use/use-multicast-to-deploy-windows-over-the-network.md)」を参照してください。  

### <a name="group-relationships"></a>グループの関係  

> [!NOTE]  
>  これらのオプションは、以前にインストールされた配布ポイントのプロパティを編集する場合にのみ使用できます。  

配布ポイントがメンバーである配布ポイントのグループを管理します。  

この配布ポイントを既存の配布ポイント グループのメンバーとして追加するには、**[追加]** をクリックします。 **[配布ポイント グループに追加]** ダイアログ ボックスの一覧にある既存の配布ポイント グループを選択してから、**[OK]** を選択します。  

この配布ポイントを配布ポイント グループから削除するには、一覧にある配布ポイント グループを選択してから、 **[削除]** を選択します。  

### <a name="content"></a>Content  

> [!NOTE]  
>  これらのオプションは、以前にインストールされた配布ポイントのプロパティを編集する場合にのみ使用できます。  

配布ポイントに配布されているコンテンツを管理します。 **[展開パッケージ]** セクションに、この配布ポイントに配布されたパッケージの一覧が表示されます。 その一覧からパッケージを選択し、次の操作を実行します。  

-   **検証** :パッケージ内のコンテンツ ファイルの整合性を検証するプロセスを開始します。 コンテンツの検証プロセスの結果を見るには、**[監視]** ワークスペースをクリックして **[配布ステータス]** を展開し、**[コンテンツの状態]** ノードを選択します。  

-   **再配布** :パッケージ内のコンテンツ ファイルをすべて配布ポイントにコピーし、既存のファイルを上書きします。 この操作は通常、パッケージ内のコンテンツ ファイルの修復に使用します。  

-   **削除** : Removes the content files from the distribution point for the package.  

### <a name="content-validation"></a>コンテンツの検証  
配布ポイントにあるコンテンツ ファイルの整合性を検証するスケジュールを設定するかどうかを指定します。 スケジュールに従ったコンテンツの検証を有効にすると、指定した時刻に Configuration Manager が配布ポイントのコンテンツの検証プロセスを開始し、すべてのコンテンツが検証されます。 また、コンテンツの検証の優先度を構成することもできます。 既定では、優先度は [ **最低** ] に設定されます。  

コンテンツの検証プロセスの結果を見るには、**[監視]** ワークスペースをクリックして **[配布ステータス]** を展開し、**[コンテンツの状態]** ノードを選択します。 パッケージの種類 (アプリケーション、ソフトウェアの更新パッケージ、ブート イメージなど) ごとにコンテンツが表示されます。  

> [!WARNING]  
>  コンテンツの検証スケジュールはコンピューターのローカル時刻を使用して指定しますが、Configuration Manager コンソールに表示されるスケジュールでは UTC が使用されます。  

### <a name="boundary-group"></a>境界グループ  
この配布ポイントを割り当てる境界グループを管理します。 境界グループを配布ポイントに関連付けることができます。 コンテンツを展開するときに、クライアントがコンテンツのソースの場所として配布ポイントを使用するには、クライアントは、その配布ポイントに関連付けられた境界グループ内になければなりません。

補足:

- 1610 より前では、**[クライアントがこのサイト システムを代替のコンテンツ ソースの場所として使用することを許可する]** をオンにすると、他に利用できる代替ポイントがない場合に、この境界グループ外のクライアントのフォールバックが許可され、配布ポイントをコンテンツ ソースの場所として使用できるようになります。 境界グループについて詳しくは、「[Boundary groups for versions 1511,1602, and 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606)」(バージョン 1511、1602、1606 の境界グループ) をご覧ください。 優先配布ポイントについて詳しくは、「[System Center Configuration Manager でのコンテンツ管理の基本的な概念](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md)」をご覧ください。

- バージョン 1610 以降では、コンテンツを検索するために、いつ、どの境界グループまでフォールバックできるかを定義する、境界グループの "*関係*" を構成します。 詳細については、「[境界グループ](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups)」を参照してください。


### <a name="schedule"></a>スケジュール  

> [!NOTE]  
>  これらのオプションは、以前にインストールされた配布ポイントのプロパティを編集する場合にのみ使用できます。  

> [!TIP]  
>  このタブは、サイト サーバー コンピューターのリモートにある配布ポイントのプロパティを編集するときにのみ、使用できます。  

 Configuration Manager で配布ポイントにいつデータを転送できるかを制限するスケジュールを構成するかどうかを指定します。  

> [!IMPORTANT]  
>  スケジュールは、配布ポイントではなく、送信側サイトのタイム ゾーンに基づきます。  

データを制限するには、期間を選択し、次の **[可用性]** の設定からいずれかを選択します。  

-   **すべての優先順位に対して開く**: Configuration Manager によって配布ポイントにデータが制限なしで送信されることを指定します。  

-   **中および高優先順位を許可する**: Configuration Manager によって中および高優先順位のデータのみが配布ポイントに送信されることを指定します。  

-   **高優先順位のみ許可する**: Configuration Manager によって高優先順位のデータのみが配布ポイントに送信されることを指定します。  

-   **不可**: Configuration Manager によって配布ポイントにデータを一切送信しないことを指定します。  

データは優先順位で制限するか、選択した期間の接続を切断して制限することができます。  

### <a name="rate-limits"></a>転送率の制限  

> [!NOTE]  
>  これらのオプションは、以前にインストールされた配布ポイントのプロパティを編集する場合にのみ使用できます。  

> [!TIP]  
>  このタブは、サイト サーバー コンピューターのリモートにある配布ポイントのプロパティを編集するときにのみ、使用できます。  

Configuration Manager がコンテンツを配布ポイントに転送するときに使用するネットワーク帯域幅を制御するために、転送率を構成するかどうかを指定します。 次のオプションから選択できます。  

-   **この宛先に送信する場合は制限しない**: このオプションは、Configuration Manager によってコンテンツが配布ポイントに転送率の制限なしで送信されることを指定します。  

-   **パルス モード**: このオプションは、配布ポイントに送信するデータ ブロックのサイズを指定します。 また、データ ブロックを送信する間隔を指定することもできます。 このオプションは、帯域幅が非常に小さなネットワーク接続でデータを配布ポイントに送信しなければならない場合に使用してください。 たとえば、リンク速度や特定の時間帯の使用率に関係なく、5 秒に 1 KB のデータを送信するように構成します。  

-   **指定された時間帯の最大転送率を制限する** :この設定を指定して、構成した時間の割合 (%) のみを使用してサイトが配布ポイントにデータを送信するようにします。 このオプションを使用すると、Configuration Manager ではネットワークの使用可能な帯域幅は考慮されず、代わりに、データを送信できる時間が分割されます。 その分割された短い時間にデータが送信され、次にデータが送信されない時間が続きます。 たとえば、最大転送率を **50%**に設定すると、Configuration Manager ではある一定の時間だけデータが転送され、その後、同じ長さの時間だけ転送が停止されます。 データの実際の量やデータ ブロックのサイズは考慮されません。 代わりに、どれだけの時間データを送信するかが管理されます。  

