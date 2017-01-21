---

title: "ソフトウェア更新プログラムを監視する | Configuration Manager"
description: "System Center Configuration Manager コンソールには、更新プログラムとコンプライアンスを監視するためのアラートとステータスがあります。"
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 9afd7b0f-5c8e-48bc-9a65-1f7d74103688
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: fe41807cebf87f4e6bab47e41db0ffe7cc83c5d1

---
# <a name="monitor-software-updates-in-system-center-configuration-manager"></a>System Center Configuration Manager でのソフトウェア更新プログラムの監視

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager コンソールには、ソフトウェア更新プログラムのオブジェクト、プロセス、コンプライアンスの情報を監視するのに役立つさまざまな手段があります。 以下のセクションではソフトウェア更新プログラムの監視について説明します。

##  <a name="a-namebkmksualertsa-alerts-for-software-updates"></a><a name="BKMK_SUAlerts"></a> ソフトウェア更新プログラムのアラート  
 ソフトウェア更新プログラムのアラートを構成して、構成されている割合 (%) よりもソフトウェア更新プログラムの展開のコンプライアンス レベルが低い場合に管理ユーザーに通知できます。 ソフトウェア更新プログラムの展開のアラートは、次の場所で構成することができます。  

-   ADR の設定: 自動展開規則の作成ウィザードおよび ADR のプロパティでアラートの設定を構成できます。  

-   展開の設定: ソフトウェア更新プログラムの展開ウィザードおよび展開プロパティでアラートの設定を構成できます。  

アラートの設定を構成すると、指定されているアラート条件に一致した場合に、Configuration Manager でアラートが生成されます。 ソフトウェア更新プログラムのアラートは、次の場所で確認することができます。  

1.  最新のアラートを確認するには、[ソフトウェア ライブラリ **** ] ワークスペースの [ソフトウェア更新プログラム **** ] ノードを使用します。  

2.  構成されているアラートを管理するには、[監視 **** ] ワークスペースの [アラート **** ] ノードを使用します。  

##  <a name="a-namebkmksusyncstatusa-software-updates-synchronization-status"></a><a name="BKMK_SUSyncStatus"></a> ソフトウェア更新プログラムの同期ステータス  
 同期プロセスを開始した後に、階層内のすべてのソフトウェア更新プログラムの同期プロセスを Configuration Manager コンソールで監視することができます。 ソフトウェア更新プログラムの同期プロセスを監視するには、次の手順に従います。  

#### <a name="to-monitor-the-software-updates-synchronization-process"></a>ソフトウェア更新プログラムの同期プロセスを監視するには  

- Configuration Manager コンソールで、**[監視]** > **[概要]** > **[ソフトウェアの更新ポイントの同期ステータス]** に移動します。  

    Configuration Manager 階層内のソフトウェアの更新ポイントが結果ウィンドウに表示されます。 このビューから、すべてのソフトウェアの更新ポイントの同期ステータスを監視することができます。 同期プロセスの詳細情報を確認するには、各サイト サーバーの <*Configuration Manager のインストール パス*>\Logs にある wsyncmgr.log ファイルを確認してください。  

##  <a name="a-namebkmksudeploystatusa-software-update-deployment-status"></a><a name="BKMK_SUDeployStatus"></a> ソフトウェア更新プログラムの展開ステータス  
 ソフトウェア更新プログラム グループのソフトウェア更新プログラムを展開した後、または個々のソフトウェア更新プログラムを展開した後に、展開ステータスを監視することができます。 ソフトウェア更新プログラム グループまたはソフトウェア更新プログラムの展開ステータスを監視するには、次の手順に従います。  

#### <a name="to-monitor-deployment-status"></a>展開ステータスを監視するには  

1.  Configuration Manager コンソールで、**[監視]** > **[概要]** > **[展開]** に移動します。  

2.  展開ステータスを監視するソフトウェア更新プログラム グループ、またはソフトウェア更新プログラムをクリックします。  

3.  [ホーム **** ] タブの [展開 **** ] グループで、[ステータスの表示 ****] をクリックします。  

