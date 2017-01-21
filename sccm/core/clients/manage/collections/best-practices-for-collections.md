---
title: "コレクションのベスト プラクティス | System Center Configuration Manager"
description: "System Center Configuration Manager のコレクションのベスト プラクティスを示します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7a2abb79-9ae5-4a25-9e18-5dcf528de3bf
caps.latest.revision: 4
caps.handback.revision: 0
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 8e22f353ba0803a3b1b4d387a8c00fdb98186bf5


---
# <a name="best-practices-for-collections-in-system-center-configuration-manager"></a>System Center Configuration Manager のコレクションのベスト プラクティス

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager のコレクションに関する以下のベスト プラクティスを使用してください。  

## <a name="do-not-use-incremental-updates-for-a-large-number-of-collections"></a>多数のコレクションに対して、増分更新を使用しないでください。  
 [このコレクションで増分更新を使用する] オプションを多数のコレクションに対して有効にすると、この構成が評価の遅延を引き起こす可能性があります。 **** しきい値は、階層内では約 200 コレクションです。 正確な数は、次の要因によります。  

-   コレクションの総数  

-   階層内で、リソースが新しく追加または変更される頻度  

-   階層内のクライアント数  

-   階層内のコレクション メンバーシップ規則の複雑さ  

## <a name="make-sure-that-maintenance-windows-are-large-enough-to-deploy-critical-software-updates"></a>重要なソフトウェア更新プログラムを展開するのに十分なメンテナンス期間を確保する  
 デバイス コレクションのメンテナンス期間を構成して、Configuration Manager がソフトウェアをそれらのデバイスにインストールできる時間を制限することができます。 メンテナンス期間の構成で十分な時間が確保されていない場合、クライアントは重要なソフトウェア更新プログラムをインストールできない可能性があり、その結果、ソフトウェア更新プログラムによって緩和される攻撃に対して脆弱なままになります。  



<!--HONumber=Nov16_HO1-->


