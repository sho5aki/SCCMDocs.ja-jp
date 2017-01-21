---
title: "アプリケーション管理の概要 | System Center Configuration Manager"
description: "System Center Configuration Manager アプリケーションの管理と展開に必要な基本的な情報について説明します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 08f711ba-83bf-4b5f-9520-a0778c6ae7eb
caps.latest.revision: 18
author: robstackmsft
ms.author: robstack
manager: angrobe
experimental: true
experiment_id: rob-table-161101
translationtype: Human Translation
ms.sourcegitcommit: aa985dcb947803f7bc6d770f80a89a2fe6750681
ms.openlocfilehash: bec4d6d7008d5eabc7219dc7aaa1198c6e68a4df


---
# <a name="introduction-to-application-management-in-system-center-configuration-manager"></a>System Center Configuration Manager でのアプリケーション管理の概要

*適用対象: System Center Configuration Manager (Current Branch)*

このトピックでは、System Center Configuration Manager アプリケーションで作業を開始する前に理解しておく必要のある基本的な情報について学習します。  

> [!TIP]  
>  Configuration Manager でのアプリケーションの管理方法について既によく理解している場合は、このトピックをスキップし、サンプル アプリケーションの作成に進むことができます。 「[System Center Configuration Manager でのアプリケーションの作成と展開](../../apps/get-started/create-and-deploy-an-application.md)」を参照してください。  

## <a name="what-is-an-application"></a>アプリケーションとは  
 "アプリケーション" は広く使用されているコンピューター用語ですが、Configuration Manager では少し意味が異なります。 アプリケーションを 1 つの箱だと考えてみてください。 この箱には、ソフトウェア パッケージ ( **展開の種類**と呼ばれる) のインストール ファイルが 1 つ以上入っており、さらにソフトウェアの展開方法に関する指示が付属しています。  

 アプリケーションをデバイスに展開すると、デバイスにインストールされる展開の種類が **要件** に応じて決まります。  

 アプリケーションはもちろん、このほかにも多くのことができますが、そのような機能についてはこのガイドで後から説明します。 次の一覧に、あらかじめ理解しておく必要のあるいくつかの概念を示してあります。 これらの概念は、作成するアプリケーションによっては必要でない場合もあります。  



- **要件**以前のバージョンの Configuration Manager では、多くの場合、アプリケーションの展開先デバイスを含むコレクションを作成していました。 これは新バージョンでも可能ですが、インストールするアプリケーションを絞り込むための条件をより詳細に要件に指定できるようになったため、その必要性は軽減されました。<br> たとえば、Windows 10 を実行しているデバイスにのみアプリケーションをインストールするように指定できます。 これにより、アプリケーションをすべてのデバイスに展開することはできますが、Windows 10 を実行しているデバイスにしかインストールされません。<br> Configuration Manager クライアントは、要件を評価して、アプリケーションとその展開の種類のいずれかがインストールされるかどうかを判別します。 その後、適切な展開の種類を判別します。この展開の種類を使用して、アプリケーションがインストールされます。 クライアント設定の [ **展開の再評価スケジュールを指定する**] に従って、コンプライアンスを確認するため、要件が再評価されます (既定では 7 日ごと)。<br> 詳細については、「[アプリケーションの作成手順と展開手順](../../apps/get-started/create-and-deploy-an-application.md)」を参照してください。 


- **グローバルな条件**1 つのアプリケーションで要件を特定の展開の種類と組み合わせて使用する場合は、グローバル条件を作成することもできます。グローバル条件は、任意のアプリケーションおよび展開の種類とともに使用できる定義済み要件のライブラリです。<br> Configuration Manager には、一連の組み込みグローバル条件が用意されていますが、独自の条件を作成することもできます。<br> 詳細については、「[System Center Configuration Manager でグローバル条件を作成する方法](../../apps/deploy-use/create-global-conditions.md)」を参照してください。


- **展開のシミュレーション**アプリケーションの要件、検出方法、依存関係を評価し、実際にはアプリケーションをインストールせずに結果を報告します。<br> 詳細については、「[System Center Configuration Manager でアプリケーションの展開をシミュレーションする方法](../../apps/deploy-use/simulate-application-deployments.md)」を参照してください。 


- **展開アクション**展開しているアプリケーションをインストールするかアンインストールするかを指定します (ただし、サポートされている場合のみ)。<br> 詳細については、「[System Center Configuration Manager でアプリケーションを展開する方法](../../apps/deploy-use/deploy-applications.md)」を参照してください。  


