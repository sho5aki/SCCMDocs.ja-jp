---
title: "Active Directory スキーマ | System Center Configuration Manager"
description: "System Center Configuration Manager の Active Directory スキーマを拡張して、クライアントの展開と構成のプロセスを簡略化します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: bc15ee7e-4d0a-4463-ae2c-f72d8d45d65d
caps.latest.revision: 17
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: d4cdaa646265b2d05ec93aeaefaf3a6e7a2c269f


---
# <a name="extend-the-active-directory-schema-for-system-center-configuration-manager"></a>System Center Configuration Manager 向けに Active Directory スキーマを拡張する

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager 向けに Active Directory スキーマを拡張すると、クライアントが簡単にアクセスできる安全な場所に重要な情報を発行するために Configuration Manager サイトが使用する新しい構造が Active Directory に導入されます。  

 オンプレミスのクライアントを管理する場合は、Active Directory 拡張スキーマと共に Configuration Manager を使用することをお勧めします。 拡張スキーマにより、クライアントの展開と構成のプロセスが簡略化され、クライアントがリソース (コンテンツ サーバーや、さまざまな Configuration Manager サイト システムの役割によって提供される追加サービスなど) を効率的に見つけることができるようになります。  

-   Configuration Manager の展開における拡張スキーマの役割についてあまり詳しくない場合は、「[System Center Configuration Manager のスキーマ拡張](../../../core/plan-design/network/schema-extensions.md)」を参照して、使用するかどうかを判断してください。  

-   拡張スキーマを使用しない場合は、DNS や WINS など、他の方法を構成してサービスやサイト システム サーバーを検索できます。 サービスの場所のこれらの方法には追加の構成が必要であり、クライアントが使用するサービスの場所に適した方法ではありません。 詳細については、「[クライアントが System Center Configuration Manager のサイト リソースやサービスを検索する方法を理解する](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md)」を参照してください。  

-   Active Directory スキーマが Configuration Manager 2007 または System Center 2012 Configuration Manager 用に拡張されている場合は、これ以上の操作を行う必要はありません。 スキーマ拡張は変更されず、既に使用可能な状態になっています。  

スキーマの拡張は、どのフォレストでも 1 回限りの操作です。 Active Directory スキーマを拡張し、拡張されたスキーマを使用するには、以下の操作を実行します。  

## <a name="step-1-extend-the-schema"></a>手順 1. スキーマの拡張  
Configuration Manager のスキーマを拡張するには、次の操作が必要です。  

-   Schema Admins セキュリティ グループのメンバーであるアカウントを使用します。  

-   スキーマ マスター ドメイン コントローラーにログインします。  

-   **Extadsch.exe** ツールを実行するか、または LDIFDE コマンド ライン ユーティリティと **ConfigMgr_ad_schema.ldf** ファイルを使用します。 このツールとファイルはどちらも Configuration Manager インストール メディアの **SMSSETUP\BIN\X64** フォルダーにあります。  

#### <a name="option-a-use-extadschexe"></a>オプション A: Extadsch.exe を使用する  

1.  **extadsch.exe** を実行して、新しいクラスと属性を Active Directory スキーマに追加します。  

    > [!TIP]  
    >  このツールをコマンド ラインから実行すると、実行中にフィードバックが表示されます。  

2.  システム ドライブのルートにある extadsch.log を確認することにより、スキーマの拡張が成功したことを確認します。  

#### <a name="option-b-use-the-ldif-file"></a>オプション B: LDIF ファイルを使用する  

1.  **ConfigMgr_ad_schema.ldf** ファイルを編集して、拡張する Active Directory ルート ドメインを定義します。  

    -   このファイルでは、テキスト **DC=x** のすべてのインスタンスを、拡張するドメインのフル ネームで置き換える必要があります。  

    -   たとえば、拡張するドメインのフル ネームが widgets.microsoft.com である場合、ファイル内にあるすべての DC=x のインスタンスを **DC=widgets, DC=microsoft, DC=com**に変更します。  

