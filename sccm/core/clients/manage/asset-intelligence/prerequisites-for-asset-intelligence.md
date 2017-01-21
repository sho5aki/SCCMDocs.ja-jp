---
title: "資産インテリジェンスの前提条件 | System Center Configuration Manager"
description: "System Center Configuration Manager の資産インテリジェンスの前提条件を取得します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 23ab4f94-7bfe-436e-8a6a-029409a2730c
caps.latest.revision: 10
caps.handback.revision: 0
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 12f7ea7223237f57fb2d90f0f7b66381e8f09a1f


---
# <a name="prerequisites-for-asset-intelligence-in-system-center-configuration-manager"></a>System Center Configuration Manager の資産インテリジェンスの前提条件

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager の資産インテリジェンスには、外部依存関係と製品内部依存関係があります。  

## <a name="dependencies-external-to-configuration-manager"></a>Configuration Manager 外部の依存関係  
 次の表は、Configuration Manager 外部の資産インテリジェンスの依存関係を示します。  

|依存関係|説明|  
|----------------|----------------------|  
|ログオン成功イベントの前提条件の監査|4 つの資産インテリジェンス レポートには、クライアント コンピューターの Windows セキュリティ イベント ログから収集された情報が表示されます。 セキュリティ イベント ログ設定がログオンに成功したすべてのイベントをログに記録するように設定されていないと、適切なハードウェア インベントリ レポート クラスが有効になっていても、レポートにはデータが表示されません。<br /><br /> 次の資産インテリジェンス レポートは、Windows セキュリティ イベント ログ情報を使用します。<br /><br /> -   ハードウェア 03A - プライマリ コンピューター ユーザー<br />-   ハードウェア 03B - 特定のプライマリ コンソール ユーザーのコンピューター<br />-   ハードウェア 04A - 共有 (複数ユーザー向け) コンピューター<br />-   ハードウェア 05A - 特定のコンピューターのコンソール ユーザー<br /><br /> ハードウェア インベントリ クライアント エージェントを有効にして、レポートをサポートするのに必要な情報のインベントリを作成するには、まずクライアントの Windows セキュリティ イベント ログ設定を変更して、ログオンに成功したすべてのイベントをログに記録し、 **SMS_SystemConsoleUser** ハードウェア インベントリ レポート クラスを有効にする必要があります。 すべてのログオン成功イベントをログに記録するようにセキュリティ イベント ログ設定を変更する方法の詳細については、「[Enable auditing of success logon events](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md#BKMK_EnableSuccessLogonEvents)」(ログオン成功イベントの監査を有効にする) を参照してください。|  

> [!NOTE]  
>  **SMS_SystemConsoleUser** ハードウェア インベントリ レポート クラスには、ログの長さに関係なく、セキュリティ イベント ログの過去 90 日間のログオン成功データのみが保持されます。 セキュリティ イベント ログのデータが 90 日未満の場合は、ログ全体が読み取られます。  

## <a name="dependencies-internal-to-configuration-manager"></a>Configuration Manager 内部の依存関係  
 次の表は、Configuration Manager 内部の資産インテリジェンスの依存関係を示します。  

|依存関係|説明|  
|----------------|----------------------|  
|クライアント エージェントに関する前提条件|資産インテリジェンス レポートの内容は、クライアントのハードウェアおよびソフトウェア インベントリ レポートから取得したクライアント情報によって異なります。 すべての資産インテリジェンス レポートに必要な情報を取得するには、次のクライアント エージェントを有効にする必要があります。<br /><br /> -   ハードウェア インベントリのクライアント エージェント<br />-   ソフトウェア使用状況測定クライアント エージェント|  
|ハードウェア インベントリのクライアント エージェントの依存関係|一部の資産インテリジェンス レポートに必要なインベントリ データを収集するには、ハードウェア インベントリのクライアント エージェントを有効にする必要があります。 さらに、資産インテリジェンス レポートが依存するハードウェア インベントリ レポート クラスを、プライマリ サイト サーバーのコンピューターで有効にする必要があります。<br /><br /> ハードウェア インベントリのクライアント エージェントを有効にする方法については、「[Configuration Manager でハードウェア インベントリを構成する方法](../../../../core/clients/manage/inventory/extend-hardware-inventory.md)」を参照してください。|  
|ソフトウェア メータリング クライアント エージェントの依存関係|資産インテリジェンス ソフトウェアのレポートの多くは、ソフトウェア使用状況測定クライアント エージェントのデータを使用します。 ソフトウェア使用状況測定クライアント エージェントを有効にする方法については、「[Monitor app usage with software metering in System Center Configuration Manager](../../../../apps/deploy-use/monitor-app-usage-with-software-metering.md)」(System Center Configuration Manager のソフトウェア使用状況測定でアプリの使用を監視する) を参照してください。<br /><br /> 次の資産インテリジェンス レポートでは、ソフトウェア使用状況測定クライアント エージェントを使用してデータを取得します。<br /><br /> -   ソフトウェア 07A - 複数のコンピューターによって最近使用された実行可能ファイル<br />-   ソフトウェア 07B - 指定した実行可能ファイルを最近使用したコンピューター<br />-   ソフトウェア 07C - 特定のコンピューターで最近使用した実行可能ファイル<br />-   ソフトウェア 08A - 複数のユーザーによって最近使用された実行可能ファイル<br />-   ソフトウェア 08B - 指定した実行可能ファイルを最近使用したユーザー<br />-   ソフトウェア 08C - 指定したユーザーが最近使用した実行可能ファイル|  
|資産インテリジェンス ハードウェア インベントリ レポート クラスの前提条件|Configuration Manager の資産インベントリ レポートは、特定のハードウェア インベントリ レポート クラスに依存します。 ハードウェア インベントリ レポート クラスが有効になり、クライアントがこれらのクラスに基づいてハードウェア インベントリをレポートするまで、関連付けられた資産インテリジェンス レポートにはデータが表示されません。 次のハードウェア インベントリ レポート クラスを有効にすると、資産インテリジェンス レポートの要件をサポートできます。<br /><br /> -   SMS_SystemConsoleUsage<sup>1</sup><br />-   SMS_SystemConsoleUser<sup>1</sup><br />-   SMS_InstalledSoftware<br />-   SMS_AutoStartSoftware<br />-   SMS_BrowserHelperObject<br />-   Win32_USBDevice<br />-   SMS_InstalledExecutable<br />-   SMS_SoftwareShortcut<br />-   SoftwareLicensingService<br />-   SoftwareLicensingProduct<br />-   SMS_SoftwareTag<br /><br /> <sup>1</sup> 既定では **SMS_SystemConsoleUsage** および **SMS_SystemConsoleUser** の資産インテリジェンス ハードウェア インベントリ レポート クラスは有効になっています。<br /><br /> **[資産とコンプライアンス]** ワークスペースで **[資産インテリジェンス]** ノードをクリックすると、Configuration Manager コンソールで資産インテリジェンス ハードウェア インベントリ レポート クラスを編集できます。 詳細については、「[Configuration Manager の資産インテリジェンスの構成](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md)」トピックの「[資産インテリジェンスのハードウェア インベントリ レポート クラスの有効化](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md#BKMK_EnableAssetIntelligence)」セクションを参照してください。|  
|レポート サービス ポイント|ソフトウェア更新レポートを表示するには、事前にレポート サービス ポイント サイト システムの役割がインストールされている必要があります。 レポート サービス ポイント作成の詳細については、「 [Configuration Manager のレポートの構成](http://go.microsoft.com/fwlink/p/?LinkId=232661)」を参照してください。|  



<!--HONumber=Nov16_HO1-->


