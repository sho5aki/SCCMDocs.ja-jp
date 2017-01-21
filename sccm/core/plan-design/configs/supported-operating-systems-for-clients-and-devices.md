---
title: "サポートされるクライアントとデバイス | System Center Configuration Manager"
description: "System Center Configuration Manager がクライアントとデバイスをサポートするオペレーティング システムについて説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87f4e041-67df-4c61-aa98-7444faffe565
caps.latest.revision: 5
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 862291f52d5a1bb34fb5483806972fcf70f158a8

---
# <a name="supported-operating-systems-for-clients-and-devices-for-system-center-configuration-manager"></a>System Center Configuration Manager のクライアントとデバイスのサポートされるオペレーティング システム

*適用対象: System Center Configuration Manager (Current Branch)*




 System Center Configuration Manager は、さまざまな Windows、Mac、Linux および UNIX コンピューター上のクライアント ソフトウェアのインストールをサポートします。  

 **すべてのクライアントの要件と制限事項:**  

-   Configuration Manager サービスについては、スタートアップの種類やログオン方法の設定の変更はサポートされていません。 そのようにすると、主要なサービスが正しく実行できなくなる可能性があります。    

-   root 以外のアカウント下のコンピューターでは、Linux または UNIX の Configuration Manager クライアントや Mac 用クライアントをインストールすることも実行することもサポートされません。 そのようにすると、主要なサービスが正しく実行できなくなる可能性があります。  

##  <a name="a-namebkmkwinclientosa-windows-computers"></a><a name="bkmk_WinClientos"></a> Windows コンピューター  
 Configuration Manager に付属の Configuration Manager クライアントを持つ Windows コンピューターを管理することができます。 詳細については、「[How to deploy clients to Windows computers in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-windows-computers.md)」 (System Center Configuration Manager でクライアントを Windows コンピューターに展開する方法) を参照してください。  

**サポートされるオペレーティング システム:**  

-  **Windows Server 2016**  – Standard、Datacenter <sup>1</sup>
  - Windows Server 2016 は、Configuration Manager バージョン 1606 以降および KB3186654 以降の修正プログラム ロールアップ (2016 年 10 月にリリースされた 1606 のベースライン バージョン) でサポートされています。  


-   **Windows Server 2012 R2** (x64) – Standard、Datacenter <sup>1</sup>    

-   **Windows Storage Server 2012 R2** (x64)    

-   **Windows Server 2012** (x64) – Standard、Datacenter <sup>1</sup>    

-   **Windows Storage Server 2012** (x64)    

-   **Windows Server 2008 R2 SP1** (x64) – Standard、Enterprise、Datacenter <sup>1</sup>    

-   **Windows Storage Server 2008 R2** (x86、x64) - Workgroup、Standard、Enterprise    

-   **Windows  Server 2008 SP2** (x86、x64) - Standard、Enterprise、Datacenter <sup>1</sup>    

-   **Windows 10 Enterprise LTSB** (x86、x64) <sup>3</sup>    

-   **Windows 10** (x86、x64) – Pro、Enterprise    

-   **Windows 8.1** (x86、x64) – Professional、Enterprise    

-   **Windows 8** (x86、x64) – Professional、Enterprise    

-   **Windows 7 SP1** (x86、x64) – Professional、Enterprise、Ultimate    

-   **Windows Server 2012 R2 の Server Core のインストールR2** (x64) <sup>2</sup>    

-   **Windows Server 2012 の Server Core のインストール** (x64) <sup>2</sup>    

-   **Windows Server 2008 R2 の Server Core のインストール**  
    **(サービス パックなし、または SP1)** (x64)    

