---
title: "オペレーティング システムの展開を監視する | Configuration Manager"
description: "オペレーティング システムの展開オブジェクトを監視するため、Configuration Manager コンソールにはアラート、レポート、およびさまざまなステータス インジケーターが用意されています。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 08085d94-295c-432f-b5e3-9736bce0193b
caps.latest.revision: 6
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 893e5fe2acee0ffedb7759be85fb2f911f631611


---
# <a name="monitor-operating-system-deployments-in-system-center-configuration-manager"></a>System Center Configuration Manager のオペレーティング システムの展開の監視

*適用対象: System Center Configuration Manager (Current Branch)*

Configuration Manager コンソールの次の機能を使用して、オペレーティング システムの展開オブジェクトを監視できます。  


##  <a name="a-namebkmkosdalertsa-alerts-for-operating-system-deployments"></a><a name="BKMK_OSDAlerts"></a> オペレーティング システムの展開のアラート  
 タスク シーケンスの展開設定でアラートを構成して、構成されている割合 (%) よりも展開のコンプライアンス レベルが低い場合に管理ユーザーに通知できます。  

 アラートの設定を構成すると、指定されているアラート条件に一致した場合に、Configuration Manager でアラートが生成されます。 次の場所で、タスク シーケンスの展開に関するアラートを確認することができます。  

1.  最新のアラートを確認するには、 **[ソフトウェア ライブラリ]** ワークスペースの **[オペレーティング システム]** ノードを使用します。  

2.  構成されているアラートを管理するには、[監視 **** ] ワークスペースの [アラート **** ] ノードを使用します。  

##  <a name="a-namebkmktsdeploystatusa-task-sequence-deployment-status"></a><a name="BKMK_TSDeployStatus"></a> タスク シーケンスの展開ステータス  
 タスク シーケンスを展開した後、展開ステータスを監視できます。 タスク シーケンスの展開ステータスを監視するには、次の手順に従います。  

#### <a name="to-monitor-deployment-status"></a>展開ステータスを監視するには  

1.  Configuration Manager コンソールで、[監視] をクリックします。 ****  

2.  [監視] ワークスペースで、[展開 ****] をクリックします。  

3.  展開ステータスを監視するタスク シーケンスをクリックします。  

4.  [ホーム **** ] タブの [展開 **** ] グループで、[ステータスの表示 ****] をクリックします。  

##  <a name="a-namebkmktsreportsa-operating-system-deployment-reports"></a><a name="BKMK_TSReports"></a> オペレーティング システムの展開レポート  
 使用可能な定義済みのオペレーティング システムの展開レポートが数多く用意されています。 レポートは複数のカテゴリに分類され、状態移行とタスク シーケンスの展開に関する特定の情報のレポートに使用できます。 事前に構成されたレポートを使用するだけでなく、企業のニーズに応じて、ソフトウェア更新プログラムのカスタム レポートを作成することもできます。 詳しくは、「[レポートの操作とメンテナンス](../../core/servers/manage/operations-and-maintenance-for-reporting.md)」を参照してください。  

##  <a name="a-namebkmkmonitorcontenta-monitor-content"></a><a name="BKMK_MonitorContent"></a> コンテンツの監視  
 Configuration Manager コンソールでコンテンツを監視して、関連する配布ポイントについて、すべての種類のパッケージのステータスを確認できます。 たとえば、パッケージのコンテンツのコンテンツ検証ステータス、特定の配布ポイント グループに割り当てられているコンテンツのステータス、配布ポイントに割り当てられているコンテンツの状態、各配布ポイントのオプション機能 (コンテンツ検証、PXE、マルチキャスト) のステータスなどを確認できます。  

###  <a name="a-namebkmkcontentstatusa-content-status-monitoring"></a><a name="BKMK_ContentStatus"></a> コンテンツのステータスの監視  
 [監視 **** ] ワークスペースの [コンテンツのステータス **** ] ノードには、コンテンツ パッケージについての情報が表示されます。 パッケージに関する全般情報、パッケージの配布ステータス、およびパッケージに関する詳細なステータス情報を確認することができます。 コンテンツのステータスを表示するには、次の手順に従います。  

#### <a name="to-monitor-content-status"></a>コンテンツのステータスを監視するには  

1.  Configuration Manager コンソールで、[監視] をクリックします。 ****  

2.  [監視] ワークスペースで、[配布ステータス ****] を展開して、[コンテンツのステータス ****] をクリックします。 パッケージが表示されます。  

3.  詳細なステータス情報を確認するパッケージを選択します。  

4.  [ホーム **** ] タブで [ステータスの表示 ****] をクリックします。 パッケージのステータスの詳細な情報が表示されます。  

###  <a name="a-namebkmkdpgroupstatusa-distribution-point-group-status"></a><a name="BKMK_DPGroupStatus"></a> 配布ポイント グループのステータス  
 [監視 **** ] ワークスペースの [配布ポイント グループのステータス **** ] ノードには、配布ポイント グループについての情報が表示されます。 配布ポイント グループに関する全般情報 (配布ポイント グループのステータスやコンプライアンス対応率など) に加え、配布ポイント グループの詳細なステータス情報も確認することができます。 次の手順に従って、配布ポイント グループのステータスを確認します。  

#### <a name="to-monitor-distribution-point-group-status"></a>配布ポイント グループのステータスを監視するには  

1.  Configuration Manager コンソールで、[監視] をクリックします。 ****  

2.  [監視] ワークスペースで、[配布ステータス ****] を展開して、[配布ポイント グループのステータス ****] をクリックします。 すると、配布ポイント グループが表示されます。  

3.  詳細なステータス情報を確認する配布ポイント グループを選択します。  

4.  [ホーム **** ] タブで [ステータスの表示 ****] をクリックします。 配布ポイント グループの詳細なステータス情報が表示されます。  

###  <a name="a-namebkmkdpconfigstatusa-distribution-point-configuration-status"></a><a name="BKMK_DPConfigStatus"></a> 配布ポイントの構成ステータス  
 [監視 **** ] ワークスペースの [配布ポイントの構成ステータス **** ] ノードには、配布ポイントについての情報が表示されます。 PXE、マルチキャスト、コンテンツの検証など、配布ポイントでどの属性が有効になっているかを確認できます。 また、配布ポイントの詳細なステータス情報も見ることができます。 次の手順に従って、配布ポイント グループの構成ステータスを確認します。  

#### <a name="to-monitor-distribution-point-configuration-status"></a>配布ポイントの構成ステータスを監視するには  

1.  Configuration Manager コンソールで、[監視] をクリックします。 ****  

2.  [監視] ワークスペースで、[配布ステータス ****] を展開して、[配布ポイントの構成ステータス ****] をクリックします。 すると、配布ポイントが表示されます。  

3.  配布ポイント ステータス情報を確認する配布ポイントを選択します。  

4.  [結果] ウィンドウで、[詳細 **** ] タブをクリックします。 すると、配布ポイントのステータス情報が表示されます。  



<!--HONumber=Nov16_HO1-->


