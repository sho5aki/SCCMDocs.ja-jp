---
title: Endpoint Protection | Microsoft Docs
description: "Configuration Manager 階層内のクライアント コンピューターのマルウェア対策ポリシーと Windows ファイアウォールのセキュリティを管理する方法について説明します。"
ms.custom: na
ms.date: 12/9/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76c90f64-d729-456b-8304-01852cd66fb6
caps.latest.revision: 11
author: NathBarn
ms.author: nathbarn
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 9fcbc0bb9c8ccd4265381ca4db7a363c8ae3b54a
ms.openlocfilehash: 59313bd6f76433782a79ab3ee9d6240f767fbd76


---
# <a name="endpoint-protection-in-system-center-configuration-manager"></a>System Center Configuration Manager での Endpoint Protection

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager の Endpoint Protection を使用して、Configuration Manager 階層内のクライアント コンピューターのマルウェア対策ポリシーと Windows ファイアウォールのセキュリティを管理できます。  

> [!IMPORTANT]  
>  Configuration Manager 階層内のクライアントの管理に Endpoint Protection を使用するにはライセンスが必要です。  

 Configuration Manager で Endpoint Protection を使用すると、次のようなメリットがあります。  

-   マルウェア対策ポリシーと Windows ファイアウォールの設定を構成し、選択したコンピューターのグループに対する Windows Defender Advanced Threat Protection を管理します。  

-   Configuration Manager ソフトウェア更新プログラムを使用して最新のマルウェア対策の定義ファイルをダウンロードし、クライアント コンピューターを最新の状態に保ちます。  

-   クライアント コンピューターでマルウェアが検出された場合は、電子メールによる通知送信、コンソール内の監視機能の使用、およびレポートの表示を行うことで管理ユーザーに通知することができます。  

Windows 10 コンピューターでは、Endpoint Protection 管理のために追加のクライアントは不要です。 Windows 8.1 およびそれ以前のコンピューターでは、Endpoint Protection により、構成マネージャー クライアントに加え、独自のクライアントもインストールされます。 Endpoint Protection は管理できます。 Endpoint Protection クライアントには、次の機能があります。  

-   マルウェアとスパイウェアの検出と修復  

-   ルートキットの検出と修復  

-   重大な脆弱性の評価、および定義とエンジンの自動更新  

-   ネットワーク検査システム経由のネットワークの脆弱性の検出  

-   Cloud Protection Service との統合によりマルウェアを Microsoft に報告。 このサービスに加入すると、コンピューターで不明なマルウェアが検出された場合に、Endpoint Protection クライアントまたは Windows Defender がマルウェア プロテクション センターから最新の定義をダウンロードできます。  

> [!NOTE]  
>  Endpoint Protection クライアントは、Hyper-V を実行しているサーバーと、サポートされているオペレーティング システムを搭載したゲスト仮想マシンにインストールできます。 CPU の過剰使用を避けるため、Endpoint Protection のアクションには複数の保護サービスが同時に実行されないように遅延をランダムに発生させる機能が組み込まれています。  

 さらに、Configuration Manager の Endpoint Protection を使用すると、Configuration Manager コンソールで Windows ファイアウォールの設定を管理することができます。  

 [シナリオ例: System Center Configuration Manager で System Center Endpoint Protection を使用してマルウェアからコンピューターを保護する](scenarios-endpoint-protection.md) Endpoint Protection および Windows ファイアウォール。  


## <a name="managing-malware-with-endpoint-protection"></a>Endpoint Protection によるマルウェアの管理  
 Configuration Manager の Endpoint Protection を使用すれば、Endpoint Protection クライアント構成用の設定を含むマルウェア対策ポリシーを作成することができます。 その後、このマルウェア対策ポリシーをクライアント コンピューターに展開し、**[監視]** ワークスペースの **[セキュリティ]** の **[Endpoint Protection のステータス]** ノードで監視するか、Configuration Manager レポートを使って監視できます。  

 追加情報:  

