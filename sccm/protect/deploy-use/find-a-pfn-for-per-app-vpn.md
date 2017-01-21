---
title: "アプリごとの VPN のパッケージ ファミリ名 (PFN) の検索 | System Center Configuration Manager"
description: "アプリごとの VPN を構成できるようにするためにパッケージ ファミリ名を検索する 2 つの方法について説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47118499-3d26-4c25-bfde-b129de7eaa59
caps.latest.revision: 3
author: Nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: bad09d52a962ea5dccf55e4e2e485a17d934055a

---
# <a name="find-a-package-family-name-pfn-for-per-app-vpn"></a>アプリごとの VPN のパッケージ ファミリ名 (PFN) の検索

*適用対象: System Center Configuration Manager (Current Branch)*


アプリごとの VPN を構成できるようにするために PFN を検索する 2 つの方法があります。

## <a name="find-a-pfn-for-an-app-thats-installed-on-a-windows-10-computer"></a>Windows 10 コンピューターにインストールされているアプリの PFN の検索

作業しているアプリが既に Windows 10 コンピューターにインストールされている場合は、[Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) PowerShell コマンドレットを使用して PFN を取得できます。

Get-AppxPackage の構文は次のとおりです。

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
> PFN を取得するために管理者として PowerShell を実行することが必要になる場合があります。

たとえば、コンピューターにインストールされているすべてのユニバーサル アプリの情報を取得するには、`Get-AppxPackage` を使用します。

情報を取得するアプリの名前、または名前の一部がわかっている場合は、`Get-AppxPackage *<app_name>` を使用します。 ワイルドカード文字を使用することもできます。これはアプリの完全な名前がわからない場合に便利です。 OneNote の情報を取得する例では、`Get-AppxPackage *OneNote` を使用します。


OneNote について取得された情報を次に示します。

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## <a name="find-a-pfn-if-the-app-is-not-installed-on-a-computer"></a>アプリがコンピューターにインストールされていない場合の PFN の検索

1.  https://www.microsoft.com/en-us/store/apps にアクセスします。
2.  検索バーで、アプリの名前を入力します。 この例では、OneNote を検索します。
3.  アプリへのリンクをクリックします。 アクセスする URL の末尾には一連の文字が含まれていることに注意してください。 この例では、URL は次のようになります: `https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`
4.  別のタブに、次の URL を貼り付けます: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`。ここで、`<app id>` を、https://www.microsoft.com/en-us/store/apps から取得したアプリ ID (手順 3 の URL の末尾に含まれる一連の文字) で置き換えます。 ここでの OneNote の例では、次の URL を貼り付けます: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`

Edge では、必要な情報が表示されます。Internet Explorer では、**[開く]** をクリックすると情報が表示されます。 PFN 値は 1 行目に記述されています。 この例での結果を次に示します。


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`



<!--HONumber=Nov16_HO1-->