- **展開の目的**展開アプリが**必須**であるか **利用可能**であるかを指定します。<br>
**必須**を指定した場合、アプリケーションは、構成されたスケジュールに従って自動的に展開されます。 ただし、ユーザーはアプリケーションの展開ステータスを (非表示にされていなければ) 追跡して、ソフトウェア センターを使用してアプリケーションを期限前にインストールすることができます。<br> [**利用可能** ] を選択した場合、アプリケーションが展開されたユーザーは、公開されているアプリケーションをソフトウェア センターで確認し、必要に応じてインストールできます。<br> 詳細については、「[System Center Configuration Manager でアプリケーションを展開する方法](../../apps/deploy-use/deploy-applications.md)」を参照してください。


- **リビジョン**アプリケーションまたはアプリケーションに含まれる展開の種類を修正すると、Configuration Manager はそのアプリケーションの新しいリビジョンを作成します。 各アプリケーションのリビジョンの履歴を表示したり、プロパティを閲覧したり、アプリケーションの以前のリビジョンを復元したり、古いリビジョンを削除したりすることができます。<br> 詳細については、「[System Center Configuration Manager でのアプリケーションの更新とインベントリからの削除](../../apps/deploy-use/update-and-retire-applications.md)」を参照してください。


- **検出方法**検出方法は、展開されたアプリケーションが既にインストールされているかどうかを判別するために使用されます。 検出方法によってアプリケーションがインストール済みであることが判明した場合、Configuration Manager はそのアプリケーションを再度インストールしようとはしません。<br> 詳細については、「[System Center Configuration Manager でアプリケーションを作成する方法](../../apps/deploy-use/create-applications.md)」を参照してください。 


- **依存関係**依存関係は、展開の種類をインストールする前にインストールする必要がある、別のアプリケーションからの 1 つまたは複数の展開の種類を定義します。 現在作成している展開に依存する展開の種類を構成して、先に自動的にインストールされるようにします。<br> 詳細については、「[System Center Configuration Manager でアプリケーションを作成する方法](../../apps/deploy-use/create-applications.md)」を参照してください。  


- **置き換え**Configuration Manager を使用すると、置き換えの関係を使用して、既存のアプリケーションをアップグレードするか置き換えることができます。 アプリケーションを置き換える際、新しい展開の種類を指定して置換対象のアプリケーションの展開の種類を置き換えたり、置き換わるアプリケーションをインストールする前に、置換対象のアプリケーションをアップグレードするのか置換対象のアプリケーションをアンインストールするのか構成することもできます。<br> 詳細については、「[System Center Configuration Manager でアプリケーションを作成する方法](../../apps/deploy-use/create-applications.md)」を参照してください。


- **ユーザー主体の管理**Configuration Manager のアプリケーションは、特定のユーザーを特定のデバイスに関連付けることができる、ユーザー主体の管理をサポートします。 ユーザーのデバイスの名前を記憶しなくても、アプリをユーザーとデバイスに展開することができます。 この機能により、特定のユーザーがアクセスする各デバイスで、最も重要なアプリを常に使用可能にすることができます。 ユーザーが新しいコンピューターを入手した場合、ユーザーがログオンする前に、そのデバイスにユーザーのアプリを自動的にインストールできます。<br> 詳細については、「[System Center Configuration Manager でのユーザーとデバイスのアフィニティへのユーザーとデバイスの関連付け](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)」を参照してください。  

## <a name="what-application-types-can-you-deploy"></a>展開可能なアプリケーションの種類  
 Configuration Manager では、次の種類のアプリケーションを展開できます。  

- Windows インストーラー (*.msi ファイル)
- Windows アプリ パッケージ (*.appx、 \*.appxbundle)
- Windows アプリケーション パッケージ (Windows ストア内)
- Microsoft Application Virtualization 4
- Microsoft Application Virtualization 5
- Windows Mobile キャビネット
- Mac OS X  


また、Microsoft Intune または Configuration Manager のオンプレミス デバイス管理でデバイスを管理すると、さらに次のアプリケーションの種類も管理できます。

- Windows Phone アプリケーション パッケージ (*.xap ファイル)
- iOS アプリ パッケージ (*.ipa ファイル)
- Android アプリ パッケージ (*.apk ファイル)
- Android 用アプリ パッケージ (Google Play 内)
- Windows Phone アプリケーション パッケージ (Windows Phone ストア内)
- MDM を介した Windows インストーラー
- Web アプリケーション



