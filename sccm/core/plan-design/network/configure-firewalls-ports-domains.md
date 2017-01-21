---
title: "ファイアウォールとドメイン | System Center Configuration Manager"
description: "System Center Configuration Manager 通信の準備としてファイアウォール、ポート、ドメインを構成します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d6993bba-f6bd-4639-adbf-efc1c638b2f3
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: cd2da8ea3bf0e1351f791d88af3dcbf95f8d6be8


---
# <a name="configure-firewalls-ports-and-domains-for-system-center-configuration-manager"></a>System Center Configuration Manager のファイアウォール、ポート、ドメインの構成

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager をサポートするためにネットワークを準備するには、Configuration Manager で使用される通信をファイアウォールで許可するなど、インフラストラクチャの構成を計画します。  

|考慮事項|説明|  
|-------------------|-------------|  
|さまざまな Configuration Manager 機能で使用する**ポートとプロトコル**。 必須のポートと、カスタマイズできる **ドメインとサービス** があります。|ほとんどの Configuration Manager 通信では、HTTP 通信にポート 80、HTTPS 通信にポート 443 など、共通のポートを使用します。 ただし、[一部のサイト システムの役割では、カスタム Web サイトとカスタム ポートの使用をサポート](/sccm/core/plan-design/network/websites-for-site-system-servers)しています。<br /><br /> **Configuration Manager を展開する前に**、使用する予定のポートを特定し、ファイアウォールを適宜構成します。<br /><br /> **後で、Configuration Manager をインストールした後でポートを変更する必要がある場合**、必ずデバイスとネットワークでファイアウォールを更新し、Configuration Manager 内からポートの構成を変更してください。<br /><br /> 詳細については、次をご覧ください。 </br>- [クライアント通信ポートを構成する方法](../../../core/clients/deploy/configure-client-communication-ports.md) </br>- [Configuration Manager で使用されるポート](../../../core/plan-design/hierarchy/ports.md) </br>- [サービス接続ポイントのインターネット アクセス要件](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_urls)|  
|サイト サーバーおよびクライアントがアクセスすることが必要になる場合がある**ドメインとサービス** 。|Configuration Manager 機能では、サイト サーバーおよびクライアントが Windowsudpate.microsoft.com や Microsoft Intune サービスなどのインターネット上の特定のサービスおよびドメインにアクセスする必要がある場合があります。<br /><br /> Microsoft Intune を使用してモバイル デバイスを管理する場合は、[Intune で必要なポートとドメインへのアクセスも構成する必要があります](https://docs.microsoft.com/en-us/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)。|  
|サイト システム サーバーとクライアント通信用の**プロキシ サーバー** 。 異なるサイト システム サーバーとクライアントに対して別のプロキシ サーバーを指定することができます。|これらの構成はサイト システムの役割またはクライアントのインストール時に行われるため、サイト システムの役割とクライアントを構成するときに注意が必要なのは、後で参照するプロキシ サーバー構成のみです。<br /><br /> 展開でプロキシ サーバーを使用する必要があるかどうかがわからない場合は、「[System Center Configuration Manager でのプロキシ サーバーのサポート](../../../core/plan-design/network/proxy-server-support.md)」を確認し、プロキシ サーバーを使用できるサイト システムの役割とクライアントの動作についてご理解ください。|  



<!--HONumber=Nov16_HO1-->