2.  LDIFDE コマンド ライン ユーティリティを使用して、 **ConfigMgr_ad_schema.ldf** ファイルの内容を Active Directory ドメイン サービスにインポートします。  

    -   たとえば、次のコマンド ラインは、スキーマ拡張を Active Directory Domain Services にインポートし、詳細ログ記録をオンにして、インポート処理中にログ ファイルを作成します: **ldifde -i -f ConfigMgr_ad_schema.ldf -v -j &lt;ログ ファイルの保存場所\>**  

3.  前の手順で使用したコマンド ラインによって作成されたログ ファイルを確認することにより、スキーマの拡張が成功したことを確認できます。  

## <a name="step-2-create-the-system-management-container-and-grant-sites-permissions-to-the-container"></a>手順 2.  System Management コンテナーの作成とコンテナーへのサイトに対するアクセス許可の付与  
 スキーマを拡張したら、Active Directory Domain Services (AD DS) で **System Management** という名前のコンテナーを作成する必要があります。  

-   データを Active Directory に発行するプライマリ サイトまたはセカンダリ サイトがあるドメインごとに、このコンテナーを 1 回作成します。  

-   そのドメインのデータを発行する各プライマリ サイト サーバーおよびセカンダリ サイト サーバーのコンピューター アカウントに、各コンテナーのアクセス許可を付与します。 各アカウントには、コンテナーに対する**フルコントロール**と、**適用先**が**このオブジェクトとすべての子オブジェクト**である拡張アクセス許可が必要です  

#### <a name="to-add-the-container"></a>コンテナーを追加する方法  

1.  Active Directory ドメイン サービス内の **System** コンテナーで**すべての子オブジェクトの作成**アクセス許可があるアカウントを使用します。  

2.  **ADSI エディター** (adsiedit.msc) を実行して、サイト サーバーのドメインに接続します。  

3.  コンテナーを作成します。  

    -   **[ドメイン]** &lt;コンピューターの完全修飾ドメイン名\>、&lt;識別名\> の順に展開して **[CN=System]** を右クリックし、**[新規]**、**[オブジェクト]** の順にクリックします。  

    -   **[オブジェクトの作成]** ダイアログ ボックスで、 **[コンテナー]**を選択し、 **[次へ]**をクリックします。  

    -   **[値]** ボックスに、「 **System Management**」と入力し、 **[次へ]**をクリックします。  

4.  アクセス許可を割り当てます。  

    > [!NOTE]  
    >  必要に応じて、Active Directory のユーザーとコンピューター管理ツール (dsa.msc) など他のツールを使用して、コンテナーにアクセス許可を追加することができます。  

    -   **[CN=System Management]**を右クリックし、 **[プロパティ]**をクリックします。  

    -   **[セキュリティ]** タブを選び、**[追加]** をクリックして、  
        **フル コントロール** アクセス許可があるサイト サーバーのコンピューター アカウントを追加します。  

    -   **[詳細設定]** をクリックして、サイト サーバーのコンピューター アカウントを選択し、**[編集]** をクリックします。  

    -   **[適用先]** の一覧で **[このオブジェクトとすべての子オブジェクト]**を選択します。  

5.  **[OK]** をクリックしてコンソールを閉じ、構成を保存します。  

## <a name="step-3-configure-sites-to-publish-to-active-directory-domain-services"></a>手順 3. Active Directory Domain Services に発行するサイトの構成  
 コンテナーを構成してアクセス許可を付与し、Configuration Manager プライマリ サイトをインストールした後、Active Directory にデータを発行するようにそのサイトを構成できます。  

 発行の詳細については、「 [Publish site data for System Center Configuration Manager](../../../core/servers/deploy/configure/publish-site-data.md)」をご覧ください。  



<!--HONumber=Nov16_HO1-->


