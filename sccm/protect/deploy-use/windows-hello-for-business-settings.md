---
title: "Windows Hello for Business の設定 | Microsoft Docs"
description: "System Center Configuration Manager に Windows Hello for Business を統合する方法について説明します。"
ms.custom: na
ms.date: 04/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a95bc292-af10-4beb-ab56-2a815fc69304
caps.latest.revision: 17
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 699b79b68440b61904a9053e5004318a2a248bfd
ms.openlocfilehash: 75def95561feb35f2f060f0daa72291983324d4f
ms.contentlocale: ja-jp
ms.lasthandoff: 05/17/2017


---
# <a name="windows-hello-for-business-settings-in-system-center-configuration-manager"></a>System Center Configuration Manager における Windows Hello for Business の設定

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager を、Windows 10 デバイスの代替サインイン方法である Windows Hello for Business (旧称: Microsoft Passport for Windows) と統合することができます。 Hello for Business では、パスワード、スマート カード、または仮想スマート カードの代わりに Active Directory または Azure Active Directory アカウントを使用します。  

Hello for Business を使用すると、パスワードの代わりに **ユーザー ジェスチャ** を使用してログインできます。 ユーザー ジェスチャには、単純な暗証番号 (PIN)、生体認証、または指紋リーダーなどの外部のデバイスがあります。

