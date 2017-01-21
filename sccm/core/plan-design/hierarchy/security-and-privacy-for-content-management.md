---
title: "コンテンツ管理のセキュリティとプライバシー | System Center Configuration Manager"
description: "System Center Configuration Manager のコンテンツ管理のセキュリティとプライバシーを最適化します。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f38b726-dc00-433a-ba05-5b7dbb0d8e99
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: fcc3c74e50a4cdac9337178f5fcfe710f0fa17a5


---
# <a name="security-and-privacy-for-content-management-for-system-center-configuration-manager"></a>System Center Configuration Manager におけるコンテンツ管理のセキュリティとプライバシー

*適用対象: System Center Configuration Manager (Current Branch)*

このトピックには、System Center Configuration Manager のコンテンツ管理のセキュリティとプライバシーの情報が含まれています。 次のトピックを参照しながら読むことをお勧めします。  

-   [System Center Configuration Manager のアプリケーション管理のセキュリティとプライバシー](../../../apps/plan-design/security-and-privacy-for-application-management.md)  

-   [System Center Configuration Manager のソフトウェア更新プログラムのセキュリティとプライバシー](/sccm/sum/plan-design/security-and-privacy-for-software-updates)  

-   [System Center Configuration Manager のオペレーティング システムの展開でのセキュリティとプライバシー](../../../osd/plan-design/security-and-privacy-for-operating-system-deployment.md)  

##  <a name="a-namebkmksecuritycontentmanagementa-security-best-practices-for-content-management"></a><a name="BKMK_Security_ContentManagement"></a> コンテンツ管理に関するセキュリティのベスト プラクティス  
 ここでは、コンテンツ管理に関するセキュリティのベスト プラクティスについて説明します。  

 **イントラネット上の配布ポイントについて、HTTPS と HTTP の長所と短所を検討する** - ほとんどのシナリオでは、HTTP とパッケージ アクセス アカウントを承認に使用するほうが、暗号化はするが承認はしない HTTPS を使用するよりもセキュリティが高くなります。 ただし、転送中に暗号化する機密データがコンテンツにあれば、HTTPS を使用します。  

-   **HTTPS を配布ポイントに使用すると**、Configuration Manager はコンテンツへのアクセスを承認するためにパッケージ アクセス アカウントを使用しませんが、コンテンツがネットワーク上を転送されるときに暗号化されます。  

-   **HTTP を配布ポイントに使用すると**、パッケージ アクセス アカウントを使用して承認できますが、コンテンツがネットワーク上を転送されるときに暗号化はされません。  


**配布ポイントに、自己署名入り証明書ではなく PKI クライアント認証証明書を使用する場合は、強力なパスワードで証明書ファイル (.pfx) を保護する。ファイルをネットワーク上に保存する場合は、ファイルを Configuration Manager にインポートするときにネットワーク チャネルをセキュリティで保護する。** - 管理ポイントと通信する配布ポイントに使用するクライアント認証証明書をインポートするためにパスワードが必要であれば、攻撃者から証明書を保護することになります。 ネットワークの場所とサイト サーバーの間で SMB 署名または IPsec を使用して、攻撃者が証明書ファイルを改ざんするのを防ぎます。  

**サイト サーバーから配布ポイントの役割を削除する** - 既定では、配布ポイントはサイト サーバーと同じサーバーにインストールされます。 クライアントはサイト サーバーと直接通信する必要はないため、攻撃対象を縮小するために、配布ポイントの役割を他のサイト システムに割り当て、サイト サーバーからは削除します。  

**パッケージ アクセス レベルでコンテンツを保護する** -配布ポイントを共有すると、すべてのユーザーに読み取りアクセス権が許可されます。 ユーザーがアクセス可能なコンテンツを制限するために、配布ポイントが HTTP に構成される場合はパッケージ アクセス アカウントを使用します。 これは、パッケージ アクセス アカウントがサポートされないクラウドベースの配布ポイントには該当しません。 パッケージ アクセス アカウントの詳細については、「[コンテンツにアクセスするためのアカウントの管理](../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md)」を参照してください。


**配布ポイント サイト システムの役割を追加するときに Configuration Manager が IIS をインストールする場合は、配布ポイントのインストールが完了するときに、HTTP リダイレクトと IIS 管理スクリプトおよびツールを削除する。** - 配布ポイントに HTTP リダイレクトと IIS 管理スクリプトおよびツールは必要ありません。 攻撃対象を減らすために、Web サーバー (IIS) の役割についてこれらの役割サービスを削除します。  配布ポイントの役割サービスの詳細については、「[サイトとサイト システムの前提条件](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)」セクションを参照してください。  

**パッケージを作成するときにパッケージ アクセス許可を設定する** - パッケージ ファイルのアクセス アカウントの変更は、パッケージを再配布したときにのみ有効になるため、最初にパッケージを作成するときに、パッケージ アクセス許可を設定します。 パッケージが大きい場合、パッケージが多数の配布ポイントに配布される場合、コンテンツを配布するためのネットワーク帯域幅容量が限られている場合は、これは特に重要です。  