-   [System Center Configuration Manager で Endpoint Protection 用にマルウェア対策ポリシーを作成し展開する方法](endpoint-antimalware-policies.md) - 構成可能な設定の一覧を使用してマルウェア対策ポリシーを作成、展開、および監視します。  

-   [System Center Configuration Manager で Endpoint Protection を監視する方法](monitor-endpoint-protection.md) - アクティビティ レポート、感染したクライアント コンピューターなどを監視します。  

-   [System Center Configuration Manager での Endpoint Protection のためのマルウェア対策ポリシーとファイアウォール設定の管理方法](endpoint-antimalware-firewall.md) - クライアント コンピューターで検出されたマルウェアを修復します。  


## <a name="managing-windows-firewall-with-endpoint-protection"></a>Endpoint Protection による Windows ファイアウォールの管理  
 Configuration Manager の Endpoint Protection には、クライアント コンピューター上の Windows ファイアウォールの基本管理機能が備わっています。 各ネットワーク プロファイルごとに、次の設定を構成できます。  

-   Windows ファイアウォールを有効または無効にする。  

-   許可されたプログラムの一覧にあるプログラムも含め、着信接続をブロックする。  

-   Windows ファイアウォールが新しいプログラムをブロックしたときにユーザーに通知する。  

> [!NOTE]  
>  Endpoint Protection は Windows ファイアウォールの管理のみをサポートします。  


 Endpoint Protection 用の Windows ファイアウォール ポリシーを作成および展開する方法の詳細については、「[System Center Configuration Manager の Endpoint Protection 用 Windows ファイアウォール ポリシーを作成および展開する方法](create-windows-firewall-policies.md)」をご覧ください。  


## <a name="windows-defender-advanced-threat-protection"></a>Windows Defender Advanced Threat Protection

Configuration Manager のバージョン 1606 (Current Branch) 以降、Endpoint Protection を使用して、Windows Defender Advanced Threat Protection (ATP) を管理および監視できるようになりました。 Windows Defender ATP は、企業が自社のネットワークに対する高度な攻撃を検出して調査し、対応するのに役立つ新しいサービスです。 「[Windows Defender Advanced Threat Protection](windows-defender-advanced-threat-protection.md)」をご覧ください。

## <a name="endpoint-protection-workflow"></a>Endpoint Protection のワークフロー  
 次の図を使用して、Endpoint Protection を Configuration Manager 階層に実装するワークフローの理解に役立ててください。  

 ![Endpoint Protection のワークフロー](../media/Endpoint-Protection-Workflow.gif)  

## <a name="endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Mac コンピューターと Linux サーバー用の Endpoint Protection クライアント  
 System Center Endpoint Protection には、Linux コンピューターと Mac コンピューター用の Endpoint Protection クライアントが付属しています。 Configuration Manager にはこれらのクライアントが付属していないため、[Microsoft ボリューム ライセンス サービス センター](https://www.microsoft.com/licensing/servicecenter/default.aspx)から次の製品をダウンロードする必要があります。  

-   System Center 2012 Endpoint Protection for the Mac  

-   System Center 2012 Endpoint Protection for Linux  


> [!IMPORTANT]  
>  Mac 用と Linux 用の Endpoint Protection インストール ファイルをダウンロードするには、Microsoft ボリューム ライセンスを購入する必要があります。  

 これらの製品は、Configuration Manager コンソールから管理することができません。 ただし、System Center Operations Manager 管理パックがインストール ファイルに付属しているため、Operations Manager を使用して Linux 用のクライアントを管理することができます。  

 Linux コンピューターと Mac コンピューター用の Endpoint Protection クライアントをインストールして管理する方法については、 **Documentation** フォルダーに配置されたこれらの製品に付属のマニュアルを参照してください。



<!--HONumber=Dec16_HO3-->