## <a name="state-based-applications"></a>状態ベースのアプリケーション  
 Configuration Manager アプリケーションは状態ベースの監視を使用しており、ユーザーとデバイスの最新のアプリケーション展開状態を追跡できます。 これらの状態メッセージには、個々のデバイスに関する情報が表示されます。 たとえば、アプリケーションがユーザーのコレクションに展開されている場合、Configuration Manager コンソールを使用して展開のコンプライアンス対応状態と展開の目的を表示できます。 ソフトウェアの展開を監視するには、Configuration Manager コンソールの **[監視]** ワークスペースを使用します。 ソフトウェアの展開には、ソフトウェアの更新、コンプライアンス設定、アプリケーション、タスク シーケンス、パッケージ、およびプログラムが含まれます。 詳細については、「[Monitor applications](/sccm/apps/deploy-use/monitor-applications-from-the-console)」(モニター アプリケーション) を参照してください。  

 アプリケーションの展開は Configuration Manager によって定期的に再評価されます。 たとえば、  

-   エンドユーザーが展開されているアプリケーションをアンインストールします。 次の評価サイクルで、Configuration Manager はアプリケーションが存在してしないことを検出し、再インストールします。  

-   アプリケーションは、要件を満たしていないため、デバイスにインストールされませんでした。 その後、デバイスが変更され、要件を満たすようになります。 Configuration Manager はその変更を検出し、アプリケーションはインストールされます。  

 [ **展開の再評価のスケジュール** ] クライアント設定を使用し、アプリケーションの展開の再評価間隔を設定できます。 詳細については、「[About client settings](../../core/clients/deploy/about-client-settings.md)」(クライアント設定の概要) を参照してください。  

## <a name="get-started-creating-an-application"></a>アプリケーション作成の概要  
 すぐにアプリケーションの作成を開始する場合は、「[Create and deploy an application](../../apps/get-started/create-and-deploy-an-application.md)」(アプリケーションの作成と展開) に単純なアプリケーションを作成するためのチュートリアルがあります。  

 アプリケーション作成の基礎知識がある場合は、使用可能なすべてのオプションについて詳しく説明している「[Create applications](/sccm/apps/deploy-use/create-applications)」(アプリケーションの作成) をまず参照してください。  

## <a name="software-center-and-the-application-catalog"></a>ソフトウェア センターとアプリケーション カタログ  
 以前のバージョンの Configuration Manager では、ソフトウェア センターを使用して、ソフトウェアのインストールとソフトウェア インストールのスケジュール、リモート コントロール設定の構成、および電源管理設定の構成を行っていました。 ユーザーはアプリケーション カタログに接続して、ソフトウェアの参照と要求、優先設定の構成、およびモバイル デバイスのリモートでのワイプを行うことができました。  

 これらの設定は System Center Configuration Manager で引き続き使用可能ですが、ソフトウェア センターの新しいバージョンが使用可能になり、Silverlight が有効になっている Web ブラウザーを必要とするアプリケーション カタログを使用せずにアプリケーションを参照することができます。 ただし、ユーザーが利用できるアプリをソフトウェア センターに表示するには、アプリケーション カタログ Web サイト ポイントとアプリケーション カタログ Web サービス ポイントのサイト システムの役割が引き続き必要です。  

 詳細については、「[Plan for and configure application management](../../apps/plan-design/plan-for-and-configure-application-management.md)」(アプリケーション管理の計画と構成) を参照してください。  

## <a name="using-configuration-manager-packages-and-programs"></a>Configuration Manager のパッケージとプログラムの使用  
 Configuration Manager は、以前のバージョンの製品で使用されていたパッケージおよびプログラムを引き続きサポートします。 次のいずれかを展開する場合、パッケージおよびプログラムを使用する展開は、アプリケーションを使用する展開よりも適切な場合があります。  

-   コンピューターにアプリケーションをインストールしないスクリプト (コンピューターのディスク ドライブを最適化するスクリプトなど)  

-   継続的に監視する必要がない "1 回限り" のスクリプト  

-   定期的なスケジュールに従って実行され、グローバルの評価版を使用できないスクリプト  

 詳細については「[Packages and programs](../../apps/deploy-use/packages-and-programs.md)」(パッケージとプログラム) を参照してください。  




<!--HONumber=Dec16_HO3-->


