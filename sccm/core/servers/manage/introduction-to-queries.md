---
title: "クエリの概要 | System Center Configuration Manager"
description: "クエリを作成して実行すると、System Center Configuration Manager 階層内で、クエリ条件に一致するオブジェクトを見つけることができます。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03d1b3a9-41db-4d3a-a70e-e05ab5dc8141
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 054f3cc5ba7963231df93ed0ceb973d20b2e8f8e


---
# <a name="introduction-to-queries-in-system-center-configuration-manager"></a>System Center Configuration Manager のクエリの概要

*適用対象: System Center Configuration Manager (Current Branch)*

クエリを作成して実行すると、System Center Configuration Manager 階層内で、クエリ条件に一致するオブジェクトを見つけることができます。 このようなオブジェクトとしては、特定の種類のコンピューターやユーザー グループなどの項目があります。 クエリは、サイト、コレクション、アプリケーション、インベントリ データなど、ほとんどの種類の Configuration Manager オブジェクトを返すことができます。  

 クエリを作成するときは、少なくとも 2 つのパラメーター、つまり検索する場所と検索する対象を指定する必要があります。 たとえば、Configuration Manager サイトのすべてのコンピューターで使用できるハード ディスクの空き領域を確認するには、使用できるハードディスク領域について、**[論理ディスク]** 属性クラスと **[空き領域 (MB)]** 属性を検索するクエリを作成します。  

 最初のクエリを作成した後、追加のクエリ条件を指定できます。 たとえば、クエリ結果が特定のサイトに割り当てられたコンピューターのみを含むように指定することができます。 また、結果の表示方法を変更して、必要な順序で結果を表示することもできます。 たとえば、ハード ディスクの空き領域を基準にして昇順または降順で結果を表示するように指定できます。  

 によって保存クエリを作成するときに Configuration Manager で表示されていると、**クエリ**内のノード、**監視**ワークスペース。 ここで、新しいクエリを作成してから、既存のクエリを実行し、更新し、管理することができます。  

 また、クエリを Configuration Manager コレクションのクエリ規則にインポートすることもできます。 詳細については、「[Configuration Manager でのコレクションの作成方法](../../../core/clients/manage/collections/create-collections.md)」を参照してください。  

## <a name="see-also"></a>関連項目  
 [System Center Configuration Manager のクエリのテクニカル リファレンス](../../../core/servers/manage/queries-technical-reference.md)



<!--HONumber=Nov16_HO1-->


