---
title: "資産インテリジェンスのセキュリティとプライバシー | System Center Configuration Manager"
description: "System Center Configuration Manager の資産インテリジェンスのセキュリティとプライバシーの情報を確認します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0c6f7a0-dcae-4e6d-aa28-35d464d97ff7
caps.latest.revision: 5
caps.handback.revision: 0
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 85e0b6e3a96852cbf9c8781a3124bff13a6c6fdd


---
# <a name="security-and-privacy-for-asset-intelligence-in-system-center-configuration-manager"></a>System Center Configuration Manager の資産インテリジェンスのセキュリティとプライバシー

*適用対象: System Center Configuration Manager (Current Branch)*

このトピックには、System Center Configuration Manager の資産インテリジェンスのセキュリティとプライバシーの情報が含まれています。  

##  <a name="a-namebkmksecurityaia-security-best-practices-for-asset-intelligence"></a><a name="BKMK_Security_AI"></a> 資産インテリジェンスに関するセキュリティのベスト プラクティス  
 資産インテリジェンスを使用する場合は、次のセキュリティ上のベスト プラクティスに従ってください。  

|セキュリティのベスト プラクティス|説明|  
|----------------------------|----------------------|  
|ライセンス ファイル (マイクロソフト ボリューム ライセンス ファイル、または一般的なライセンス ステートメント ファイル) をインポートするときは、ファイルと通信チャネルをセキュリティ保護してください。|NTFS ファイルシステムの権限を使って、許可されたユーザーだけがライセンス ファイルにアクセスできるようにします。また、サーバー メッセージ ブロック (SMB) の署名によって、インポートの過程でサイト サーバーに転送されるとき、データの整合性を保つようにします。|  
|ライセンスのインポートでは最小限の特権という原則を使用してください。|役割に基づいた管理を行って、資産インテリジェンスの管理権限を、ライセンス ファイルをインポートする管理者に付与します。 資産管理者の組み込みロールには次の権限が含まれます。|  

##  <a name="a-namebkmkprivacyhardwareinventorya-privacy-information-for-asset-intelligence"></a><a name="BKMK_Privacy_HardwareInventory"></a> 資産インテリジェンスに関するプライバシー情報  
 資産インテリジェンスは、企業の資産をより高いレベルから表示するように Configuration Manager のインベントリ機能を拡張します。 資産インテリジェンス情報コレクションは自動で有効化されません。 収集される情報の種類は、ハードウェア インベントリ レポート クラスを有効にすると変更できます。 詳細については、「[System Center Configuration Manager での資産インテリジェンスの構成](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md)」を参照してください。  

 資産インテリジェンス情報は、インベントリ情報と同じ方法で Configuration Manager データベースに保存されます。 HTTPS を使用してクライアントが管理ポイントに接続するときは、データは管理ポイントへの転送中必ず暗号化されます。 HTTP を使用してクライアントが接続するときは、インベントリ データの転送に署名して暗号化するよう構成することができます。 インベントリ データは、暗号化された形式でデータベースに格納されるわけではありません。 情報は、90 日ごとに実行されるサイトのメンテナンス タスク [期限切れのインベントリ履歴の削除] によって削除されるまでデータベースに保持されます。 **** 削除間隔は構成できます。  

 資産インテリジェンスからは、Microsoft にユーザーおよびコンピューターに関する情報やライセンスの使用状況は送信されません。 System Center Online にカテゴリ化要求を送信することを選択できます。これは、カテゴリ化されていない 1 つまたは複数のソフトウェア タイトルにタグを付け、調査およびカテゴリ化用に System Center Online に送信できることを意味します。 ソフトウェア タイトルがアップロードされたら、マイクロソフトの調査担当者は、ソフトウェアを特定し、カテゴリ化して、オンライン サービスを利用されるすべてのお客様がその知識を利用できるようにします。 System Center Online に送信する情報の次のようなプライバシー問題に注意が必要です。  

-   アップロードは、System Center Online に送信することを選択した一般的なソフトウェア タイトル情報 (名前、発行元など) にのみ適用されます。 アップロードと共にインベントリ情報が送信されるわけではありません。  

-   アップロードは決して自動的には行われず、システムはこのタスクが自動化できるように設計されていません。 各ソフトウェア タイトルのアップロードを手動で選択および承認する必要があります。  

-   実際のアップロード処理が開始される前に、ダイアログ ボックスにアップロードされるデータの内容が表示されます。  

-   ライセンス情報はマイクロソフトに送信されません。 ライセンス情報は Configuration Manager データベースの独立した領域に保存されるため、マイクロソフトに送信することはできません。  

-   アップロードされたソフトウェア タイトルは、(特定のアプリケーションおよびアプリケーションのカテゴリ化の情報が System Center Online 資産インテリジェンス カタログを構成するものになるという意味で) 公開され、カタログの他の利用者にダウンロードされます。  

-   ソフトウェア タイトルのソースは資産インテリジェンス カタログには記録されず、他のお客様に入手可能にはなりません。 ただし、プライベートな情報が含まれているアプリケーション タイトルを読み込まないように確認する必要はあります。  

-   アップロードされたデータを取り消すことはできません。  

 資産インテリジェンス データ コレクションを構成して情報を System Center Online に送信するかどうかを判断する前に、所属組織のプライバシー要件を考慮してください。  



<!--HONumber=Nov16_HO1-->


