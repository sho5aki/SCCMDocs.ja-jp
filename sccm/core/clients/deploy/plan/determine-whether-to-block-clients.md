---
title: "クライアントのブロック | System Center Configuration Manager"
description: "System Center Configuration Manager を使用してクライアントのアクセスをブロックし、システムのセキュリティを確保します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 54ef5fbb-521d-4ca5-a1c5-61e6f538d71e
caps.latest.revision: 8
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: bbb541d62c0d8f6d7deb602aaf962e81d4e2b13a


---
# <a name="determine-whether-to-block-clients-in-system-center-configuration-manager"></a>System Center Configuration Manager でクライアントをブロックするかどうかの判断

*適用対象: System Center Configuration Manager (Current Branch)*

クライアント コンピューターまたはクライアント モバイル デバイスが信頼できなくなった場合は、System Center 2012 Configuration Manager コンソールでクライアントをブロックできます。 ブロックされたクライアントは、Configuration Manager インフラストラクチャによって拒否されるため、サイト システムと通信してポリシーをダウンロードしたり、インベントリ データをアップロードしたり、状態またはステータス メッセージを送信したりすることはできなくなります。  

 クライアントのブロックとブロック解除は、セカンダリ サイトや中央管理サイトではなく、そのクライアントが割り当てられているサイトから行う必要があります。  

> [!IMPORTANT]  
>  Configuration Manager でブロックすることにより Configuration Manager サイトをセキュリティで保護することができますが、新しい自己署名入り証明書およびハードウェア ID を使用すると、ブロックされたクライアントがサイトに再参加できるため、HTTP を使ってクライアントがサイト システムと通信することを許可する場合は、信頼されていないコンピューターやモバイル デバイスからサイトを保護するのに、この機能に依存しないでください。 そうではなく、サイト システムが HTTPS クライアント接続を受け入れる場合は、オペレーティング システムの展開時に使用したあと紛失したブート メディア、または危険のあるブート メディアをブロックするのに、このブロック機能を使用します。  

 ISV プロキシ証明書を使用してサイトにアクセスするクライアントをブロックすることはできません。 ISV プロキシ証明書の詳細については、System Center Configuration Manager Software Development Kit (SDK) を参照してください。  

 サイト システムが HTTPS クライアント接続に対応しており、公開キー インフラストラクチャで証明書失効リスト (CRL) がサポートされている場合、危険の可能性のある証明書に対しては、証明書失効が第 1 の防御ラインとなることを常に考慮してください。 Configuration Manager でクライアントをブロックすることは、階層を保護するための第 2 の防御ラインとなります。  

##  <a name="a-namebkmkblockvscrla-considerations-for-blocking-clients"></a><a name="BKMK_Block_vs_CRL"></a> クライアントのブロックに関する考慮事項  

-   このオプションは、HTTP および HTTPS クライアント接続で使用できますが、クライアントが HTTP でサイトシステムに接続するときは、セキュリティが制限されます。  

-   Configuration Manager の管理ユーザーにはクライアントをブロックする権限があります。この操作には Configuration Manager コンソールを使用します。  

-   クライアントの通信は、Configuration Manager 階層でのみ拒否されます。  

    > [!NOTE]  
    >  同じクライアントは、別の Configuration Manager 階層に登録できます。  

-   クライアントはすぐに Configuration Manager サイトからブロックされます。  

-   危険性のあるコンピューターおよびモバイル デバイスからサイト システムを保護できます。  

## <a name="considerations-for-using-certificate-revocation"></a>証明書の失効を使用するときの考慮事項  

-   公開キー インフラストラクチャが証明書失効リスト (CRL) をサポートする場合は、このオプションを HTTPS Windows クライアント接続に適用できます。  

     Mac クライアントは CRL チェックを常に実行するため、この機能を無効にすることはできません。  

     モバイル デバイス クライアントはサイト システムの証明書を確認するのに証明書失効リストを使用しませんが、証明書は、Configuration Manager によって失効させたり、確認したりすることができます。  

-   公開キー インフラストラクチャ管理者には、証明書を失効させる権限があり、この操作は Configuration Manager コンソール以外で実行されます。  

-   クライアントの通信は、このクライアント証明書が必要な任意のコンピューターまたはモバイル デバイスから拒否できます。  

-   証明書が失効してから、サイト システムが更新後の証明書失効リスト (CRL) をダウンロードするまでの間に遅延が発生しやすくなります。  

-   多くの PKI 展開を行う場合、この遅延は 1 日またはそれ以上になる可能性があります。 たとえば、Active Directory 証明書サービスでは、既定の有効期間は完全な CRL で 1 週間、差分の CRL で 1 日です。  

-   危険性のあるコンピューターおよびモバイル デバイスからサイト システムとクライアントを保護できます。  

    > [!NOTE]  
    >  IIS の証明書信頼リスト (CTL) を構成すると、IIS を実行するサイト システムを、未知のクライアントから一層保護できます。  



<!--HONumber=Nov16_HO1-->


