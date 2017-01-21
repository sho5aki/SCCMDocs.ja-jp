---
title: "移行のセキュリティとプライバシー | System Center Configuration Manager"
description: "System Center Configuration Manager 環境に移行するためのセキュリティのベスト プラクティスとプライバシー情報を確認します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6893fce1-7ad5-4151-9ba9-3096871e8e4a
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 8c47633cfe6a03d881ebd02154ca2ab2e3009b3e


---
# <a name="security-and-privacy-for-migration-to-system-center-configuration-manager"></a>System Center Configuration Manager への移行のセキュリティとプライバシー

*適用対象: System Center Configuration Manager (Current Branch)*

このトピックには、System Center Configuration Manager 環境に移行するためのセキュリティのベスト プラクティスとプライバシー情報が含まれています。  

## <a name="security-best-practices-for-migration"></a>移行のセキュリティのベスト プラクティス  
 次の表に、セキュリティのベスト プラクティスをまとめます。  

|セキュリティのベスト プラクティス|説明|  
|----------------------------|----------------------|  
|ソース サイトの SMS プロバイダー アカウントとソース サイトの SQL Server アカウントに、ユーザー アカウントではなく、コンピューター アカウントを使用します。|移行でユーザー アカウントを使用する必要がある場合は、移行完了後にアカウントの詳細を削除してください。|  
|ソース サイトの配布ポイントから移行先サイトの配布ポイントにコンテンツを移行する際には、IPsec を使用します。|不正な改ざんを検知するため移行対象のコンテンツはハッシュされますが、転送中にデータが変更された場合は移行に失敗します。|  
|移行ジョブを作成できる管理ユーザーを制限し、監視します。|移行先階層のデータベースの整合性は、管理ユーザーがソース階層からインポートすることを決めたデータの整合性によって左右されます。 また、管理ユーザーはソースのソース階層の全データを読むことができます。|  

### <a name="security-issues-for-migration"></a>移行に関するセキュリティの問題  
移行には以下のようなセキュリティの問題が伴います。  

-   クライアントがソース サイトからブロックされている場合、そのクライアント レコードが移行される前に、移行先階層に正常に割り当てられる場合があります。  

     Configuration Manager では、移行するクライアントのブロック状態が維持されますが、クライアント レコードの移行が完了する前にクライアントの割り当てが行われた場合には、クライアントが移行先階層に正常に割り当てられることがあります。  

-   監査メッセージは移行されません。  

ソース サイトから移行先サイトにデータが移行されると、ソース階層のすべての監査情報が失われます。  

## <a name="privacy-information-for-migration"></a>移行に関するプライバシー情報  
 移行処理では、ソース インフラストラクチャで指定したサイト データベースの情報が探索され、そのデータは移行先階層のデータベースに保管されます。 System Center Configuration Manager がソース サイトまたはソース階層から探索できる情報は、ソース環境で有効にしていた機能や、ソース環境で実行していた管理操作に応じて変わります。  

 セキュリティとプライバシー情報の詳細については、次のトピックのいずれかを参照してください。  

-   Configuration Manager 2007 のプライバシー情報の詳細については、Configuration Manager 2007 ドキュメント ライブラリの「[Configuration Manager 2007 のセキュリティとプライバシー](http://go.microsoft.com/fwlink/p/?LinkId=216450)」を参照してください。  

-   System Center 2012 Configuration Manager のプライバシー情報の詳細については、System Center 2012 Configuration Manager ドキュメント ライブラリの「[System Center 2012 Configuration Manager のセキュリティとプライバシー](https://technet.microsoft.com/library/gg682033.aspx)」を参照してください。  

-   System Center Configuration Manager のプライバシー情報の詳細については、「[System Center Configuration Manager のセキュリティとプライバシー](../../core/plan-design/security/security-and-privacy.md)」を参照してください。  

サポートされるデータ全体またはその一部を、ソース サイトから移行先階層に移行できます。  

移行は既定では有効化されず、いくつかの構成手順を実行しなければなりません。 移行情報はマイクロソフトに送信されません。  

ソース階層からデータを移行する前に、プライバシーの要件を考慮してください。  



<!--HONumber=Nov16_HO1-->


