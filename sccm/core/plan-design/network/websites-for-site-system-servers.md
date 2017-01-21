---
title: "サイト システムの Web サイト | System Center Configuration Manager"
description: "System Center Configuration Manager のサイト システム サーバーの既定およびカスタム Web サイトについて説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 681f0893-e83b-476e-9ec0-a5dc7c9deeb6
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 3f463aa804cb928b29fc26d9af8dede7f65222df


---
# <a name="websites-for-site-system-servers-in-system-center-configuration-manager"></a>System Center Configuration Manager のサイト システム サーバーの Web サイト

*適用対象: System Center Configuration Manager (Current Branch)*

いくつかの Configuration Manager のサイト システムの役割には、Microsoft インターネット インフォメーション サービス (IIS) を使用することが必要であり、そのような役割はサイト システム サービスをホストするために既定の IIS Web サイトを使用します。 同じサーバー上で他の Web アプリケーションを実行する必要があり、設定に Configuration Manager との互換性がない場合は、Configuration Manager のカスタム Web サイトの使用を検討します。  

> [!TIP]  
>  セキュリティのベスト プラクティスとして、IIS を必要とする Configuration Manager サイト システム専用のサーバーを設置してください。 Configuration Manager サイト システムで他のアプリケーションを実行すると、そのコンピューターが攻撃を受ける確率が高まります。  




##  <a name="a-namebkmkwhat2knowa-what-to-know-before-choosing-to-use-custom-websites"></a><a name="BKMK_What2Know"></a> カスタム Web サイトを使用する前に理解しておくこと  
 既定では、サイト システムの役割は、IIS の **既定の Web サイト** を使用します。 これは、サイト システムの役割のインストール時に自動的に構成されます。 ただし、プライマリ サイトでは、カスタム Web サイトを使用するように選択できます。 カスタム Web サイトを使用する場合。  

-   カスタム Web サイトは、個々のサイト システム サーバーまたは役割に対してではなく、サイト全体に対して有効になります。  

-   プライマリ サイトでは、適用可能なサイト システムの役割をホストする各コンピューターは、**SMSWEB** という名前のカスタム Web サイトで構成されている必要があります。 この Web サイトを作成し、そのコンピューター上のサイト システムの役割がカスタム Web サイトを使用するように構成されるまでの間、クライアントはそのコンピューターのサイト システムの役割と通信できない可能性があります。  

-   プライマリ親サイトがカスタム Web サイトを使用するよう構成されているときに、セカンダリ サイトは同じ目的で自動的に構成されるため、IIS を必要とする各セカンダリ サイト システム サーバー上の IIS にカスタム Web サイトを作成する必要もあります。  


  **カスタム Web サイトを使用するための前提条件:**  

 サイトでカスタム Web サイトを使用するオプションを有効にする前に、次の操作を実行する必要があります。  

-   IIS を必要とする各サイト システム サーバーの IIS で **SMSWEB** という名前のカスタム Web サイトを作成します。 プライマリ サイトおよびすべての子セカンダリ サイトでこれを行います。  

-   Configuration Manager クライアント通信用に構成したのと同じポート (クライアント要求ポート) に応答するよう、カスタム Web サイトを構成します。  

