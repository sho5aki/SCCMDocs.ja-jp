---
title: "コンテンツ ライブラリ | System Center Configuration Manager"
description: "分散型コンテンツの全体的なサイズを小さくするために System Center Configuration Manager が使用するコンテンツ ライブラリについて説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 65c88e54-3574-48b0-a127-9cc914a89dca
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 5406dcbc8b1ca04f2754e19b171c55ab20a00d46

---
# <a name="the-content-library-in-system-center-configuration-manager"></a>System Center Configuration Manager のコンテンツ ライブラリ

*適用対象: System Center Configuration Manager (Current Branch)*

コンテンツ ライブラリは、配布するコンテンツの合計サイズを減らすために System Center Configuration Manager が使用する、コンテンツの単一インスタンス ストアです。 コンテンツ ライブラリには、ソフトウェア更新プログラム、アプリケーション、オペレーティング システムなどの展開で使用するすべてのコンテンツ ファイルが格納されます。

 - コンテンツ ライブラリのコピーが、各 **サイト サーバー** と各 **配布ポイント**で自動的に作成および保持されます。
 - Configuration Manager がコンテンツ ファイルをサイト サーバーにダウンロードするか、それらのファイルを配布ポイントにコピーする前に、Configuration Manager は各コンテンツ ファイルが既にコンテンツ ライブラリにあるかどうかを確認します。
 - コンテンツ ファイルを使用できる場合、Configuration Manager はファイルをコピーする代わりに、既存のコンテンツ ファイルをアプリケーションまたはパッケージに関連付けます。

配布ポイントをインストールするコンピューターでは、次の項目を構成できます。
- コンテンツ ライブラリを作成する 1 つまたは複数のディスク ドライブ
- 使用する各ドライブの優先順位

Configuration Manager は、優先順位が最も高いドライブの空き領域が指定の最小値を下回るまで、そのドライブにコンテンツ ファイルをコピーします。
- ドライブ設定は、配布ポイントをインストールするときに構成します。
- インストールの完了後は、配布ポイントのプロパティでドライブ設定を構成することはできません。


配布ポイントのドライブ設定の構成方法については、「[Manage content and content infrastructure for System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)」 (System Center Configuration Manager のコンテンツとコンテンツ インフラストラクチャの管理) を参照してください。  


>  [!IMPORTANT]  
>  インストール後にコンテンツ ライブラリを配布ポイントの別の場所に移動するには、System Center 2012 R2 Configuration Manager Toolkit の **Content Library Transfer Tool** を使用します。 この Toolkit は、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkId=279566)からダウンロードできます。  

## <a name="about-the-content-library-on-the-central-administration-site"></a>中央管理サイトのコンテンツ ライブラリについて  
 Configuration Manager の既定では、サイトのインストール時に中央管理サイトにコンテンツ ライブラリを作成します。 コンテンツ ライブラリは、空きディスク領域が最も多いサイト サーバーのドライブに配置します。 配布ポイントは中央管理サイトにインストールできないため、コンテンツ ライブラリに使用するドライブを優先することはできません。 他のサイト サーバーおよび配布ポイントのコンテンツ ライブラリと同様に、コンテンツ ライブラリを含むドライブに空きディスク領域がなくなったら、コンテンツ ライブラリは次の空き領域があるドライブを自動的に使用します。  

 Configuration Manager は、次のシナリオで中央管理サイトのコンテンツ ライブラリを使用します。  

-   中央管理サイトでコンテンツを作成する場合。  

-   別の Configuration Manager サイトからコンテンツを移行し、そのコンテンツを管理するサイトとして中央管理サイトを割り当てる場合。  

> [!NOTE]  
>  プライマリ サイトにコンテンツを作成してから、別のプライマリ サイトまたは別のプライマリ サイトの下のセカンダリ サイトに配布すると、中央管理サイトは、中央管理サイトのスケジューラの受信トレイにコンテンツを一時的に保存しますが、そのコンテンツをコンテンツ ライブラリに追加しません。  

 次のオプションを使用して、中央管理サイトのコンテンツ ライブラリを管理します。  

-   コンテンツ ライブラリが特定のドライブにインストールされないようにするには、コンテンツ ライブラリを作成する前に、 **no_sms_on_drive.sms** と言う名前の空のファイルを作成して、ドライブのルート フォルダーにコピーしておきます。  

-   コンテンツ ライブラリを作成したら、System Center 2012 R2 Configuration Manager Toolkit の **Content Library Transfer ツール**を使用して、コンテンツ ライブラリの場所を管理します。 この Toolkit は、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkId=279566)からダウンロードできます。  



<!--HONumber=Nov16_HO1-->


