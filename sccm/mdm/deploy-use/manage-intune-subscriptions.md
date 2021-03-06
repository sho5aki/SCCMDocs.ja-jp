---
title: "System Center Configuration Manager に関連付けられた Intune サブスクリプションの管理 | Microsoft Docs"
description: "System Center Configuration Manager に関連付けられた Intune サブスクリプションを管理します。"
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b494767-68c1-47b1-9a86-591bff0ad491
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 2e0b3cd1070d0f8adb1219acd33c3126d2758a49
ms.contentlocale: ja-jp
ms.lasthandoff: 05/17/2017

---
# <a name="manage-an-intune-subscription-associated-with-system-center-configuration-manager"></a>System Center Configuration Manager に関連付けられた Intune サブスクリプションの管理

*適用対象: System Center Configuration Manager (Current Branch)*

Microsoft Intune (試用版サブスクリプションまたは有料サブスクリプション) を Configuration Manager に追加してから、別の Intune サブスクリプションに切り替える必要がある場合は、**Microsoft Intune サブスクリプション**と**サービス接続ポイント**の両方を Configuration Manager コンソールから削除する必要があります。これにより、新しいサブスクリプションを追加することができるようになります。

> [!NOTE]
> ハイブリッド モバイル デバイス管理では 1 回につき 1 つだけ Intune サブスクリプションを構成できます。

## <a name="how-to-delete-an-intune-subscription-from-configuration-manager"></a>Configuration Manager から Intune サブスクリプションを削除する方法

> [!IMPORTANT]
>  サブスクリプションを削除すると、Intune サブスクリプションによって管理されるデバイスに構成された、ユーザー登録、ポリシー、アプリの展開などのすべてのコンテンツが削除されます。

1.  Configuration Manager コンソールで、**[管理]** > **[概要]** > **[Cloud Services]** > **[Microsoft Intune サブスクリプション]** の順に移動します。

2.  表示された **[Microsoft Intune サブスクリプション]** を右クリックしてから、**[削除]** をクリックします。

3.   ウィザードで、**[Configuration Manager から Microsoft Intune サブスクリプションを削除]**、**[次へ]**、**[次へ]** の順にクリックして、サブスクリプションを削除します。


## <a name="how-to-remove-the-service-connection-point-role"></a>サービス接続ポイントの役割を削除する方法

1.  **[管理]** > **[概要]** > **[サイトの構成]** > **[サーバーとサイト システムの役割]** の順に移動します。

2.  **[サービス接続ポイント]** の役割をホストするサーバーを選びます。

3.  **[サイト システムの役割]** 一覧で、**[サービス接続ポイント]** を選んでから、リボンに表示されている **[役割の削除]** をクリックします。 ロールを削除することを確認します。 サービス接続ポイントが削除されます。

これで、新しいサービス接続ポイントを作成したり、Configuration Manager に新規 Intune サブスクリプションを追加したり、Configuration Manager を MDM 機関として設定したりできるようになります。

## <a name="how-to-change-mdm-authority-to-intune"></a>MDM 機関を Intune に変更する方法

バージョン 1610 以降では、MDM 機関を Configuration Manager から Intune に切り替えることができます。 この機能についての情報は間もなく公開されます。

