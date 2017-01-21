---
title: "クライアント ピア キャッシュ | System Center Configuration Manager"
description: "System Center Configuration Manager でコンテンツを展開する場合は、クライアントのコンテンツ ソースの場所のピア キャッシュを使用します。"
ms.custom: na
ms.date: 1/3/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 86cd5382-8b41-45db-a4f0-16265ae22657
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: e2a72fd9fb9ae5e64b7eb92e1d2106162fc7ea5d
ms.openlocfilehash: 599ba03a1934b9feb030f27c827625c2c9471d8e

---
# <a name="peer-cache-for-configuration-manager-clients"></a>Configuration Manager クライアントのピア キャッシュ

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager バージョン 1610 以降、**ピア キャッシュ**を使用して、コンテンツをリモートの場所にあるクライアントに展開できます。 ピア キャッシュとは、クライアントがローカル キャッシュで他のクライアントとコンテンツを直接共有できるようにするための組み込みの Configuration Manager ソリューションです。   

> [!TIP]  
> バージョン 1610 では、ピア キャッシュとクライアント データ ソースのダッシュボードは、プレリリース機能です。 有効にするには、「[更新プログラムからのプレリリース機能の使用](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease)」をご覧ください。

 -  クライアント設定を使用してピア キャッシュを使用するクライアントを有効にできます。
 -  コンテンツを共有するには、両方のピア キャッシュ クライアントが、コンテンツをシークするクライアントの現在の境界グループのメンバーである必要があります。 クライアントがフォールバックを使用して近隣の境界グループからコンテンツをシークする場合は、近隣の境界グループのピア クライアントは使用可能なコンテンツ ソースの場所のプールに含まれません。 現在および近隣の境界グループの詳細については、「[境界グループ](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups##a-namebkmkboundarygroupsa-boundary-groups)」を参照してください。
 -  Configuration Manager クライアントのキャッシュに保持されているコンテンツのすべての種類は、ピア キャッシュを使用して他のクライアントに提供できます。
 -  ピア キャッシュは、BranchCache などのその他のソリューションの使用に取って代わるものではなく、それらのソリューションと並列動作し、配布ポイントなどの従来のコンテンツ展開ソリューションを拡張する追加のオプションを提供します。 これは、BranchCache に依存しないカスタム ソリューションであるため、Windows BranchCache を有効にしない、または使用しない場合でも機能します。

ピア キャッシュを有効にするクライアント設定をコレクションに展開すると、そのコレクションのメンバーは同じ境界グループ内の他のクライアントのピア コンテンツ ソースとして動作できます。
 -  ピア コンテンツ ソースとして動作するクライアントは、キャッシュされている利用可能なコンテンツの一覧を管理ポイントに送信します。
 -  次に、その境界グループ内の次のクライアントがそのコンテンツを要求すると、コンテンツのある各ピア キャッシュ ソースが、その境界グループ内の配布ポイントとその他のコンテンツ ソースの場所とともに潜在的なコンテンツ ソースとして返されます。
 -  通常の運用プロセスごとにコンテンツをシークするクライアントは、提供されたソースのプールからコンテンツ ソースを選択し、そのコンテンツの取得の試みを続行します。

> [!NOTE]
> コンテンツの近隣の境界グループへのフォールバックが発生した場合、近隣の境界グループからのピア キャッシュ コンテンツ ソースの場所は、クライアントの潜在的なコンテンツ ソースの場所のプールに追加されません。  

すべてのクライアントをピア キャッシュに参加させることができたとしても、ピア キャッシュ ソースに最も適しているクライアントのみを選択することをお勧めします。  クライアントのシャーシの種類、ディスク容量、ネットワーク接続などに基づくクライアントの適合性を評価できます。 ピア キャッシュで使用する最適なクライアントを選択するのに役立つ詳細については、[Microsoft のコンサルタントによる、このブログ](https://blogs.technet.microsoft.com/setprice/2016/06/29/pe-peer-cache-custom-reporting-examples/)を参照してください。

クライアントが正常にピア キャッシュの使用を把握しやすいように、クライアント データ ソース ダッシュボードを表示できます。 「[Client Data Sources dashboard](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard)」 (クライアント データ ソースのダッシュボード) を参照してください。


## <a name="requirements-and-considerations-for-peer-cache"></a>ピア キャッシュの要件と考慮事項
- 各クライアントのキャッシュ フォルダーに対する**フル コントロール**を持つ**ネットワーク アクセス アカウント**を使用してサイトを構成する必要があります。 既定で、これは ***%windir%\ccmcache*** です。

- クライアントは、現在の境界グループ内にあるピア キャッシュ クライアントのコンテンツのみを転送できます。

-   ピア キャッシュ コンテンツ ソースの現在の境界は、そのクライアントの最後のハードウェア インベントリ送信によって決定されるため、ネットワークの場所に移動し別の境界グループ内にあるクライアントは、ピア キャッシュを目的として、その以前の境界グループのメンバーであると見なされる場合があります。 これにより、クライアントが、直接のネットワークの場所にない、ピア キャッシュ コンテンツ ソースが提供されます。 この構成の傾向のあるクライアントをピア キャッシュ ソースとして参加させないようにすることをお勧めします。

## <a name="to-configure-client-peer-cache-client-settings"></a>クライアント ピア キャッシュのクライアント設定を構成するには
1.  Configuration Manager コンソールで **[管理]** > **[クライアント設定]** に移動し、使用するデバイス クライアント設定オブジェクトを開きます。 既定のクライアント設定オブジェクトを変更することもできます。
2.  使用可能な設定のリストから [**クライアント キャッシュ設定**] を選びます。
3.  **[完全な OS 上の Configuration Manager クライアントでコンテンツを共有できるようにする]** を **[はい]** に設定します。
4.  ピア キャッシュに使用するポートを定義するには、次の設定を構成します。  
  -  **初期ネットワーク ブロードキャスト用ポート**
  -  **クライアント ピア通信用に HTTPS を有効にする**
  -  **ピアからのコンテンツのダウンロード用ポート (HTTP/HTTPS)**

ピア キャッシュが有効になっている各コンピューターで Windows ファイアウォールを使用している場合、Configuration Manager はユーザーが構成したポートの使用を許可するようにします。



<!--HONumber=Jan17_HO1-->


