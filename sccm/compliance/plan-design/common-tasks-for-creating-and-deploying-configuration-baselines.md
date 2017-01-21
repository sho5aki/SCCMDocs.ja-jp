---
title: "System Center Configuration Manager での構成基準の作成と展開に関する一般的なタスク | System Center Configuration Manager"
description: "System Center Configuration Manager の構成基準を作成して展開する方法について説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4bb6afeb-d267-4f9b-ade2-26e5400c223b
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 0d66240408dcd65576954ffb27395d3f05f5a41e


---
# <a name="common-tasks-for-creating-and-deploying-configuration-baselines-with-system-center-configuration-manager"></a>System Center Configuration Manager での構成基準の作成と展開に関する一般的なタスク

*適用対象: System Center Configuration Manager (Current Branch)*

このトピックには、System Center Configuration Manager の構成基準を作成および展開する方法を習得するのに役立つ一般的なシナリオが含まれます。  

 [構成基準の作成](../../compliance/deploy-use/create-configuration-baselines.md)と[構成基準の展開](../../compliance/deploy-use/deploy-configuration-baselines.md)についてのトピックには、コンプライアンス設定に関する知識を既にお持ちの方を対象とした、使用するすべての機能に関する詳細なドキュメントが記載されています。  

 作業を開始する前に、「[System Center Configuration Manager のコンプライアンス設定を使ってみる](../../compliance/get-started/get-started-with-compliance-settings.md)」をお読みになり、いくつかの基本的なコンプライアンス設定を確認してください。また、[コンプライアンス設定の計画と構成](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)に関するページをお読みになり、必要な前提条件の実装方法を確認してください。  

## <a name="create-a-configuration-baseline"></a>構成基準の作成  
 この例では、Configuration Manager クライアントを実行している Windows 10 PC のみを対象に構成項目を作成しました。  

 この構成項目では、Windows 10 PC で 6 文字以上のパスワードが求められるように指定します。 構成項目には、" **Windows 10 パスワード適用**" という名前が付けられます。  

次の手順では、この構成項目を構成基準に追加して、展開用に準備する方法について説明します。  

1.  Configuration Manager コンソールで、**[資産とコンプライアンス]** > **[コンプライアンス設定]** > **[構成基準]** の順にクリックします。  

3.  **ホーム** ] タブで、 **作成** グループで、[ **構成基準の作成**です。  

4.  **[構成基準の作成]** ダイアログ ボックスで、次を構成します。  

    -   **名前** - **Windows 10 パスワード** (または任意の別の名前)  

5.  **[追加]** > **[構成項目]** の順にクリックします。  

6.  **[構成項目の追加]** ダイアログ ボックスで、前に作成した **[Windows 10 パスワード適用]** 構成項目を選択し、 **[追加]**をクリックします。  

7.  [OK] をクリックして **[構成項目の追加]** ダイアログ ボックスを閉じて、 **[構成基準の作成]** ダイアログ ボックスに戻ります (次のスクリーンショットを参照)。  

     ![[構成基準の作成] ダイアログ ボックス](/sccm/compliance/plan-design/media/Create-Configuration-Baseline.png)  

8.  **[OK]** をクリックして、 **[構成基準の作成]** ダイアログ ボックスを閉じます。  

 これで、Configuration Manager コンソールの **[構成基準]** ノードに作成した構成基準が表示されます。  

## <a name="deploy-the-configuration-baseline"></a>構成基準の展開  
 この例では、前の手順で作成した構成基準をコンピューターのコレクションに展開します。  

1.  Configuration Manager コンソールで、**[資産とコンプライアンス]** > **[コンプライアンス設定]** > **[構成基準]** の順にクリックします。  

3.  構成基準の一覧から、 **[Windows 10 パスワード]**を選択します。  

4.  [ **ホーム** ] タブの [ **展開** ] グループで、[ **展開**] をクリックします。  

5.  **[構成基準の展開]** ダイアログ ボックスで、次を構成します。  

    -   **選択した構成基準** - **[Windows 10 パスワード]** 構成基準が、この一覧に自動的に追加されたことを確認します。  

    -   **サポートされている場合は対応していない規則を修復する** - このチェック ボックスをオンにすると、対象デバイスに正しい設定が存在しない場合に、Configuration Manager によって修復されます。  

    -   **コレクション** - **[参照]** をクリックして、構成基準の対応状況を評価および修復するコンピューターのコレクションを選択します。 この例では、構成基準は、組み込みの **[すべてのデスクトップ クライアントおよびサーバー クライアント]** コレクションに展開されました。  

        > [!TIP]  
        >  選択したコレクションに Windows 10 を実行していないコンピューターまたはデバイスが含まれていても、問題はありません。 サポートされているプラットフォームを作成した構成項目で構成してあれば、Windows 10 PC のみの対応状況が評価されます。  

    -   必要な場合は、構成基準を評価するスケジュールを構成します。 それ以外の場合は、既定の **7 日間**にしておきます。  

6.  ダイアログ ボックスは次のようになります。  

     ![[構成基準の展開] ダイアログ ボックス](/sccm/compliance/plan-design/media/Deploy-configuration-baselines.png)  

7.  **[OK]** をクリックして **[構成基準の展開]** ダイアログ ボックスを閉じると、展開が作成されます。  

 この展開のコンプライアンスに関する統計情報の概要を確認するには、 **[監視]** ワークスペースで **[展開]**をクリックします。 画面の下部に、 **[コンプライアンスに関する統計情報]** グラフが表示されます。  

 構成基準を監視する方法の詳細については、[コンプライアンス設定の監視](../../compliance/deploy-use/monitor-compliance-settings.md)に関するページを参照してください。  



<!--HONumber=Nov16_HO1-->


