---
title: "System Center Configuration Manager でのセキュリティの構成"
description: "System Center Configuration Manager のセキュリティ関連オプションを構成します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 552e7e3d-e584-4a7c-9155-0f796a14b678
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 2e43979e1c5cdf9559b8a9f11c8f8de4008ae406


---
# <a name="configure-security-in-system-center-configuration-manager"></a>System Center Configuration Manager でのセキュリティの構成

*適用対象: System Center Configuration Manager (Current Branch)*

このトピック内の情報は、以下の System Center Configuration Manager 用のセキュリティ関連オプションを構成する上で参考になります。  

-   [Configure Settings for Client PKI Certificates](#BKMK_ConfigureClientPKI)  

-   [署名と暗号化の構成](#BKMK_ConfigureSigningEncryption)  

-   [Configure Role-Based Administration](#BKMK_ConfigureRBA)  

-   [Manage Accounts that are Used by Configuration Manager](#BKMK_ManageAccounts)  

##  <a name="a-namebkmkconfigureclientpkia-configure-settings-for-client-pki-certificates"></a><a name="BKMK_ConfigureClientPKI"></a> クライアント PKI 証明書の設定の構成  
インターネット インフォメーション サービス (IIS) を使用するサイト システムへのクライアント接続に公開キー基盤 (PKI) 証明書を使用する場合、次の手順に従ってこれらの証明書の設定を構成します。  

#### <a name="to-configure-client-pki-certificate-settings"></a>クライアント PKI 証明書の設定を構成するには  

1.  Configuration Manager コンソールで、[ **管理**] をクリックします。  

2.  **[管理]** ワークスペースで、 **[サイトの構成]**を展開して、 **[サイト]**をクリックしてから、構成するプライマリ サイトをクリックします。  

3.  **[ホーム]** タブの **[プロパティ]** グループで、 **[プロパティ]**をクリックして、 **[クライアント コンピューターの通信方法]** タブをクリックします。  

    このタブは、プライマリ サイトでのみ使用できます。 [クライアント コンピューターの通信方法 **** ] タブが表示されない場合、中央管理サイトまたはセカンダリ サイトに接続されていないことを確認してください。  

4.  サイトに割り当てられているクライアントが IIS を使用するサイト システムに接続するときに、常にクライアント PKI 証明書を使用する必要がある場合は、[HTTPS のみ] をクリックします。 **** または、クライアントが PKI 証明書を使用する必要がない場合は、[HTTPS または HTTP] をクリックします。 ****  

5.  **[HTTPS または HTTP]**を選択した場合は、HTTP 接続にクライアント PKI 証明書を使用する際に、 **[使用可能な場合はクライアント PKI 証明書 (クライアント認証機能) を使用する]** をクリックします。 クライアントは、サイト システムに対する認証に、自己署名入り証明書ではなく、この証明書を使用します。 このオプションは、[HTTPS のみ] を選択すると自動的に選択されます。 ****  

    クライアントがインターネット上にあることが検出された場合、またはクライアントがインターネットのみでのクライアント管理向けに構成されている場合、このクライアントは常にクライアント PKI 証明書を使用します。  

6.  **[変更]** をクリックして、クライアントで複数の有効な PKI クライアント証明書が使用可能な場合のために、選択したクライアント選択方法を構成してから、 **[OK]**をクリックします。  

    クライアント証明書の選択方法の詳細については、「[PKI クライアント証明書の選択の計画](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForClientCertificateSelection)」を参照してください。  

7.  クライアントが証明書失効リスト (CRL) をチェックするかどうかのチェック ボックスを、オンまたはオフにします。  

    クライアントの CRL チェックの詳細については、「[PKI 証明書失効の計画](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForCRLs)」を参照してください。  

8.  クライアントに信頼されたルート証明機関 (CA) 証明書を指定する必要がある場合は、 **[設定]**をクリックしてルート CA 証明書ファイルをインポートしてから、 **[OK]**をクリックします。  

    この設定の詳細については、「[PKI 信頼されたルート証明書と証明書発行者リストの計画](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRootCAs)」を参照してください。  

9. [OK] をクリックして、サイトの [プロパティ] ダイアログ ボックスを閉じます。 ****  

階層内のすべてのプライマリ サイトで、この手順を繰り返します。  

##  <a name="a-namebkmkconfiguresigningencryptiona-configure-signing-and-encryption"></a><a name="BKMK_ConfigureSigningEncryption"></a> 署名と暗号化の構成  
サイト内のすべてのクライアントがサポートすることができるサイト システムに、最も安全な署名設定と暗号化設定を構成します。 これらの設定が特に重要になるのが、自己署名入り証明書を使用してクライアントが HTTP 経由でサイト システムと通信する場合です。  

#### <a name="to-configure-signing-and-encryption-for-a-site"></a>サイトに署名と暗号化を構成するには  

1.  Configuration Manager コンソールで、[ **管理**] をクリックします。  

2.  **[管理]** ワークスペースで、 **[サイトの構成]**を展開して、 **[サイト]**をクリックしてから、構成するプライマリ サイトをクリックします。  

3.  **[ホーム]** タブの **[プロパティ]** グループで、 **[プロパティ]**をクリックして、 **[署名と暗号化]** タブをクリックします。  

    このタブは、プライマリ サイトでのみ使用できます。 [署名および暗号化 **** ] タブが表示されない場合、中央管理サイトまたはセカンダリ サイトに接続されていないことを確認してください。  

4.  必要な署名オプションと暗号化オプションを構成し、[OK] をクリックします。 ****  

    > [!WARNING]  
    >  [SHA-256 を必要とする] を選択する場合は、サイトに割り当てられている可能性があるすべてのクライアントがこのハッシュ アルゴリズムをサポートできること、またはこれらのクライアントに有効な PKI クライアント認証証明書があることを確認してからにしてください。 **** SHA-256 をサポートするクライアントに対する更新プログラムまたは修正プログラムのインストールが必要な場合があります。 たとえば、Windows Server 2003 SP2 を実行しているコンピューターでは、 [サポート技術情報 938397](http://go.microsoft.com/fwlink/p/?LinkId=226666)に示されている修正プログラムをインストールする必要があります。  
    >   
    >  このオプションを選択した場合、クライアントが SHA-256 をサポートしておらず、自己署名入り証明書を使用できないと、Configuration Manager はクライアントを拒否します。 この場合は、SMS_MP_CONTROL_MANAGER コンポーネントにメッセージ ID 5443 が記録されます。  

5.  **[OK]** をクリックして、サイトの **[プロパティ]** ダイアログ ボックスを閉じます。  

階層内のすべてのプライマリ サイトで、この手順を繰り返します。  

##  <a name="a-namebkmkconfigurerbaa-configure-role-based-administration"></a><a name="BKMK_ConfigureRBA"></a> 役割に基づいた管理の構成  
役割に基づいた管理では、セキュリティ ロール、セキュリティ スコープ、および割り当てられたコレクションを組み合わせて、各管理ユーザーの管理スコープを定義します。 管理スコープには、Configuration Manager コンソールで管理ユーザーが表示できるオブジェクト、および管理ユーザーが実行するアクセス許可を持っている、それらのオブジェクトに関連するタスクが含まれます。 役割に基づいた管理の構成は、階層内の各サイトに適用されます。  

次のリンクが「[System Center Configuration Manager のロール ベース管理の構成](../../../core/servers/deploy/configure/configure-role-based-administration.md)」トピックから関連するセクションにつながっています。  

-   [カスタム セキュリティ ロールの作成](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole)  

-   [セキュリティ ロールの構成](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecRole)  

-   [オブジェクトのセキュリティ スコープの構成](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecScope)  

-   [セキュリティを管理するコレクションの構成](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigColl)  

-   [新しい管理ユーザーの作成](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_Create_AdminUser)  

-   [管理ユーザーの管理スコープの変更](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ModAdminUser)  

> [!IMPORTANT]  
>  独自の管理スコープでオブジェクトと設定を定義し、別の管理ユーザーの役割に基づいた権限を構成するときに、これらのオブジェクトと設定を割り当てることができます。 ロール ベース管理の計画方法については、「[System Center Configuration Manager のロール ベース管理の基礎](../../../core/understand/fundamentals-of-role-based-administration.md)」を参照してください。  

##  <a name="a-namebkmkmanageaccountsa-manage-accounts-that-are-used-by-configuration-manager"></a><a name="BKMK_ManageAccounts"></a> Configuration Manager で使用するアカウントの管理  
Configuration Manager は、Windows アカウントのさまざまなタスクとユーザーをサポートしています。  

さまざまなタスク用に構成されているアカウントを表示し、各アカウントについて Configuration Manager が使用するパスワードを管理するには、次の手順に従います。  

#### <a name="to-manage-accounts-that-are-used-by-configuration-manager"></a>Configuration Manager で使用するアカウントを管理するには  

1.  Configuration Manager コンソールで、[ **管理**] をクリックします。  

2.  **[管理]** ワークスペースで、 **[セキュリティ]**を展開してから、 **[アカウント]** をクリックして、Configuration Manager に構成されたアカウントを表示します。  

3.  Configuration Manager に構成されているアカウントのパスワードを変更するには、そのアカウントを選択します。  

4.  **[ホーム]** タブの **[プロパティ]** グループで、 **[プロパティ]**をクリックします。  

5.  **[設定]** をクリックして、 **[Windows ユーザー アカウント]** ダイアログ ボックスを開きます。Configuration Manager のアカウントに使用する新しいパスワードを指定します。  

    > [!NOTE]  
    >  指定するパスワードが、Active Directory ユーザーとコンピューターのアカウントに指定されているパスワードと一致している必要があります。  

6.  [OK] をクリックして手順を完了します。 ****  



<!--HONumber=Nov16_HO1-->


