---
title: "構成基準の展開 | System Center Configuration Manager"
description: "構成基準を展開し、構成基準の展開の定義や、展開に対する構成基準の追加や削除を行います。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9be8aaf3-075e-4acd-abd2-7459254e16e2
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 47aad22bc88d3a466767e4d131122fbee38e3fd7


---
# <a name="how-to-deploy-configuration-baselines-in-system-center-configuration-manager"></a>System Center Configuration Manager で構成基準を展開する方法

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager の構成基準は、1 つまたは複数のユーザーまたはデバイスのコレクションに展開する必要があります。これにより、これらのコレクションに含まれるクライアント デバイスは、構成基準に対する自らのコンプライアンスを評価できるようになります。  

構成基準の展開を定義するには、[構成基準の展開] ダイアログ ボックスを使用します。このダイアログ ボックスでは、展開からの構成基準の追加と削除や評価スケジュールの指定などを行います。 ****  

## <a name="deploy-a-configuration-baseline"></a>構成基準の展開  

1.  Configuration Manager コンソールで、**[資産とコンプライアンス]** > **[コンプライアンス設定]** > **[構成基準]** の順にクリックします。  

3.  **構成基準** 一覧で、展開にする構成基準を選択し、[、 **ホーム** ] タブで、 **展開** グループで、[ **展開**です。  

4.  **構成基準の展開** ] ダイアログ ボックスで、展開する構成基準の選択、 **使用可能な構成基準** ] ボックスの一覧です。 クリックして **追加** に追加する、 **構成基準を選択した** ] ボックスの一覧です。  

    > [!IMPORTANT]  
    >  展開された構成基準に追加されている構成項目を変更する場合に、その次にスケジュールされた評価時間まで更新された構成項目は対応評価されません。  

5.  次の追加情報を指定します。  

    -   **[サポートされている場合は対応していない規則を修復する]** – Windows Management Instrumentation (WMI)、レジストリ、スクリプト、および、Configuration Manager が登録したモバイル デバイスのすべての設定が対応しない規則があれば、自動的に修復します。  

    -   **[メンテナンス期間以外の修復を許可する]** – このオプションを有効にすると、構成基準の展開先のコレクションにメンテナンス期間が設定されていても、コンプライアンス設定がメンテナンス期間外に値を修復します。 メンテナンス期間について詳しくは、「[メンテナンス期間を使用する方法](/sccm/core/clients/manage/collections/use-maintenance-windows)」をご覧ください。  

6.  **[アラートを生成する]** – 構成基準のコンプライアンスが、指定した日付と時刻までに指定した割合に達しなかった場合に生成されるアラートを構成します。 アラートを System Center Operations Manager に送信するかどうかも指定できます。  

7.  **[コレクション]** - **[参照]** をクリックして、構成基準を展開するコレクションを選択します。  

8.  **[この構成基準のコンプライアンス評価スケジュールを指定してください]** – 展開された構成基準をクライアント コンピューターで評価するスケジュールを指定します。 簡易スケジュールまたはカスタム スケジュールを使用できます。  

    > [!NOTE]  
    >  構成基準がコンピューターに展開された場合、スケジュールされた開始時間から 2 時間以内にコンプライアンスが評価されます。 ユーザーに展開された場合、ユーザーがログオンするとコンプライアンスが評価されます。  

9. をクリックして **[ok]** を閉じる、 **構成基準の展開** ] ダイアログ ボックスと、展開を作成します。 展開の監視方法の詳細については、「[Monitor compliance settings](/sccm/compliance/deploy-use/monitor-compliance-settings)」 (コンプライアンス設定の監視) をご覧ください。  



<!--HONumber=Nov16_HO1-->


