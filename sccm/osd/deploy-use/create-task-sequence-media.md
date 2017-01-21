---
title: "System Center Configuration Manager を使用したタスク シーケンス メディアの作成"
description: "Configuration Manager 環境内で対象コンピューターにオペレーティング システムを展開するため、CD などのタスク シーケンス メディアを作成します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 90498b4b-6a9b-43cd-b465-1d6c9a52df1c
caps.latest.revision: 8
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: f00defcdb56e37476ac24d8ce25d1dc5fb2f3260


---
# <a name="create-task-sequence-media-with-system-center-configuration-manager"></a>System Center Configuration Manager を使用したタスク シーケンス メディアの作成

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager 環境の参照コンピューターのオペレーティング システム イメージをキャプチャする、または対象となるコンピューターにオペレーティングシステムを展開するのに、メディアを使用することができます。 作成できるのは、CD、DVD セット、または USB フラッシュ ドライブです。  

 メディアはほとんどの場合、オペレーティング システムを展開するコンピューターがネットワークに未接続、または Configuration Manager サイトへ低帯域幅で接続しているときに使用されます。 しかし、展開メディアは、既存の Windows オペレーティング システムの外でオペレーティング システム 展開を行うときにも使用できます。 展開メディアのこうした二次的な使用方法は、展開先のコンピューターにオペレーティング システムがインストールされていないとき、オペレーティング システムが運用不可能な状態のとき、または管理者が展開先のコンピューターのハードディスクのパーティションを再作成するときなどに重要となります。  

 展開メディアには、起動可能なメディア、スタンドアロン メディア、事前設定されたメディアの 3 種類があります。 展開メディアの内容は使用しているメディアの種類によって異なります。 たとえば、スタンドアロン メディアには、オペレーティング システムを展開するタスク シーケンスが含まれている一方で、他の種類のメディアは、管理ポイントからタスク シーケンスを取得します。  

> [!IMPORTANT]  
>  タスク シーケンス メディアを作成するには、Configuration Manager コンソールを実行するコンピューターの管理者である必要があります。 管理者でない場合は、タスク シーケンス メディアの作成ウィザードを起動するときに管理者の資格情報が求められます。  

##  <a name="a-namebkmkplancapturemediaa-capture-media-for-operating-system-images"></a><a name="BKMK_PlanCaptureMedia"></a> オペレーティング システム イメージ用キャプチャ メディア  
 キャプチャ メディアにより、オペレーティング システム イメージを参照コンピューターからキャプチャすることが可能です。 キャプチャ メディアには、参照コンピューターを起動するブート イメージとオペレーティング システム イメージをキャプチャするタスク シーケンスが含まれています。 キャプチャ メディアの作成方法の詳細については、「[System Center Configuration Manager を使用したキャプチャ メディアの作成](create-capture-media.md)」を参照してください。  

##  <a name="a-namebkmkplanbootablemediaa-bootable-media-operating-system-deployments"></a><a name="BKMK_PlanBootableMedia"></a> 起動可能なメディアによるオペレーティング システムの展開  
 起動可能なメディアには、ブート イメージ、オプションとして[起動前コマンド](../understand/prestart-commands-for-task-sequence-media.md)とそれに必要なファイル、さらに Configuration Manager バイナリのみが含まれています。 展開先のコンピューターが立ち上がると、ネットワークに接続し、タスクシーケンス、オペレーティング システム イメージ、およびその他の要求されたコンテンツをネットワークから取得します。 タスク シーケンスはメディアにはないため、タスク シーケンスやコンテンツを更新しても、メディアを再作成する必要はありません。  

> [!IMPORTANT]  
>  起動可能なメディアのパッケージは暗号化されていません。 管理者ユーザーは、メディアにパスワードを設定するなど、適切なセキュリティ手段を講じ、パッケージのコンテンツを承認されていないユーザーから守る必要があります。  

 起動可能なメディアを作成する方法の詳細については、「[起動可能なメディアの作成](create-bootable-media.md)」を参照してください。  

