---
title: "ネットワーク共有からの Endpoint Protection のマルウェア定義 | System Center Configuration Manager"
description: "Microsoft から最新の定義ファイルの更新を手動でダウンロードし、これらの定義をダウンロードするようにクライアントを構成する方法について説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ddef4d2a-f481-4020-9ddd-9cca5f9795cb
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: e4ff39f89a71ddbf9cadfcfa80f0c5c019611a35


---

# <a name="enable-endpoint-protection-malware-definitions-to-download-from-a-network-share-for-configuration-manager"></a>Configuration Manager で Endpoint Protection のマルウェア定義をネットワーク共有からダウンロードできるようにする

*適用対象: System Center Configuration Manager (Current Branch)*

 Microsoft から最新の定義ファイルの更新を手動でダウンロードし、ネットワーク上の共有フォルダーからこれらの定義をダウンロードするようにクライアントを構成できます。 この更新ソースを使用する場合、ユーザーは定義ファイルの更新も開始できます。

> [!NOTE]
>  クライアントは、定義ファイルの更新をダウンロードするために、共有フォルダーへの読み取りアクセス権が必要です。

 定義とエンジンの更新プログラムをダウンロードしてファイル共有に保存する方法の詳細については、「[Install the latest Microsoft antimalware and antispyware software](http://www.microsoft.com/security/portal/Definitions/HowToForeFront.aspx)」 (最新の Microsoft マルウェア対策およびスパイウェア対策ソフトウェアのインストール) をご覧ください。

## <a name="to-configure-definition-downloads-from-a-file-share"></a>ファイル共有からの定義ファイルのダウンロードを構成するには

1.  Configuration Manager コンソールで、[ **資産とコンプライアンス**] をクリックします。

2.  **[資産とコンプライアンス]** ワークスペースで **[Endpoint Protection]**を展開してから、 **[マルウェア対策ポリシー]**をクリックします。

3.  **[既定のマルウェア対策ポリシー]** プロパティ ページを開くか、新しいマルウェア対策ポリシーを作成します。 マルウェア対策ポリシーを作成する方法の詳細については、「[System Center Configuration Manager で Endpoint Protection 用にマルウェア対策ポリシーを作成し展開する方法](endpoint-antimalware-policies.md)」をご覧ください。

4.  マルウェア対策プロパティ ダイアログ ボックスの **[定義ファイルの更新]** セクションで **[ソースの設定]**をクリックします。

5.  **[定義ファイルの更新ソースの構成]** ダイアログ ボックスで、 **[UNC ファイル共有から更新する]**を選びます。

6.  **[OK]** をクリックして **[定義ファイルの更新ソースの構成]** ダイアログ ボックスを閉じます。

7.  **[パスの設定]**をクリックします。 次に、 **[定義更新プログラム用 UNC パスの構成]** ダイアログ ボックスで、ネットワーク共有上の定義ファイルの更新ファイルの場所を示す UNC パスを 1 つまたは複数追加します。

8.  **[OK]** をクリックして **[定義更新プログラム用 UNC パスの構成]** ダイアログ ボックスを閉じます。


> [!div class="button"]
[次のステップ >](endpoint-antimalware-policies.md)

> [!div class="button"]
[戻る >](endpoint-configure-alerts.md)



<!--HONumber=Nov16_HO1-->


