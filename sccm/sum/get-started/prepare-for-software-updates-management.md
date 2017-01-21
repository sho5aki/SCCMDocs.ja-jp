---

title: "ソフトウェア更新管理の準備 | Configuration Manager"
description: "更新管理を準備するには、次のタスクを実行して、System Center Configuration Manager コンソールでコンプライアンス対応評価データを表示します。"
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
ms.assetid: 01907900-e28b-4cd7-9479-42906416707b
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 54da71905de83133012c124dbc25283258141d6c


---

# <a name="prepare-for-software-updates-management"></a>ソフトウェア更新管理の準備

*適用対象: System Center Configuration Manager (Current Branch)*

ソフトウェア更新のコンプライアンス対応評価データを System Center Configuration Manager コンソールに表示し、ソフトウェア更新をクライアント コンピューターに展開する前に、次のセクションの手順を完了する必要があります。

## <a name="step-1-install-a-software-update-point"></a>手順 1: ソフトウェアの更新ポイントのインストール  
ソフトウェア更新プログラムのコンプライアンス対応評価を有効にし、ソフトウェア更新プログラムをクライアントに展開するには、中央管理サイトとスタンドアロン プライマリ サイトにソフトウェアの更新ポイントが必要です。 セカンダリ サイトのソフトウェアの更新ポイントは、オプションです。 詳細については、「[ソフトウェアの更新ポイントのインストール](install-a-software-update-point.md)」を参照してください。  

## <a name="step-2-synchronize-software-updates"></a>手順 2: ソフトウェア更新プログラムの同期
ソフトウェア更新プログラムの同期は、構成された基準を満たすソフトウェア更新プログラムのメタデータを取得するプロセスです。 ソフトウェア更新プログラムを同期するまで、ソフトウェア更新プログラムは Configuration Manager コンソールに表示されません。 詳細については、「[ソフトウェア更新プログラムの同期](synchronize-software-updates.md)」を参照してください。   

## <a name="step-3-configure-classifications-and-products-to-synchronize"></a>手順 3: 同期する分類と製品の構成
この構成は、中央管理サイトまたはスタンドアロン プライマリ サイトで行います。 ソフトウェア更新プログラムを初めて同期した後で、Configuration Manager は、更新された分類および製品の一覧を取得します。 これで、ソフトウェアの更新ポイント コンポーネントのプロパティの新しいオプションから選択できます。 新しい分類と製品を構成した後は、手順 2 を繰り返して、ソフトウェア更新プログラムの同期を開始し、新しい条件のソフトウェア更新プログラムのメタデータを取得します。 詳細については、「[同期する分類と製品の構成](configure-classifications-and-products.md)」を参照してください。

## <a name="step-4-manage-settings-for-software-updates"></a>手順 4: ソフトウェア更新プログラムの設定の管理
ソフトウェア更新プログラムを同期した後は、ソフトウェア更新プログラムを展開する前に、Configuration Manager クライアントの設定、グループ ポリシーの構成、およびソフトウェア更新プログラムの設定を確認します。 詳細については、「[ソフトウェア更新プログラムの設定の管理](manage-settings-for-software-updates.md)」を参照してください。



<!--HONumber=Nov16_HO1-->