##  <a name="a-namebkmkplanprestagedmediaa-prestaged-media-operating-system-deployments"></a><a name="BKMK_PlanPrestagedMedia"></a> 事前設定されたメディアによるオペレーティング システムの展開  
 事前設定されたメディアを使用すると、プロビジョニング プロセスの前に、ハード ディスクに起動可能なメディアとオペレーティング システム イメージを事前に設定することができます。 事前設定されたファイルは、Windows Imaging Format (WIM) と呼ばれる形式のファイルであり、製造元によるベア メタル コンピューター、または Configuration Manager 環境に接続していない企業の準備センターにインストールすることができます。  

 事前設定されたメディアには展開先のコンピューターを起動するのに使用するブート イメージと、展開先のコンピューターに適用されるオペレーティング システム イメージを含んでいます。 また、事前設定されたメディアの一部として含める、アプリケーション、パッケージ、およびドライバー パッケージを指定できます。 オペレーティング システムを展開するタスク シーケンスはメディアに含まれていません。 事前設定されたメディアを使用するタスク シーケンスを展開すると、クライアントによって、まずローカルのタスク シーケンス キャッシュ内に有効なコンテンツがあることが確認され、コンテンツが見つからない場合、またはコンテンツが改訂された場合は、配布ポイントからコンテンツがダウンロードされます。  

 事前設定されたメディアは、コンピューターがエンドユーザーに渡る前に、新しいコンピューターのハード ドライブに適用されます。 事前設定されたメディアを適用して初めてコンピューターを起動すると、コンピューターは Windows PE を起動し、オペレーティング システム展開プロセスを完了するタスク シーケンスが置かれている管理ポイントに接続します。  

> [!IMPORTANT]  
>  事前設定されたメディアのパッケージは暗号化されていません。 管理者ユーザーは、メディアにパスワードを設定するなど、適切なセキュリティ手段を講じ、パッケージのコンテンツを承認されていないユーザーから守る必要があります。  

 事前設定されたメディアを作成する方法については、「[事前設定されたメディアの作成](create-prestaged-media.md)」を参照してください。  

##  <a name="a-namebkmkplanstandalonemediaa-stand-alone-media-operating-system-deployments"></a><a name="BKMK_PlanStandaloneMedia"></a> スタンドアロン メディアによるオペレーティング システムの展開  
 スタンドアロン メディアには、オペレーティング システムを展開するのに必要なすべてが含まれています。 タスク シーケンスやその他の要求されているコンテンツも含まれています。 オペレーティング システムを展開するのに必要なすべてをスタンドアロン メディアに保存するため、スタンドアロン メディアのディスク容量は、他の種類のメディアで必要とされる容量よりもずっと大きなものである必要があります。  

 スタンドアロン メディアを作成する方法については、「[スタンドアロン メディアの作成](create-stand-alone-media.md)」を参照してください。  

## <a name="media-considerations-when-using-site-systems-configured-for-https"></a>HTTPS 用に構成したサイト システムを使用する場合のメディアに関する考慮事項  
 HTTPS 通信を使用するように管理ポイントと配布ポイントを構成する場合、中央管理サイトではなく、プライマリ サイトでブート メディアと事前設定されたメディアを作成する必要があります。 また、動的メディアとサイトベースのメディアのどちらを構成するかを判断する際は、次の点を考慮してください。  

-   動的メディアとしてメディアを構成するには、すべてのプライマリ サイトに、メディアを作成したサイトのルート CA が必要です。 ルート CA は階層内のすべてのプライマリ サイトにインポートできます。  

-   Configuration Manager 階層内のプライマリ サイトが複数のルート CA を使用する場合、各サイトでサイトベースのメディアを使用する必要があります。  



<!--HONumber=Nov16_HO1-->