-   **Windows Server 2008 SP2 の Server Core のインストール** (x86、x64)  

 <sup>1</sup> Datacenter リリースは、Configuration Manager でサポートされますが動作は保障されません。 Windows Server Datacenter エディションに固有の問題に対しては、修正プログラムのサポートは提供されません。  

 <sup>2</sup> クライアント プッシュ インストールをサポートするには、このオペレーティング システムのバージョンを実行するコンピューターで、ファイルおよびストレージ サービスのサーバーの役割のための、ファイル サーバーの役割サービスを実行する必要があります。 Server Core コンピューターに Windows の機能をインストールする詳細については、Windows Server 2012 TechNet ライブラリの「[Server Core サーバーへのサーバーの役割と機能のインストール](http://go.microsoft.com/fwlink/p/?LinkId=299359)」を参照してください。  

 <sup>3</sup> このオペレーティング システムを使用するには、1602 以降のバージョンが必要です。  

##  <a name="a-namebkmkembeddedosa-windows-embedded"></a><a name="bkmk_EmbeddedOS"></a> Windows Embedded  
 Windows Embedded デバイスを管理するには、デバイス上に Configuration Manager クライアント ソフトウェアをインストールします。  書き込みフィルターについて詳しくは「[Planning for client deployment to Windows Embedded devices in System Center Configuration Manager](../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md)」 (System Center Configuration Manager での Windows Embedded デバイスへのクライアント展開の計画) を参照してください。  

**要件と制限事項**  

-   すべてのクライアント機能は、書き込みフィルターが有効化されていないサポート対象の Windows Embedded システムでサポートされます。  

-   次のいずれかを使用するクライアントは、電源管理が必要なすべての機能でサポートされます。  

    -   Enhanced Write Filter (EWF)    

    -   RAM ファイル ベースの書き込みフィルター (FBWF)    

    -   Unified Write Filter (UWF)  

-   アプリケーション カタログは、どのような Windows Embedded デバイスについてもサポートされません。  

-   Windows XP ベースの Windows Embedded デバイスで検出したマルウェアを監視するには、Embedded デバイスに Microsoft Windows WMI スクリプト パッケージを先にインストールしておく必要があります。 このパッケージは、Windows Embedded Target Designer を使用してインストールします。 検出したマルウェアが確実に報告されるようにするには、Embedded デバイスにファイル **WBEMDISP.DLL** および **WBEMDISP.TLB** が存在している必要があり、フォルダー **%windir%\System32\WBEM** に登録されている必要があります。  

**サポートされるオペレーティング システム:**  

-   **Windows 10 Enterprise** (x86、x64)  

-   **Windows 10 IoT Enterprise** (x86、x64)  

-   **Windows Embedded 8.1 Industry** (x86、x64)    

-   **Windows Embedded 8 Industry** (x86、x64)    

-   **Windows Embedded 8 Standard** (x86、x64)    

-   **Windows Embedded 8 Pro** (x86、x64)    

-   **Windows Thin PC** (x86、x64)    

-   **Windows Embedded POSReady 7** (x86、x64)    

-   **Windows Embedded Standard 7 SP1** (x86、x64)    

-   **WEPOS 1.1 SP3** (x86)    

-   **Windows Embedded POSReady 2009** (x86)    

-   **Windows Fundamentals for Legacy PCs (WinFLP)** (x86)    

-   **Windows XP Embedded SP3** (x86)    

-   **Windows Embedded Standard 2009** (x86)  

## <a name="windows-ce"></a>Windows CE  
 Configuration Manager に付属の Configuration Manager モバイル デバイス レガシ クライアントを持つ Windows CE デバイスを管理することができます。  

**要件と制限事項**  

-   モバイル デバイス クライアントには、0.78 MB またはクライアントをインストールする記憶領域が必要です。 モバイル デバイス上のログ記録に、最大 256 KB の追加の記憶領域が必要な場合があります。    

-   これらのモバイル デバイスの機能は、プラットフォームとクライアントの種類によって異なります。 モバイル デバイス レガシ クライアントで Configuration Manager がサポートする管理機能の詳細については、「[Choose a device management solution for System Center Configuration Manager](../../../core/plan-design/choose-a-device-management-solution.md)」 (System Center Configuration Manager のデバイス管理ソリューションの選択) を参照してください。  

**サポートされるオペレーティング システム:**  

-   Windows CE 7.0 (ARM および x86 プロセッサ)  

**サポートされる言語:**  

-   中国語 (簡体字、繁体字)    

-   英語 (米国)    

-   フランス語 (フランス)    

-   ドイツ語    

-   イタリア語    

-   日本語  

-   韓国語  

-   ポルトガル語 (ブラジル)  

-   ロシア語  

-   スペイン語 (スペイン)  

## <a name="mac-computers"></a>Mac コンピューター  
 Mac OS X コンピューターを Mac 向けの Configuration Manager クライアントとともに管理できます。  

 Configuration Manager メディアでは、Mac クライアント インストール パッケージは提供されません。 これは、[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=525184)から、追加のオペレーティング システム用のクライアントのダウンロードの一環としてダウンロードできます。  

**要件と制限事項**  

 Mac 用 Configuration Manager クライアント (バージョン 5.0.8333.1 以降) を個別にダウンロードして使用する必要があります。 Windows クライアントとは異なり、Mac クライアントは、Configuration Manager ソフトウェアをインストールするときに含まれていません。 Mac クライアントをダウンロードするには、「[Microsoft System Center Configuration Manager - Clients for Additional Operating Systems (Microsoft System Center Configuration Manager - 追加のオペレーティング システム用のクライアント)](http://go.microsoft.com/fwlink/?LinkID=525184)」に移動します。  

 詳細については、「[How to deploy clients to Macs in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-macs.md)」 (System Center Configuration Manager でクライアントを Mac に展開する方法) を参照してください。  

**サポートされるバージョン:**  

-   **Mac OS X 10.9** (Mavericks)  

-   **Mac OS X 10.10** (Yosemite)  

-   **Mac OS X 10.11** (El Capitan)  

##  <a name="a-namebkmklinuxosa-linux-and-unix-servers"></a><a name="bkmk_LinuxOS"></a> Linux および UNIX サーバー  
 Linux および UNIX サーバーを Linux および UNIX 用の Configuration Manager クライアントとともに管理できます。  

 Configuration Manager メディアでは、Linux および UNIX クライアント インストール パッケージは提供されません。 これらは、[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=525184)から、追加のオペレーティング システム用のクライアントのダウンロードの一環としてダウンロードできます。 クライアント インストール パッケージに加え、クライアント ダウンロードには、各コンピューター上でクライアントのインストールを管理する install スクリプトも含まれています。  

**要件と制限事項**  

-   Linux および UNIX 向けクライアントのオペレーティング システム ファイルの依存関係を確認するには、[Prerequisites for Client Deployment to Linux and UNIX Servers](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md#BKMK_ClientDeployPrereqforLnU) (Linux および UNIX サーバーへのクライアントの展開の前提条件) を参照してください。  

-   Linux または UNIX を実行するコンピューターでサポートされている管理機能の概要については、「[How to deploy clients to UNIX and Linux servers in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md)」 (System Center Configuration Manager で UNIX および Linux サーバーにクライアントを展開する方法) を参照してください。  

-   Linux および UNIX のサポートされるバージョンの場合、一覧に示したバージョンには後続のマイナー バージョンがすべて含まれます。 たとえば、CentOS バージョン 6 のサポートが示されている場合は、CentOS 6 の後続のマイナー バージョン (CentOS 6.3 など) もすべて含まれます。 同様に、サービス パックを使用するオペレーティング システム (SUSE Linux Enterprise Server 11 SP1 など) のサポートが示されている場合は、そのオペレーティング システムのバージョンの後続のサービス パックもサポートに含まれます。  

-   Linux と UNIX でクライアントをインストールする方法については、「[System Center Configuration Manager で UNIX および Linux サーバーにクライアントを展開する方法](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md)」を参照してください。  

**サポートされているバージョン:** 次のバージョンは、指定された .tar ファイルを使用してサポートされます。  

### <a name="aix"></a>AIX  

|||  
|-|-|  
|バージョン 5.3 (Power)|ccm-Aix53ppc.&lt;ビルド\>.tar|  
|バージョン 6.1 (Power)|ccm-Aix61ppc.&lt;ビルド\>.tar|  
|バージョン 7.1 (Power)|ccm-Aix71ppc.&lt;ビルド\>.tar|  

### <a name="centos"></a>CentOS  

|||  
|-|-|  
|バージョン 5 x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 5 x64|ccm-Universalx64.&lt;ビルド\>.tar|  
|バージョン 6 x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 6 x64|ccm-Universalx64.&lt;ビルド\>.tar|  
|バージョン 7 x64|ccm-Universalx64.&lt;ビルド\>.tar|  

### <a name="debian"></a>Debian  

|||  
|-|-|  
|バージョン 5 x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 5 x64|ccm-Universalx64.&lt;ビルド\>.tar|  
|バージョン 6 x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 6 x64|ccm-Universalx64.&lt;ビルド\>.tar|  
|バージョン 7 x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 7 x64|ccm-Universalx64.&lt;ビルド\>.tar|  
|バージョン 8 x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 8 x64|ccm-Universalx64.&lt;ビルド\>.tar|  

### <a name="hp-ux"></a>HP-UX  

|||  
|-|-|  
|バージョン 11iv2 IA64|ccm-HpuxB.11.23i64.&lt;ビルド\>.tar|  
|バージョン 11iv2 PA-RISC|ccm-HpuxB.11.23PA.&lt;ビルド\>.tar|  
|バージョン 11iv3 IA64|ccm-HpuxB.11.31i64.&lt;ビルド\>.tar|  
|バージョン 11iv3 PA-RISC|ccm-HpuxB.11.31PA.&lt;ビルド\>.tar|  

### <a name="oracle-linux"></a>Oracle Linux  

|||  
|-|-|  
|バージョン 5 x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 5 x64|ccm-Universalx64.&lt;ビルド\>.tar|  
|バージョン 6 x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 6 x64|ccm-Universalx64.&lt;ビルド\>.tar|  
|バージョン 7 x64|ccm-Universalx64.&lt;ビルド\>.tar|  

### <a name="red-hat-enterprise-linux-rhel"></a>Red Hat Enterprise Linux (RHEL)  

|||  
|-|-|  
|バージョン 4 x86|ccm-RHEL4x86.&lt;ビルド\>.tar|  
|バージョン 4 x64|ccm-RHEL4x64.&lt;ビルド\>.tar|  
|バージョン 5 x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 5 x64|ccm-Universalx64.&lt;ビルド\>.tar|  
|バージョン 6 x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 6 x64|ccm-Universalx64.&lt;ビルド\>.tar|  
|バージョン 7 x64|ccm-Universalx64.&lt;ビルド\>.tar|  

### <a name="solaris"></a>Solaris  

|||  
|-|-|  
|バージョン 9 SPARC|ccm-Sol9sparc.&lt;ビルド\>.tar|  
|バージョン 10 x86|ccm-Sol10x86.&lt;ビルド\>.tar|  
|バージョン 10 SPARC|ccm-Sol10sparc.&lt;ビルド\>.tar|  
|バージョン 11 x86|ccm-Sol11x86.&lt;ビルド\>.tar|  
|バージョン 11 SPARC|ccm-Sol11sparc.&lt;ビルド\>.tar|  

### <a name="suse-linux-enterprise-server-sles"></a>SUSE Linux Enterprise Server (SLES)  

|||  
|-|-|  
|バージョン 9 x86|ccm-SLES9x86.&lt;ビルド\>.tar|  
|バージョン 10 SP1 x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 10 SP1 x64|ccm-Universalx64.&lt;ビルド\>.tar|  
|バージョン 11 SP1 x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 11 SP1 x64|ccm-Universalx64.&lt;ビルド\>.tar|  
|バージョン 12 x64|ccm-Universalx64.&lt;ビルド\>.tar|  

### <a name="ubuntu"></a>Ubuntu  

|||  
|-|-|  
|バージョン 10.04 LTS x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 10.04 LTS x64|ccm-Universalx64.&lt;ビルド\>.tar|  
|バージョン 12.04 LTS x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 12.04 LTS x64|ccm-Universalx64.&lt;ビルド\>.tar|  
|バージョン 14.04 LTS x86|ccm-Universalx86.&lt;ビルド\>.tar|  
|バージョン 14.04 LTS x64|ccm-Universalx64.&lt;ビルド\>.tar|  

##  <a name="a-namebkmkintuneosa-mobile-devices-enrolled-by-microsoft-intune"></a><a name="bkmk_IntuneOS"></a> Microsoft Intune で登録されるモバイル デバイス  
 Microsoft Intune を Configuration Manager と統合する場合に管理できるコンピューターとデバイスの詳細については、Microsoft Intune ドキュメント ライブラリの次の 2 つのトピックを参照してください。  

-   [Microsoft Intune のモバイル デバイス管理機能](https://docs.microsoft.com/intune/get-started/choose-how-to-manage-devices)  
-   [Microsoft Intune の Windows PC 管理機能](https://docs.microsoft.com/intune/get-started/windows-pc-management-capabilities-in-microsoft-intune)  

##  <a name="a-namebkmkonpremosa-on-premises-mobile-device-management"></a><a name="bkmk_OnpremOS"></a> オンプレミス モバイル デバイス管理  
 Configuration Manager には、クライアント ソフトウェアをインストールすることがないオンプレミスであるデバイスを管理する組み込みの機能があります。  詳細については、「[Manage mobile devices with on-premises infrastructure in System Center Configuration Manager](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md)」 (System Center Configuration Manager のオンプレミス インフラストラクチャとともにモバイル デバイスを管理する) を参照してください。  

 **要件と制限事項**  

-   階層の最上位層で、 **サービス接続ポイント**を構成する必要があります。  

 **サポートされるオペレーティング システム:**  

-   **Windows 10 Pro** (x86、x64)  

-   **Windows 10 Pro Enterprise** (x86、x64)  

-   **Windows 10 IoT Enterprise** (x86、x64)

-   **Windows 10 Mobile**  

-   **Windows 10 Mobile Enterprise**  

-  **Windows 10 IoT Mobile Enterprise**

##  <a name="a-namebkmkexsrvconosa-exchange-server-connector"></a><a name="bkmk_ExSrvConOS"></a> Exchange Server コネクタ  
 Configuration Manager は、クライアント ソフトウェアをインストールすることがない、Exchange サーバーに接続するデバイスの限定された管理をサポートしています。  詳細については、「[System Center Configuration Manager と Exchange によるモバイル デバイスの管理](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)」を参照してください。  

 **要件と制限事項**  

-   Configuration Manager は、Exchange Server または Exchange Online を実行しているサーバーに接続する Exchange Active Sync (EAS) 対応デバイス向けに Exchange Server コネクタを使用する場合に、モバイル デバイスの限定された管理を提供します。  

-   Exchange Server コネクタで管理するモバイル デバイスに対して、Configuration Manager がサポートする管理機能の詳細については、「Configuration Manager でのモバイル デバイスの管理方法を決定する」を参照してください。  

**サポートされている Exchange Server のバージョン:**  

-   **Exchange Server 2010 SP1**  

-   **Exchange Server 2010 SP2**  

-   **Exchange Server 2013**  

-   **Exchange Online (Office 365)** - これは、Business Productivity Online Standard Suite を含みます。  



<!--HONumber=Nov16_HO1-->


