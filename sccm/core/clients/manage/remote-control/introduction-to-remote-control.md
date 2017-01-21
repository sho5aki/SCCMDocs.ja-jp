---
title: "リモート コントロール | System Center Configuration Manager"
description: "System Center Configuration Manager のリモート コントロールの概要"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 29350919-6a25-446b-a0da-05e8914fbb26
caps.latest.revision: 4
caps.handback.revision: 0
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 6b5886e8f804a22745df5e4203001104a68d09eb


---
# <a name="introduction-to-remote-control-in-system-center-configuration-manager"></a>System Center Configuration Manager のリモート コントロールの概要

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager のリモート コントロールを使用して、リモートでの管理、支援の提供、階層内の任意のコンピューターの表示ができます。 リモート コントロールを使用することで、クライアント コンピューターのハードウェアやソフトウェアの構成に関する問題のトラブルシューティングを行ったり、ユーザーのコンピューターへのアクセスが必要な場合にヘルプ デスク サポートを提供したりできます。 Configuration Manager は、ワークグループ コンピューターと Active Directory ドメインに参加しているコンピューターのリモート コントロールをサポートしています。  

 また、Configuration Manager によって、Configuration Manager コンソールから Windows リモート デスクトップとリモート アシスタンスを実行して、クライアント設定を構成することができます。  

> [!NOTE]  
>  次のシナリオでは、Configuration Manager コンソールからクライアント コンピューターに、リモート アシスタンス セッションを確立できません。  
>   
>  -   クライアント コンピューターがワークグループにある。  
> -   Configuration Manager コンソールを実行するコンピューターは Windows XP Service Pack 3 を実行しているが、ホスト コンピューターは Windows XP Service Pack 3 を実行していない。 詳細については、Windows リモート アシスタンスのドキュメントを参照してください。  

 Configuration Manager コンソールの任意のデバイス コレクション、Windows コマンド プロンプト ウィンドウ、または Windows の **[スタート]** メニューから、リモート コントロール セッションを開始できます。  



<!--HONumber=Nov16_HO1-->


