---
title: BranchCache ホスト型キャッシュ モードの展開計画
description: このガイドでは、Windows Server 2016 および Windows 10 を実行するコンピューターでホスト型キャッシュ モードで BranchCache の展開の説明
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-bc
ms.topic: article
ms.assetid: bc44a7db-f7a5-4e95-9d95-ab8d334e885f
ms.author: pashort
author: shortpatti
ms.openlocfilehash: e7232f8732e7476b955115741b5582a585dc6068
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59890683"
---
# <a name="branchcache-hosted-cache-mode-deployment-planning"></a>BranchCache ホスト型キャッシュ モードの展開計画

>適用対象:Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

このトピックを使用すると、ホスト型キャッシュ モードで BranchCache の展開を計画します。

>[!IMPORTANT]
>Windows Server 2016、Windows Server 2012 R2、または Windows Server 2012、ホスト型キャッシュ サーバーを実行する必要があります。

ホスト型キャッシュ サーバーを展開する前に、次のものを計画する必要があります。

- [基本的なサーバー構成を計画します。](#bkmk_basic)

- [ドメイン アクセスを計画します。](#bkmk_domain)

- [ホスト型キャッシュのサイズと場所を計画します。](#bkmk_cachelocation)

- [コンテンツ サーバーのパッケージがコピーされる共有を計画します。](#bkmk_package)

- [プランの事前ハッシュおよびデータ パッケージのコンテンツ サーバーの作成](#bkmk_prehash)

## <a name="bkmk_basic"></a>基本的なサーバー構成を計画します。
  
ホスト型キャッシュ サーバーとして、ブランチ オフィスで既存のサーバーの使用に関する計画している場合は、コンピューターは、という名前が既にあり、IP アドレスを構成するために、この計画の手順を実行する必要はありません。

ホスト型キャッシュ サーバーで Windows Server 2016 をインストールした後、コンピューターの名前を変更を割り当てると、ローカル コンピューターの静的 IP アドレスを構成してください。

>[!NOTE]
>このガイドで、ホスト型キャッシュ サーバーの名前が HCS1、展開に適切であるサーバー名を使用する必要があります。

## <a name="bkmk_domain"></a>ドメイン アクセスを計画します。

場合は、ブランチ オフィスで既存のサーバーを使用して、ホスト型キャッシュ サーバーとして計画している、する必要はありませんこの計画手順を実行するコンピューターが現在ドメインに参加していない場合を除き。
  
ドメインにログオンするには、コンピューターがドメイン メンバー コンピューターをする必要があり、ログオン試行の前に AD DS でユーザー アカウントを作成する必要があります。 さらに、コンピューターを適切なグループ メンバーシップを持つアカウントを使用してドメインに参加する必要があります。

## <a name="bkmk_cachelocation"></a>ホスト型キャッシュのサイズと場所を計画します。

HCS1 にする場所を決定、ホスト型キャッシュ サーバー上のホスト型キャッシュを検索します。 たとえば、ハード ディスク、ボリューム、およびキャッシュを格納するフォルダーの場所を決定します。

さらに、ホスト型キャッシュに割り当てる必要なディスク領域の割合を指定します。

## <a name="bkmk_package"></a>コンテンツ サーバーのパッケージがコピーされる共有を計画します。

コンテンツ サーバーにデータ パッケージを作成したら、する必要がありますにコピー、ネットワーク経由で、共有ホスト型キャッシュ サーバーでします。

フォルダーの場所と、共有フォルダーの共有アクセス許可を計画します。 さらに、WAN 帯域幅が使用するときに他のユーザーが時間中に、コピー操作で消費されないように off\ – ピーク時に、コピー操作を実行する場合は、コンテンツ サーバーは、大量のデータをホストし、作成したパッケージは大きなファイルになります、計画します。 通常の業務の帯域幅。

## <a name="bkmk_prehash"></a>プランの事前ハッシュおよびデータ パッケージのコンテンツ サーバーの作成

コンテンツ サーバーのコンテンツを prehash する前に、フォルダーとデータのパッケージに追加するコンテンツを含むファイルを識別する必要があります。 

さらに、ホスト型キャッシュ サーバーにコピーする前に、データ パッケージを格納するローカル フォルダーの場所を計画する必要があります。

このガイドを続行する、次を参照してください。 [BranchCache ホスト キャッシュ モードの配置](4-Bc-Hcm-Deployment.md)します。