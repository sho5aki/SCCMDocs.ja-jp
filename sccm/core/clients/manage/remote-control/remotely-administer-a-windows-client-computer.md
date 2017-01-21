---
title: "Windows クライアント コンピューターのリモート管理 | System Center Configuration Manager"
description: "System Center Configuration Manager を使用してリモートの Windows クライアント コンピューターを管理します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c9648c4-645e-4e47-ae10-2da817b8c83b
caps.latest.revision: 5
caps.handback.revision: 0
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 02c11420d3b05ad4eaae31d9413b66459751da70
ms.openlocfilehash: 51a9b7269993bfa133382b88792ac94032824eed


---
# <a name="how-to-remotely-administer-a-windows-client-computer-by-using-system-center-configuration-manager"></a>System Center Configuration Manager を使用して Windows クライアント コンピューターをリモート管理する方法

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager で、コンピューターをリモート管理するには、次の手順に従います。  

 リモート コントロールを開始する前に、次のトピックの情報を確認してください。  

-   [System Center Configuration Manager のリモート コントロールの前提条件](../../../../core/clients/manage/remote-control/prerequisites-for-remote-control.md)  

-   [System Center Configuration Manager でのリモート コントロールの構成](../../../../core/clients/manage/remote-control/configuring-remote-control.md)  

 Configuration Manager のリモート コントロール ビューアーは次の 3 つの方法のいずれかを使って開始できます。  

-   Configuration Manager コンソールを使用する。  

-   Windows のコマンド プロンプトを使用する。  

-   **Microsoft System Center 2012** プログラム グループから、Configuration Manager コンソールを実行するコンピューターの Windows **スタート** メニューを使用する。  

### <a name="to-remotely-administer-a-client-computer-from-the-configuration-manager-console"></a>Configuration Manager コンソールからクライアント コンピューターをリモート管理するには  

1.  Configuration Manager コンソールで、[ **資産とコンプライアンス**] をクリックします。  

2.  [資産とコンプライアンス] **** ワークスペースで [デバイス] **** または [デバイス コレクション] ****をクリックします。  

3.  リモートで管理するコンピューターを選択し、[、 **ホーム** ] タブで、 **デバイス** グループで、[ **開始**, 、順にクリック **リモート制御**です。  

    > [!IMPORTANT]  
    >  場合、クライアント設定 **リモート制御のプロンプトのユーザー** にアクセス許可が設定されている **True**, 、接続では、リモート コンピューターのユーザーがリモート コントロール プロンプトに同意するまでは開始されません。 詳しくは、「[System Center Configuration Manager でのリモート コントロールの構成](../../../../core/clients/manage/remote-control/configuring-remote-control.md)」を参照してください。  

4.  [Configuration Manager リモート コントロール] ウィンドウが開いたら、クライアント コンピューターをリモート管理できます。 **** 接続を構成するには、次のオプションを使用します。  

    > [!NOTE]  
    >  接続するコンピューターに複数のモニターがある場合は、すべてのモニターの表示画面がリモート コントロール ウィンドウに表示されます。  

    -   **ファイル - 接続** – ほかのコンピューターに接続します。 このオプションはリモート コントロール セッションがアクティブな間は使用できません。  

    -   **ファイル - 切断** – アクティブなリモート コントロール セッションを切断しますが、[**Configuration Manager リモート コントロール**] ウィンドウは閉じません。  

    -   **ファイル - 終了** – アクティブなリモート コントロール セッションを切断し、[**Configuration Manager リモート コントロール**] ウィンドウを閉じます。  

        > [!NOTE]  
        >  リモート コントロール セッションを切断すると、見ているコンピューターの Windows クリップボードのコンテンツは削除されます。  

    -   **表示 - 全画面表示** – 使用できる表示スペース全体を使って、[**Configuration Manager リモート コントロール**] ウィンドウを最大化します。  

        > [!NOTE]  
        >  全画面表示モードを終了するには、Ctrl+Alt+Break を押します。  

    -   **表示 - 画面に合わせて拡大縮小** – リモート コンピューターの画面を、[**Configuration Manager リモート コントロール**] ウィンドウのサイズに合わせて拡大縮小します。  

    -   **表示 - ステータス バー** – [**Configuration Manager リモート コントロール**] ウィンドウ ステータス バーの表示を切り替えます。  

    -   **操作 - Ctrl+Alt+Del キーの送信** – Ctrl+Alt+Del キーの組み合わせをリモート コンピューターに送信します。  

    -   **操作 - クリップボードの共有** – リモート コンピューターとの間でコピーと貼り付けを可能にします。 この値を変えた場合は、その変更を有効にするには、リモート コントロールのセッションを再起動する必要があります  

        > [!NOTE]  
        >  Configuration Manager コンソールでクリップボードを共有できないようにするには、そのコンソールを実行しているコンピューターで、レジストリ キー **HKEY_CURRENT_USER\Software\Microsoft\ConfigMgr10\Remote Control\Clipboard Sharing** の値を **0**に設定します。  

    -   **操作 - リモートのキーボードとマウスのロック** – リモート キーボードとマウスをロックして、ユーザーがリモート コンピューターを操作するのを防ぎます。  

    -   **ヘルプ - バージョン情報** – リモート コントロール ビューアーの現在のバージョン情報を表示します。  

5.  リモート コンピューターのユーザーは、Windows 通知領域の Configuration Manager **[リモート コントロール]** アイコンまたはリモート コントロール セッション バーのアイコンをクリックすると、リモート コントロールのセッションについて、より多くの情報を得ることができます。  

6.  リモート コントロール セッションを続ける必要がなくなったら、前述の方法の 1 つを使ってリモート コントロール セッションを終了します。  

### <a name="to-start-the-remote-control-viewer-from-the-windows-command-line"></a>Windows のコマンド ラインから、リモート コントロール ビューアーを起動するには  

-   Windows のコマンド プロンプトで、「*<Configuration Manager インストール フォルダー>\>***\AdminConsole\Bin\x64\CmRcViewer.exe**」と入力します。  

    > [!NOTE]  
    >  CmRcViewer.exe は次のコマンドライン オプションをサポートします。  
    >   
    >  -   *<アドレス\>* - NetBIOS 名、完全修飾ドメイン名 (FQDN)、または接続先クライアント コンピューターの IP アドレスを指定します。  
    > -   *<サイト サーバー名>\>* - リモート コントロール セッションに関連するステータス メッセージの送信先の System Center 2012 Configuration Manager サイト サーバー名を指定します。  
    > -   **/?** - リモート コントロール ビューアーのコマンド ライン オプションを表示します。  
    >   
    >  **例: CmRcViewer.exe** *<アドレス\>* *<\\\サイト サーバー名>*  



<!--HONumber=Nov16_HO1-->


