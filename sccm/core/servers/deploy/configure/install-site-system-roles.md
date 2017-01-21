---
title: "サイト システムの役割のインストール | System Center Configuration Manager"
description: "ウィザードを使用して、サイト内の既存の、または新しいサイト システム サーバーにサイト システムの役割を追加します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61f5c774-7667-44ae-b8e4-a4951318b183
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 780ef516ddc641d53e1d2d4a5f559795cfd22cbb

---
# <a name="install-site-system-roles-for-system-center-configuration-manager"></a>System Center Configuration Manager のサイト システム役割のインストール

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager コンソールには、サイト システムの役割をインストールできるウィザードが 2 つあります。  

-   サイト システムの役割の追加ウィザード:****このウィザードを使用して、サイト内の既存のサイト システム サーバーにサイト システムの役割を追加します。  

-   サイト システム サーバーの作成ウィザード:****このウィザードを使用して、新しいサーバーをサイト システム サーバーとして指定し、そのサーバーにサイト システムの役割をインストールします。 このウィザードはサイト システムの役割の追加ウィザードと同様に動作しますが、唯一異なっているのは、最初のページで使用するサイトの名前とインストール先のサイトを指定する点です。 ****  

リモート コンピューター (SMS プロバイダーのインスタンスを含む) にサイト システムの役割をインストールすると、リモート コンピューターのコンピューター アカウントがサイト サーバーのローカル グループに追加されます。 ドメイン コントローラーにサイトをインストールすると、サイト サーバーのグループはローカル グループではなくドメイン グループになり、サイト システムの役割のコンピューターが再起動されるか、リモート コンピューターのアカウント [System Center Configuration Manager で使用されるアカウント](../../../../core/plan-design/hierarchy/accounts.md) の Kerberos チケットが更新されるまで、リモート サイト システムの役割は機能しません。  

サイト システムの役割をインストールする前に、Configuration Manager は対象のコンピューターを調べて、選択されたサイト システムの役割の前提条件を満たしていることを確認します。 サイト システムの役割をインストールする場合:  

-   既定では、Configuration Manager がサイト システムの役割をインストールする際、ディスク空き領域が最も多く残っていて、最初に利用可能な NTFS 形式のディスク ドライブにインストール ファイルがインストールされます。 Configuration Manager が特定のドライブにインストールされないようにするには、サイト システム サーバーをインストールする前に、**no_sms_on_drive.sms** と言う名前の空のファイルを作成して、ドライブのルート フォルダーにコピーしておきます。  

-   Configuration Manager では、**サイト システムのインストール アカウント**を使用してサイト システムの役割をインストールします。 適切なウィザードを実行して、新しいサイト システム サーバーを作成したり、既存のサイト システム サーバーにサイト システムの役割を追加したりするときに、このアカウントを指定します。 既定では、このアカウントはサイト サーバー コンピューターのローカル システム アカウントですが、ドメイン ユーザー アカウントをサイト システムのインストール アカウントとして使用するように指定できます。 詳細については、「[System Center Configuration Manager で使用されるアカウント](../../../../core/plan-design/hierarchy/accounts.md)」トピックの「サイト システムのインストール アカウント」を参照してください。  

##  <a name="a-namebkmkinstalla-to-install-site-system-roles-on-an-existing-site-system-server"></a><a name="bkmk_Install"></a> 既存のサイト システム サーバーにサイト システムの役割をインストールするには  

1.  Configuration Manager コンソールで、[ **管理**] をクリックします。  

2.  [ **管理** ] ワークスペースで [ **サイトの構成**] を展開し、[ **サーバーとサイト システムの役割**] をクリックしてから、新しいサイト システムの役割に使用するサーバーを選択します。  

3.  [ **ホーム** ] タブの [ **サーバー** ] グループで、[ **サイト システムの役割の追加**] をクリックします。  

4.  [ **全般** ] ページで設定を確認し、[ **次へ**] をクリックします。  

    > [!TIP]  
    >  インターネットからサイト システムの役割にアクセスするには、インターネット FQDN を指定してください。  

5.  このサイト システム サーバー上で実行されるサイト システムの役割が、プロキシ サーバーを使用してインターネット上の場所に接続しなければならない場合は、[ **プロキシ** ] ページでプロキシ サーバーの設定を指定してから [ **次へ**] をクリックします。  

6.  [ **システムの役割の選択** ] ページで、追加するサイト システムの役割を選択し、[ **次へ**] をクリックします。  

7.  ウィザードを完了します。  

> [!TIP]  
>  Windows PowerShell コマンドレット New-CMSiteSystemServer で、この手順と同じ機能が実行されます。 詳細については、System Center 2012 Configuration Manager SP1 コマンドレット リファレンス ドキュメントの「[New-CMSiteSystemServer](http://go.microsoft.com/fwlink/p/?LinkID=271414)」を参照してください。  

## <a name="to-install-site-system-roles-on-a-new-site-system-server"></a>新しいサイト システム サーバーにサイト システムの役割をインストールするには  

1.  Configuration Manager コンソールで、[ **管理**] をクリックします。  

2.  **[管理]** ワークスペースで、 **[サイトの構成]**を展開して **[サーバーとサイト システムの役割]**をクリックします。  

3.  [ **ホーム** ] タブの [ **作成** ] グループで、[ **サイト システム サーバーの作成**] をクリックします。  

4.  **[全般]** ページで、サイト システムの全般設定を指定し、 **[次へ]**をクリックします。  

    > [!TIP]  
    >  インターネットから新しいサイト システムの役割にアクセスするには、インターネット FQDN を指定してください。  

5.  このサイト システム サーバー上で実行されるサイト システムの役割が、プロキシ サーバーを使用してインターネット上の場所に接続しなければならない場合は、[ **プロキシ** ] ページでプロキシ サーバーの設定を指定してから [ **次へ**] をクリックします。  

6.  [ **システムの役割の選択** ] ページで、追加するサイト システムの役割を選択し、[ **次へ**] をクリックします。  

7.  ウィザードを完了します。  

> [!TIP]  
>  Windows PowerShell コマンドレット New-CMSiteSystemServer で、この手順と同じ機能が実行されます。 詳細については、System Center 2012 Configuration Manager SP1 コマンドレット リファレンス ドキュメントの「[New-CMSiteSystemServer](http://go.microsoft.com/fwlink/p/?LinkID=271414)」を参照してください。  



<!--HONumber=Nov16_HO1-->