[Windows Hello for Business の詳細](https://docs.microsoft.com/windows/access-protection/hello-for-business/hello-identity-verification)

 Configuration Manager と Windows Hello for Business を統合するには、次の 2 つの方法があります。  

-   Configuration Manager を使用して、ユーザーがサインインに使用できるジェスチャと使用できないジェスチャを制御できます。  

-   Windows Hello for Business のキー格納プロバイダー (KSP) に認証証明書を格納できます。 詳細については、「[Certificate profiles](introduction-to-certificate-profiles.md)」 (証明書プロファイル) をご覧ください。  

- ドメインに参加しており構成マネージャー クライアントを実行している Windows 10 デバイスに Windows Hello for Business ポリシーを展開できます。 この構成については、以下の「[ドメインに参加している Windows 10 デバイスで Windows Hello for Business を構成する](#configure-windows-hello-for-business-on-domain-joined-windows-10-devices)」で説明されています。 Configuration Manager と Intune (ハイブリッド) を使用している場合、これらの設定は、Windows 10 デバイスと Windows 10 Mobile デバイスで構成できますが、ドメインに参加しており構成マネージャー クライアントを実行しているデバイスでは構成できません。 詳細については、[Windows Hello for Business 設定の構成 (ハイブリッド)](../../mdm/deploy-use/windows-hello-for-business-settings.md)に関する記事を参照してください。

## <a name="configure-windows-hello-for-business-on-domain-joined-windows-10-devices"></a>ドメインに参加している Windows 10 デバイスで Windows Hello for Business を構成する
ドメインに参加している Windows 10 デバイスの Windows Hello for Business 設定は、次の 3 つの方法で制御できます。

- Windows Hello for Business プロファイルを作成して展開することができます。 これは、推奨される方法です。
- グループ ポリシーを使用できます。  
- PowerShell スクリプトを使用できます。

この構成に加えて、「[証明書プロファイルの構成](#configure-a-certificate-profile)」で説明されているように、証明書プロファイルも展開する必要があります。

## <a name="configure-a-windows-hello-for-business-profile"></a>Windows Hello for Business プロファイルの構成  

Configuration Manager コンソールの **[会社のリソースへのアクセス]** で、**[Windows Hello for Business プロファイル]** を右クリックし、**[新規]** を選択してプロファイル ウィザードを開始します。 ウィザードによって要求された設定を指定し、最後のページで設定を確認して、**[閉じる]** をクリックします。 設定の例を次に示します。  

![Windows Hello for Business の設定](../media/Hello-for-Business-settings.png)

## <a name="configure-windows-hello-for-business-with-group-policy-in-active-directory"></a>Active Directory のグループ ポリシーを使用して Windows Hello for Business を構成する  

Active Directory のグループ ポリシーを使用して、ユーザーが Windows にログインするときに、そのユーザーの Hello for Business 資格情報をプロビジョニングするように Windows 10 ドメイン参加デバイスを構成できます。

1.  Windows Server コンピューターでサーバー マネージャーを開き、**[ツール]** > **[グループ ポリシー管理]** に移動します。    

2.  **[グループ ポリシー管理]** ダイアログ ボックスで、Automatic Workplace Join を有効にするドメインを展開します。    

3.  **[グループ ポリシー オブジェクト]**を右クリックして、 **[新規]**をクリックします。  

4.  **[新しい GPO]** ダイアログ ボックスに、新しいグループ ポリシー オブジェクトの名前 (**Windows Hello for Business を有効にする**など) を入力して、**[OK]** をクリックします。  

5.  **[グループ ポリシー オブジェクト]** ノードで、作成したオブジェクトを右クリックし、 **[編集]**をクリックします。  

6.  **[グループ ポリシー管理エディター]** ダイアログ ボックスで、**[コンピューターの構成]** > **[ポリシー]** > **[管理用テンプレート]** > **[Windows コンポーネント]** > **[Windows Hello for Business]** の順に移動します。  

7.  **[Windows Hello for Business を有効にする]** を右クリックし、**[編集]** をクリックします。   

8.  **[有効]**を選び、 **[適用]**をクリックし、 **[OK]**をクリックします。

作成したグループ ポリシー オブジェクトを任意の場所にリンクできます。 たとえば、    

   Windows 10 ドメイン参加コンピューターが配置される AD の特定の組織単位 (OU)。    

   Azure AD に自動的に登録される Windows 10 ドメイン参加コンピューターを含む特定のセキュリティ グループ。    

## <a name="configure-windows-hello-for-business-by-deploying-a-powershell-script-with-configuration-manager"></a>Configuration Manager で PowerShell スクリプトを展開して Windows Hello for Business を構成する    
Configuration Manager アプリケーション管理を使用して、次の PowerShell スクリプトを作成して展開できます。    

**powershell.exe -ExecutionPolicy Bypass -NoLogo -NoProfile -Command "& {New-ItemProperty "HKLM:\Software\Policies\Microsoft\PassportForWork" -Name "Enabled" -Value 1 -PropertyType "DWord" -Force}" ** 

Configuration Manager アプリケーション管理の詳細については、「[System Center Configuration Manager でのアプリケーション管理の概要](/sccm/apps/understand/introduction-to-application-management)」をご覧ください。  

## <a name="configure-a-certificate-profile-to-enroll-the-windows-hello-for-business-enrollment-certificate-in-configuration-manager"></a>Configuration Manager で証明書プロファイルを構成して、Windows Hello for Business の登録証明書を登録する  
 Windows Hello for Business の証明書ベースのログオンまたは Microsoft Hello を使用する場合は、次の構成を行います。  

-   Configuration Manager の証明書プロファイル。  

-   証明書プロファイルで、スマート カード ログオンの EKU を使用するテンプレートを選びます。  

-    ビジネス向け Windows Hello キー コンテナーに証明書プロファイルを保存する場合、証明書プロファイルで**スマート カード ログオン** EKU が使用されているときには、キー登録で証明書が正しく検証されるように次のアクセス許可を構成する必要があります。
最初に **Key Admins** グループを作成しておき、すべての Configuration Manager 管理ポイント コンピューターをこのグループに追加する必要があります。

    1.    ドメイン管理者または同等の資格情報でドメイン コントローラーまたは管理ワークステーションにログインします。
    2.    **[Active Directory Users and Computers]** を開きます。
    3.    ナビゲーション ウィンドウで、ドメイン名を右クリックし、**[プロパティ]** をクリックします。
    4.    **[*<domain name>* のプロパティ]** ダイアログ ボックスの **[セキュリティ]** タブで、**[詳細設定]** をクリックします。 **[セキュリティ]** タブが表示されない場合、**[Active Directory Users and Computers]** の **[表示]** メニューの **[高度な機能]** をオンにします。
    5.    [ **追加**] をクリックします。
    6.    **[*<domain name>* のアクセス許可エントリ]** ダイアログ ボックスで **[プリンシパルの選択]** をクリックします。
    7.    **[ユーザー、コンピューター、サービス アカウント、またはグループの選択]** ダイアログ ボックスの **[選択するオブジェクト名を入力します]** テキスト ボックスに「**Key Admins**」と入力します。  **[OK]**をクリックします。
    8.    **[適用先]** リストから **[Descendant User objects (子孫ユーザー オブジェクト)]** を選択します。
    9.    ページの一番下までスクロールし、**[すべてクリア]** をクリックします。
    10.    **[プロパティ]** セクションで **[Read msDS-KeyCredentialLink (msDS-KeyCredentialLink を読む)]** を選択します。
    11.    **[OK]** を 3 回クリックし、タスクを完了します。


 詳細については、「[Certificate profiles](introduction-to-certificate-profiles.md)」 (証明書プロファイル) をご覧ください。  