##  <a name="a-namebkmksureportsa-software-updates-reports"></a><a name="BKMK_SUReports"></a> ソフトウェア更新プログラムのレポート  
 ソフトウェアの更新の状態メッセージには、ソフトウェア更新プログラムのコンプライアンスに関する情報と、ソフトウェア更新プログラムの展開についての評価と強制実行状態に関する情報が示されます。 ソフトウェア更新プログラム レポートを実行して、これらの状態メッセージを表示できます。 事前定義されたソフトウェア更新プログラム レポートが 30 種類以上用意されています。 レポートは複数のカテゴリに分類され、ソフトウェア更新プログラムと展開に関する特定の情報のレポートに使用できます。 事前に構成されたレポートを使用するだけでなく、企業のニーズに応じて、ソフトウェア更新プログラムのカスタム レポートを作成することもできます。 詳しくは、「[レポートの操作とメンテナンス](../../core/servers/manage/operations-and-maintenance-for-reporting.md)」を参照してください。  

##  <a name="a-namebkmkmonitorcontenta-monitor-content"></a><a name="BKMK_MonitorContent"></a> コンテンツの監視  
 Configuration Manager コンソールでコンテンツを監視して、関連する配布ポイントについて、すべての種類のパッケージのステータスを確認できます。 たとえば、パッケージのコンテンツのコンテンツ検証ステータス、特定の配布ポイント グループに割り当てられているコンテンツのステータス、配布ポイントに割り当てられているコンテンツの状態、各配布ポイントのオプション機能 (コンテンツ検証、PXE、マルチキャスト) のステータスなどを確認できます。  

###  <a name="a-namebkmkcontentstatusa-content-status-monitoring"></a><a name="BKMK_ContentStatus"></a> コンテンツのステータスの監視  
 [監視 **** ] ワークスペースの [コンテンツのステータス **** ] ノードには、コンテンツ パッケージについての情報が表示されます。 パッケージに関する全般情報、パッケージの配布ステータス、およびパッケージに関する詳細なステータス情報を確認することができます。 コンテンツのステータスを表示するには、次の手順に従います。  

#### <a name="to-monitor-content-status"></a>コンテンツのステータスを監視するには  

1.  Configuration Manager コンソールで、**[監視]** > **[概要]** > **[配布ステータス]** > **[コンテンツのステータス]** に移動します。 パッケージが表示されます。  

2.  詳細なステータス情報を確認するパッケージを選択します。  

3.  [ホーム **** ] タブで [ステータスの表示 ****] をクリックします。 パッケージのステータスの詳細な情報が表示されます。  

###  <a name="a-namebkmkdpgroupstatusa-distribution-point-group-status"></a><a name="BKMK_DPGroupStatus"></a> 配布ポイント グループのステータス  
 [監視 **** ] ワークスペースの [配布ポイント グループのステータス **** ] ノードには、配布ポイント グループについての情報が表示されます。 配布ポイント グループに関する全般情報 (配布ポイント グループのステータスやコンプライアンス対応率など) に加え、配布ポイント グループの詳細なステータス情報も確認することができます。 次の手順に従って、配布ポイント グループのステータスを確認します。  

#### <a name="to-monitor-distribution-point-group-status"></a>配布ポイント グループのステータスを監視するには  

1.  Configuration Manager コンソールで、**[監視]** > **[概要]** > **[配布ステータス]** > **[配布ポイント グループのステータス]** に移動します。 すると、配布ポイント グループが表示されます。  

2.  詳細なステータス情報を確認する配布ポイント グループを選択します。  

3.  [ホーム **** ] タブで [ステータスの表示 ****] をクリックします。 配布ポイント グループの詳細なステータス情報が表示されます。  

###  <a name="a-namebkmkdpconfigstatusa-distribution-point-configuration-status"></a><a name="BKMK_DPConfigStatus"></a> 配布ポイントの構成ステータス  
 [監視 **** ] ワークスペースの [配布ポイントの構成ステータス **** ] ノードには、配布ポイントについての情報が表示されます。 PXE、マルチキャスト、コンテンツの検証など、配布ポイントでどの属性が有効になっているかを確認できます。 また、配布ポイントの詳細なステータス情報も見ることができます。 次の手順に従って、配布ポイント グループの構成ステータスを確認します。  

#### <a name="to-monitor-distribution-point-configuration-status"></a>配布ポイントの構成ステータスを監視するには  

1.  Configuration Manager コンソールで、**[監視]** > **[概要]** > **[配布ステータス]** > **[配布ポイントの構成のステータス]** に移動します。 すると、配布ポイントが表示されます。  

2.  配布ポイント ステータス情報を確認する配布ポイントを選択します。  

3.  [結果] ウィンドウで、[詳細 **** ] タブをクリックします。 すると、配布ポイントのステータス情報が表示されます。  



<!--HONumber=Nov16_HO1-->