-   カスタム フォルダーを使用するカスタムまたは既定の Web サイトごとに、使用する既定のドキュメントの種類のコピーを、Web サイトをホストするルート フォルダーに配置します。 たとえば、既定の構成を使用している Windows Server 2008 R2 コンピューターでは、 **iisstart.htm** が使用可能な既定のドキュメントの種類のうちの 1 つです。 既定の Web サイトのルートでこのファイルを検索し、SMSWEB カスタム Web サイトをホストするルート フォルダーにこのファイル (または使用する既定のドキュメントの種類のコピー) のコピーを配置できます。 既定のドキュメントの種類の詳細については、IIS の「[Default Document &lt;defaultDocument\>](http://www.iis.net/configreference/system.webserver/defaultdocument)」 (「既定のドキュメント defaultDocument」) を参照してください。  

**IIS の要件について:**
**次のサイト システムの役割では、サイト システム サービスをホストするために IIS と Web サイトが必要です。**  

-   アプリケーション カタログ Web サービス ポイント  

-   アプリケーション カタログ Web サイト ポイント  

-   配布ポイント  

-   登録ポイント  

-   登録プロキシ ポイント  

-   フォールバック ステータス ポイント  

-   管理ポイント  

-   ソフトウェアの更新ポイント  

-   状態移行ポイント  

その他の考慮事項:  

-   プライマリ サイトでカスタム Web サイトを有効にすると、そのサイトに割り当てられたクライアントは、適用可能なサイト システム サーバー上の既定の Web サイトではなくカスタム Web サイトと通信するよう誘導されます。  

-   1 つのプライマリ サイトでカスタム Web サイトを使用する場合は、クライアントが階層内を問題なくローミングできるように、階層にあるすべてのプライマリ サイトでカスタム Web サイトを使用することをご検討ください。 (ローミングは、クライアント コンピューターが他のサイトで管理されている新しいネットワーク セグメントに移動したときに発生します。 ローミングにより、クライアントが WAN リンク経由ではなくローカルでアクセスできるリソースに影響が及ぶ場合があります)。  

-   IIS を使用するがクライアントからの接続を受け入れないサイト システムの役割 (レポート サービス ポイントなど) も、既定の Web サイトではなく "SMSWEB" Web サイトを使用します。  

-   カスタム Web サイトでは、コンピューターの既定の Web サイトで使用されるポート番号とは異なるポート番号を割り当てる必要があります。 既定の Web サイトとカスタム Web サイトで同じ TCP/IP ポートの使用を試みると、両方の Web サイトを同時に実行することはできません。  

-   カスタム Web サイトの IIS に構成する TCP/IP ポートは、サイト用のクライアント要求ポートと一致する必要があります。  

## <a name="switching-between-default-and-custom-websites"></a>既定の Web サイトとカスタム Web サイトの切り替え  
いつでも、プライマリ サイトでカスタム Web サイトを使用するためのチェック ボックス (サイトの [プロパティ] の [全般] タブにあるチェック ボックス) をオンまたはオフにすることができますが、慎重に計画してからこの変更を行います。 この構成が変更されると、プライマリ サイトと子セカンダリ サイトの適用可能なサイト システムの役割は、すべてアンインストールされてから再インストールされます。  

次の役割は、 **自動的に再インストール**されます。  

-   管理ポイント  

-   配布ポイント  

-   ソフトウェアの更新ポイント  

-   フォールバック ステータス ポイント  

-   状態移行ポイント  

次の役割は、 **手動で再インストール**する必要があります。  

-   アプリケーション カタログ Web サービス ポイント  

-   アプリケーション カタログ Web サイト ポイント  

-   登録ポイント  

-   登録プロキシ ポイント  

補足:  

-   既定の Web サイトの使用からカスタム Web サイトの使用に変更した場合、Configuration Manager により、以前の仮想ディレクトリが削除されることはありません。 Configuration Manager で使用されたファイルを削除したい場合は、既定の Web サイトの下に作成された仮想ディレクトリを手動で削除する必要があります。  

-   カスタム Web サイトを使用するようサイトを変更した場合は、そのサイトに既に割り当てられているクライアントは、カスタム Web サイトの新しいクライアント要求ポートを使用するよう再構成する必要があります。 「[System Center Configuration Manager でのクライアント通信ポートの構成方法](../../../core/clients/deploy/configure-client-communication-ports.md)」を参照してください。  

## <a name="configure-custom-websites"></a>カスタム Web サイトの構成  
オペレーティング システムのバージョンによってカスタム Web サイトを作成する手順が異なるため、正確な手順については、オペレーティング システムのバージョンのドキュメントをご覧ください。ただし、適用可能な場合は、次の情報を使用します。  

-   Web サイトの名前は **SMSWEB**である必要があります。  

-   HTTPS を構成する場合は、構成を保存する前に、SSL 証明書を指定する必要があります。  

-   カスタム Web サイトを作成した後は、使用するカスタム Web サイトのポートを IIS 内の他の Web サイトから削除します。  

    1.  他の Web サイトの **バインド** を編集し、 **SMSWEB** Web サイトに割り当てられているポートと一致するポートを削除します。  

    2.  **SMSWEB** Web サイトを起動します。  

    3.  そのサイトのサイト サーバーの **SMS_SITE_COMPONENT_MANAGER** サービスを再開します。  



<!--HONumber=Nov16_HO1-->


