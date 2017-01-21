---
title: "証明書プロファイルのセキュリティとプライバシー | System Center Configuration Manager"
description: "System Center Configuration Manager でユーザーとデバイスの証明書プロファイルを管理する場合のセキュリティのベスト プラクティスについて説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3393db41-900a-44c5-b950-2d46a35a198c
caps.latest.revision: 7
caps.handback.revision: 0
author: Nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 06ab159203e3ee2d3b6da726bc7264445dd41488


---
# <a name="security-and-privacy-for-certificate-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager の証明書プロファイルのセキュリティとプライバシー

*適用対象: System Center Configuration Manager (Current Branch)*

このトピックには、System Center Configuration Manager の証明書プロファイルのセキュリティとプライバシーの情報が含まれています。  

##  <a name="a-namebkmksecurityremoteconnectionsa-security-best-practices-for-certificate-profiles"></a><a name="BKMK_Security_RemoteConnections"></a> 証明書プロファイルのセキュリティ ベスト プラクティス  
 ユーザーとデバイスの証明書プロファイルを管理する場合は、次のセキュリティ ベスト プラクティスを使用してください。  

|セキュリティのベスト プラクティス|説明|  
|----------------------------|----------------------|  
|ネットワーク デバイス登録サービスのセキュリティのベスト プラクティスに従います。たとえば、インターネット インフォメーション サービス (IIS) のネットワーク デバイス登録サービスの Web サイトが必ず SSL 接続されるように設定し、クライアント証明書を無視するように構成します。|TechNet の Active Directory 証明書サービスの「 [Network Device Enrollment Service Guidance (ネットワーク デバイス登録サービス ガイド)](http://go.microsoft.com/fwlink/p/?LinkId=309016) 」を参照してください。|  
|SCEP 証明書プロファイルを構成するときに、デバイスとインフラストラクチャがサポートできる最も安全なオプションを選択します。|デバイスとインフラストラクチャに推奨されるセキュリティ ベスト プラクティスを特定し、実装し、従います。|  
|プライマリ デバイスの指定をユーザーに許可せずに、手動でユーザーとデバイスのアフィニティを指定します。 また、使用状況に基づいた構成を有効にしないでください。|SCEP 証明書プロファイルで [ユーザーのプライマリ デバイスでのみ証明書登録を許可する **** ] オプションを選択するときは、必ず正規のユーザーやデバイスから情報が収集されることになると考えないでください。 このオプションを指定して SCEP 証明書プロファイルを展開し、信頼されている管理ユーザーがデバイスのアフィニティを指定しなかった場合は、権限のないユーザーに特権が付与され、その認証用の証明書が登録される可能性があります。<br /><br /> **注:** 使用状況に基づいた構成を有効にすると、使用状況に関する情報が、System Center Configuration Manager のセキュリティの管轄外の状態メッセージから収集されます。 この脅威を軽減するには、クライアント コンピューターと管理ポイント間で、SMB 署名または IPsec を使用します。|  
|証明書テンプレートに対する読み取りアクセス許可または登録アクセス許可は、ユーザーに付与しないでください。また、証明書テンプレート チェックをスキップするように証明書登録ポイントを構成しないでください。|System Center Configuration Manager は、ユーザーの読み取りおよび登録のセキュリティ アクセス許可を追加するかどうかの追加チェックをサポートしており、認証できない場合にこのチェックをスキップするように証明書登録ポイントを構成できますが、いずれの構成もセキュリティ ベスト プラクティスではありません。 詳細については、「[System Center Configuration Manager の証明書プロファイルに関する証明書テンプレート アクセス許可の計画](../../protect/plan-design/planning-for-certificate-template-permissions.md)」を参照してください。|  

## <a name="privacy-information-for-certificate-profiles"></a>証明書プロファイルのプライバシー情報  
 証明書プロファイルを使って、証明機関 (CA) のルート証明書とクライアント証明書を展開し、プロファイルの適用後にデバイスがコンプライアンスに対応しているかどうかを評価できます。 コンプライアンス対応情報は、管理ポイントからサイト サーバーに送信され、System Center Configuration Manager によってサイト データベースに保存されます。 コンプライアンス情報には、サブジェクト名や拇印などの証明書のプロパティが含まれます。 情報はデバイスが管理ポイントに送信するときは暗号化されますが、サイト データベースに保存するときは暗号化されません。 データベースに保存された情報は、90 日 (既定) 後に "期限切れの構成管理データの削除" というメンテナンス タスクで削除されるまで維持されます。 **** 削除間隔は構成できます。 対応情報がマイクロソフトに送信されることはありません。  

 証明書プロファイルは、System Center Configuration Manager の探索機能によって収集された情報を使用します。 探索のプライバシー情報の詳細については、「 **Security and privacy for System Center Configuration Manager** 」の「 [探索のプライバシー情報](../../core/plan-design/security/security-and-privacy.md)」を参照してください。  

> [!NOTE]  
>  ユーザーやデバイスに発行された証明書によって、機密情報にアクセス可能になる場合があります。  

 既定では、デバイスは証明書プロファイルを評価しません。 また、証明書プロファイルを構成し、それをユーザーまたはデバイスに展開する必要があります。  

 証明書プロファイルを構成する前に、プライバシー要件について検討してください。  



<!--HONumber=Nov16_HO1-->


