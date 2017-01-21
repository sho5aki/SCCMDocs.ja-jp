---
title: "System Center Configuration Manager と Microsoft Intune を使ったハイブリッド Android モバイル デバイスのセットアップ"
description: "Configuration Manager と Intune を使用して Android モバイル デバイスを管理できるように準備します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c517fe34-0130-465b-a020-bdb555878778
caps.latest.revision: 9
caps.handback.revision: 0
author: NathBarn
ms.author: nathbarn
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: fa189e812a2e3104cb337ccf40c693621745ee53


---
# <a name="set-up-android-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>System Center Configuration Manager と Microsoft Intune を使ったハイブリッド Android モバイル デバイスのセットアップ

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager の場合、ユーザーは Google Play から Android 向けの会社のポータル アプリをダウンロードして、Android デバイス (Samsung KNOX など) を登録できます。 Android 用の会社のポータル アプリを使用すると、コンプライアンス設定の管理、Android デバイスのワイプまたは削除、およびソフトウェアとハードウェアのインベントリの収集を実行できます。 Android 用の会社のポータル アプリが Android デバイスにインストールされていない場合、利用できない管理機能 (インベントリとコンプライアンス設定など) がいくつかありますが、Android デバイスにアプリを展開することはできます。  

## <a name="prepare-to-manage-android-mobile-devices-with-configuration-manager-and-intune"></a>Configuration Manager と Intune を使用して Android モバイル デバイスを管理できるように準備する  
 次の手順に従うと、Configuration Manager で Android デバイスを管理できます。  

#### <a name="to-enable-android-enrollment"></a>Android の登録を有効にするには  

1.  **前提条件** - 任意のプラットフォームの登録をセットアップする前に、「[ハイブリッド MDM をセットアップする](setup-hybrid-mdm.md)」の前提条件と手順を完了しておく必要があります。  

2.  Configuration Manager コンソールの **[管理]** ワークスペースで、**[クラウド サービス]**  >  **[Microsoft Intune サブスクリプション]** に移動します。  

3.  **[ホーム]** タブの **[サブスクリプション]** グループで、**[プラットフォームの構成]**  >  **[Android]** の順にクリックします。  

4.  **[Microsoft Intune サブスクリプションのプロパティ]** ダイアログ ボックスで、 **[Android]** タブを選択し、 **[Android の登録を有効にする]** チェック ボックスをオンにします。  

 セットアップが完了したら、デバイスを登録する方法をユーザーに知らせる必要があります。 「[デバイスの登録についてユーザーに通知する事柄](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)」に関する記事をご覧ください。 この情報は、Microsoft Intune と Configuration Manager の両方によって管理されるモバイル デバイスに適用されます。



<!--HONumber=Nov16_HO1-->


