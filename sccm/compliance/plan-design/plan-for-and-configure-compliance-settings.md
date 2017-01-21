---
title: "コンプライアンス設定の計画と構成 | System Center Configuration Manager"
description: "System Center Configuration Manager でコンプライアンス設定を行う場合の前提条件と構成タスクについて説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ea20b01-676a-4cc2-b328-0098a41b202e
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 43bbbacfcd0e873974c517f1cb870ebc4d5e003d


---
# <a name="plan-for-and-configure-compliance-settings-in-system-center-configuration-manager"></a>System Center Configuration Manager におけるコンプライアンス設定の計画と構成

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager のコンプライアンス設定に取りかかる前に、把握しておく必要がある前提条件、および実行しなければならない構成タスクがいくつかあります。  

## <a name="prerequisites-for-compliance-settings"></a>コンプライアンス設定の前提条件  

|前提条件|説明|  
|------------------|----------------------|  
|Windows Configuration Manager クライアントを有効にして、コンプライアンス評価用に構成する必要があります。|以下を参照|  
|レポートを実行する場合、サイトのレポートを作成するように構成する必要があります。|[System Center Configuration Manager のレポート](../../core/servers/manage/reporting.md)|  
|必要なセキュリティのアクセス許可。|[**コンプライアンス設定マネージャー**] セキュリティ ロールには、コンプライアンス設定、ユーザー データ、プロファイルの構成項目、リモート接続プロファイルを管理するために必要なアクセス許可が含まれます。<br /><br /> [ロール ベース管理の構成](../../core/servers/deploy/configure/configure-role-based-administration.md)|  

##  <a name="enable-and-configure-compliance-settings-for-windows-pcs-only"></a>コンプライアンス設定の有効化および構成 (Windows コンピューターのみ)  

この手順に従って、コンプライアンス設定に既定のクライアント設定を構成し、階層内のすべてのコンピューターに適用します。 これらの設定を一部のコンピューターのみに適用する場合は、カスタム クライアント デバイス設定を作成して、コンプライアンス設定を使用するコンピューターを含むコレクションに割り当てます。 デバイスの設定をカスタマイズする方法について詳しくは、「[How to configure client settings](../../core/clients/deploy/configure-client-settings.md)」 (クライアント設定の構成方法) を参照してください。  

> [!TIP]  
>  その他のデバイスの種類には、コンプライアンス設定を評価するための特定の構成は不要です。  

1.  Configuration Manager コンソールで、**[管理]**、**[クライアント設定]**、**[既定の設定]**の順にクリックします。  
2.  **[ホーム]** タブの **[プロパティ]** グループで、 **[プロパティ]**をクリックします。  
3.  **既定の設定の** ダイアログ ボックスで、をクリックして **法令遵守の設定**です。  
4.  コンプライアンス設定に、次のクライアント設定を構成します。
    - **[クライアントのコンプライアンス評価を有効にする]**: クライアント デバイスのコンプライアンスを評価するには、[**TRUE**] に設定します。
    - **[コンプライアンスの評価スケジュールを設定する]**: クライアント デバイスの既定のコンプライアンスの評価スケジュールを変更するには、**[スケジュール]** をクリックします。
    - **[ユーザー データとプロファイルを有効にする]**: ユーザー データとプロファイルの構成項目を Windows コンピューターに作成して展開する場合は、このオプションを有効にします。 詳細については、「[ユーザー データとプロファイル構成項目の作成](/sccm/compliance/deploy-use/create-remote-connection-profiles)」を参照してください。
5. [OK] **** をクリックして [既定の設定] **** ダイアログ ボックスを閉じます。  

クライアント コンピューターは、次にクライアント ポリシーをダウンロードするときに、これらの設定で構成されます。  



<!--HONumber=Nov16_HO1-->