**事前設定されたコンテンツを含むメディアを保護するためにアクセス制御を実装する** - 事前設定されたコンテンツは圧縮されていますが暗号化されていません。 攻撃者がファイルを読み取って変更し、デバイスにダウンロードする可能性があります。 Configuration Manager クライアントが改ざんされているコンテンツを拒否しても、それでもダウンロードされます。  

**Configuration Manager で提供される ExtractContent コマンドライン ツール (ExtractContent.exe) のみを使用して事前設定されたコンテンツをインポートし、Microsoft によって署名されているかどうか確認する** - 改ざんと権限の昇格を避けるために、Configuration Manager で提供される承認済みコマンドライン ツールのみをご使用ください。  

**サイト サーバーとパッケージ ソースの場所との間の通信チャネルをセキュリティで保護する** - アプリケーションおよびパッケージを作成するときには、サイト サーバーとパッケージ ソースの場所との間で IPsec または SMB 署名を使用します。 これにより、攻撃者からソース ファイルの改ざんを防ぎます。  

**配布ポイントの役割のインストール後に、既定の Web サイトではなくカスタム Web サイトを使うためにサイトの構成オプションを変更する場合は、既定の仮想ディレクトリを削除する** - 既定の Web サイトからカスタム Web サイトの使用に変更した場合、Configuration Manager により、前の仮想ディレクトリが削除されることはありません。 既定の Web サイトの下に Configuration Manager によって作成された、仮想ディレクトリを削除します。  

-   SMS_DP_SMSPKG$  

-   SMS_DP_SMSSIG$  

-   NOCERT_SMS_DP_SMSPKG$  

-   NOCERT_SMS_DP_SMSSIG$  

**クラウドベースの配布ポイントについて、サブスクリプションの詳細と証明書を保護する** - クラウド ベースの配布ポイントを使用する場合は、Azure サブスクリプションのユーザー名とパスワード、Azure 管理証明書、クラウド ベースの配布ポイント サービス証明書など、重要な項目を保護します。 証明書を安全に保存します。また、クラウドベースの配布ポイントを構成するときにネットワーク上の証明書を参照する場合、サイト システム サーバーとソースの場所の間で IPsec または SMB 署名を使用します。  

**クラウド ベースの配布ポイント: サービスの継続性のために証明書の有効期限を監視する** - Configuration Manager は、クラウド ベースの配布ポイント サービスの管理のためにインポートした証明書の期限切れが近づいたときに警告しません。 Configuration Manager とは別に有効期限を監視し、有効期限前に新しい証明書に更新してインポートするようにします。 このような監視は、Configuration Manager クラウドベースの配布ポイント サービス証明書を外部証明機関 (CA) から購入している場合に特に重要です。更新された証明書を取得するために時間がかかる可能性があるためです。  

 いずれかの証明書の有効期限が切れると、 **Cloud Services Manager** によってステータス メッセージ ID **9425** が生成され、 **CloudMgr.log** ファイルにはログ記録された有効期限日 (UTC) とともに証明書の **is in expired state**を示すエントリが含まれます。  

## <a name="security-considerations-for-content-management"></a>コンテンツ管理についてのセキュリティの考慮事項  
コンテンツ管理を計画するときは、次のことをご考慮ください。  

-   クライアントはダウンロードが終わるまでコンテンツを検証しない  

     Configuration Manager クライアントは、コンテンツがクライアント キャッシュにダウロードされた後のみ、コンテンツのハッシュを検証します。 攻撃者によって、ダウンロードされるファイルのリスト、あるいはコンテンツ自体が改ざんされると、ダウンロード プロセスにおいて、クライアントのかなり広いネットワーク帯域幅が消費されてから、無効なハッシュが発生してコンテンツが破棄される可能性があります。  

-   クラウドベースの配布ポイントを使用する場合、コンテンツへのアクセスは社内に自動的に制限されるため、さらに選択したユーザーまたはグループに制限することはできません。  

-   クラウドベースの配布ポイントを使用する場合、クライアントは管理ポイントから認証され、Configuration Manager トークンを使用して、クラウドベースの配布ポイントにアクセスします。 トークンは 8 時間有効なので、信頼しなくなったクライアントをブロックしても、そのトークンの有効期間が切れるまで、クラウドベースの配布ポイントからコンテンツを継続してダウンロードできます。 この時点で、クライアントはブロックされているため、管理ポイントはクライアント用に追加のトークンを発行しません。  

     ブロックされたクライアントがこの 8 時間の間にコンテンツをダウンロードできないようにするため、Configuration Manager コンソールの **[管理]** ワークスペースにある **[階層の構成]** の **[クラウド]** ノードからクラウド サービスを停止することができます。  

##  <a name="a-namebkmkprivacycontentmanagementa-privacy-information-for-content-management"></a><a name="BKMK_Privacy_ContentManagement"></a> コンテンツ管理のプライバシー情報  
 管理ユーザーが選択することがありますが、Configuration Manager はコンテンツ ファイルのユーザー データを含みません。  

 コンテンツ管理を構成する前に、プライバシー要件について検討してください。  



<!--HONumber=Nov16_HO1-->


