---

title: "ソフトウェア更新プログラムのメンテナンス | Configuration Manager"
description: "Configuration Manager の更新プログラムをメンテナンスするには、WSUS クリーンアップ タスクをスケジュールするか、手動で実行します。"
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
ms.assetid: 4b0e2e90-aac7-4d06-a707-512eee6e576c
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 1495aa474c39723767ec2d81bc60eb1582ac5504



---
# <a name="software-updates-maintenance"></a>ソフトウェア更新プログラムのメンテナンス

*適用対象: System Center Configuration Manager (Current Branch)*

Configuration Manager コンソールから WSUS クリーンアップ タスクをスケジュールして実行するか、ソフトウェアの更新ポイント コンポーネントのプロパティから、WSUS クリーンアップ タスクを手動で実行できます。 WSUS クリーンアップ タスクを実行することを選ぶと、次回、ソフトウェア更新プログラムを最新に保つときにこのタスクが実行されます。 期限切れのソフトウェアの更新プログラムは WSUS サーバー上で拒否状態に設定され、コンピューター上の Windows Update エージェントでこれらのソフトウェア更新プログラムをスキャンできなくなります。 既定では、WSUS クリーンアップ ジョブは 30 日ごとに実行されます。  

#### <a name="to-schedule-and-run-the-wsus-cleanup-job"></a>WSUS クリーンアップ ジョブをスケジュールし、実行するには  

1.  Configuration Manager コンソールで、**[管理]** > **[概要]** > **[サイト構成]** > **[サイト]** の順に移動します。  

2.  **[設定]** グループで **[サイト コンポーネントの構成]** をクリックし、 **[ソフトウェアの更新ポイント]** をクリックして、ソフトウェアの更新ポイント コンポーネントのプロパティを開きます。  

3.  **[置き換えの規則]** タブをクリックし、 **[WSUS クリーンアップ ウィザードの実行]**を選んでから **[OK]**をクリックします。



<!--HONumber=Nov16_HO1-->


