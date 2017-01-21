---
title: "インターナショナル サポート | System Center Configuration Manager"
description: "外国の特定の要件に準拠するように System Center Configuration Manager を構成します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46dd9cb2-a812-4b6a-a747-b840f92fef8b
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 592ae2b8fbf55fa59afe909071a81b6bd3159ef7


---
# <a name="international-support-in-system-center-configuration-manager"></a>System Center Configuration Manager のインターナショナル サポート

*適用対象: System Center Configuration Manager (Current Branch)*

次のセクションでは、特定の国際的要件に準拠するように System Center Configuration Manager を構成するための技術詳細について説明します。  

## <a name="gb18030-requirements"></a>GB18030 の要件  
 Configuration Manager は、GB18030 で定義された規格に対応しているため、中国で Configuration Manager を使用することができます。 GB18030 の要件を満たすには、Configuration Manager 展開に次の構成が必要です。  

-   Configuration Manager で使用する各サイト サーバー コンピューターと SQL Server コンピューターが中国語のオペレーティング システムを使用している必要があります。  

-   階層内の各サイト データベースと SQL Server の各インスタンスが同じ照合順序を使用する必要があります。以下のいずれかが使用されていなければなりません。  

    -   Chinese_Simplified_Pinyin_100_CI_AI  

    -   Chinese_Simplified_Stroke_Order_100_CI_AI  

    > [!NOTE]  
    >  これらのデータベース照合順序は、「[System Center Configuration Manager の SQL Server バージョンのサポート](../../../core/plan-design/configs/support-for-sql-server-versions.md)」に記載された要件の例外となります。  

-   **GB18030.SMS** という名前のファイルを、階層内の各サイト サーバー コンピューターのシステム ボリュームのルート フォルダーに配置する必要があります。 このファイルにはデータは保存されません。この要件を満たす名前が付けられた空のテキスト ファイルを使用できます。  



<!--HONumber=Nov16_HO1-->


