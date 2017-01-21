---
title: "構成データを管理する | System Center Configuration Manager"
description: "System Center Configuration Manager で構成項目と基準を作成した後は、他のコマンドを使ってさまざまなアクションを実行できます。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b48c693c-d2b0-4707-a5dd-fe92172c49fe
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 4f9c78524bc264e55f7c8b5625a8d654ecabc8b7


---
# <a name="manage-configuration-data-in-system-center-configuration-manager"></a>System Center Configuration Manager で構成データを管理する

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Managerで構成項目と構成基準を作成した後は、他のコマンドを使ってさまざまなアクションを実行できます。  

## <a name="manage-configuration-items"></a>構成項目を管理する  

-   **[資産とコンプライアンス]** ワークスペースで、**[コンプライアンス設定]** > **[構成項目]** の順に展開し、管理対象の構成項目を選んでから、管理タスクを選びます。  

|管理タスク|説明|  
|---------------------|-------------|  
|**子構成項目の作成**|子構成項目の作成ウィザードが開き、選択した構成項目から、子構成項目を作成できます。 ****<br /><br /> モバイル デバイスの構成項目から子構成項目を作成することはできません。<br /><br /> 詳しくは、「[Create child configuration items](../../compliance/deploy-use/create-child-configuration-items.md)」 (子構成項目を作成する) を参照してください。|  
|**リビジョン履歴**|[構成項目のリビジョン履歴] ダイアログ ボックスが開き、選択した構成項目の以前のリビジョンを表示し管理できます。 ****|  
|**XML 定義の表示**|新しいウィンドウに選択した構成項目の XML 定義ファイルが表示されます。 この情報は、構成データを手動で作成するときに役立ちます。|  
|**エクスポート**|構成項目がサイト内で作成された場合は、その構成項目をキャビネット (.cab) ファイル形式でエクスポートします。 その後、Configuration Manager の同じサイトや別のサイトにインポートできます。 構成データは DCM ダイジェストに変換されます。|  
|**コピー**|選択した構成項目のコピーを指定した名前で作成します。 新しい構成項目は、コピー元の構成項目とは一切関係を保持しません。 つまり、コピーされた構成項目は、元の構成項目の構成情報を継続的に継承しません。|  
|**削除**|[構成項目の削除] ダイアログ ボックスが開き、この構成項目への参照を確認できます。 ****<br /><br /> 構成項目を削除する前に、その構成項目へのすべての参照を削除する必要があります。|  

## <a name="manage-configuration-baselines"></a>構成基準を管理する  

-   **[資産とコンプライアンス]** ワークスペースで、**[コンプライアンス設定]** > **[構成基準]** の順に展開し、管理対象の構成基準を選んでから、管理タスクを選びます。  


|管理タスク|説明|  
|---------------------|-------------|  
|**メンバーの表示**|構成基準が参照するすべての構成項目を表示します。|  
|**スケジュールの概要作成**|Configuration Manager コンソールの **[構成基準]** ノードに表示されるデータが、サイト データベースからの最新情報で更新されるスケジュールを構成します。|  
|**概要作成を実行します。**|概要作成を行うと、[構成基準] ノードにあるデータがサイト データベースからの最新データで更新されます。 **** この操作が完了するまでに数分かかることがあります。 コンソールで最新データを表示するには、[最新の情報に更新] をクリックする必要がある場合があります。 ****|  
|**XML 定義の表示**|新しいウィンドウに選択した構成基準の XML 定義ファイルが表示されます。 この情報は、構成データを手動で作成するときに役立ちます。|  
|**有効化**|コンプライアンス対応の監視用に構成基準を有効にします。|  
|**無効化**|クライアント コンピューターのコンプライアンス対応の評価をやめるように構成基準を無効化します。 この構成基準を参照する構成基準も無効になります。|  
|**エクスポート**|構成項目がサイト内で作成された場合は、その構成基準をキャビネット (.cab) ファイル形式でエクスポートします。 その後、Configuration Manager の同じサイトや別のサイトにインポートできます。 構成データは DCM ダイジェストに変換されます。<br /><br /> 構成データのインポート方法について詳しくは、「[Import configuration data](../../compliance/deploy-use/import-configuration-data.md)」 (構成データのインポート) を参照してください。|  
|**コピー**|選択した構成基準のコピーを指定した名前で作成します。 新しい構成基準は、コピー元の構成基準とは一切関係を保持しません。|  
|**削除**|[構成基準の削除] ダイアログ ボックスが開き、この構成基準への参照を確認できます。 ****<br /><br /> 構成基準を削除する前に、その構成基準へのすべての参照を削除する必要があります。|  
|**デプロイ**|[構成基準の展開] ダイアログ ボックスが開き、階層内のデバイスに 1 つまたは複数の構成基準を展開できます。 ****<br /><br /> 詳しくは、「[構成基準を展開する](../../compliance/deploy-use/deploy-configuration-baselines.md)」を参照してください。|  



<!--HONumber=Nov16_HO1-->


