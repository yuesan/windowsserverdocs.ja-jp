---
title: ホスト型キャッシュ サーバーでデータ パッケージをインポートする (省略可能)
description: このガイドでは、Windows Server 2016 と Windows 10 を実行するコンピューターに、ホスト型キャッシュモードで BranchCache を展開する手順について説明します。
manager: brianlic
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: article
ms.assetid: d6159e91-f77c-42ec-9180-14bbb230ad17
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 41bb7f5f0637bd4b1f1bfa3c0451debff58a3e5a
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80318429"
---
# <a name="import-data-packages-on-the-hosted-cache-server-optional"></a>ホスト型キャッシュサーバーにデータパッケージをインポートする \(オプション\)

>適用対象: Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

この手順を使用すると、データパッケージをインポートし、ホスト型キャッシュサーバーにコンテンツを事前に読み込むことができます。

ホスト型キャッシュサーバーにコンテンツを事前にハッシュし、事前に読み込む必要がないため、この手順は省略できます。

コンテンツを事前に読み込む\-ない場合、データは WAN 接続を介してクライアントがダウンロードするときに、自動的にホスト型キャッシュに追加されます。

この手順を実行するには、Administrators グループのメンバーである必要があります。

## <a name="to-import-data-packages-on-the-hosted-cache-server"></a>ホスト型キャッシュサーバーにデータパッケージをインポートするには  

1. サーバーコンピューターで、管理者特権を使用して Windows PowerShell を開きます。

2. 次のコマンドを入力し、– Path パラメーターの値を、データパッケージが格納されているフォルダーの場所に置き換えて、ENTER キーを押します。

    ```  
    Import-BCCachePackage –Path D:\temp\PeerDistPackage.zip
    ```  

3. コンテンツを事前に読み込む複数のホスト型キャッシュサーバーがある場合は、各ホスト型キャッシュサーバーでこの手順を実行します。

このガイドを続行するには、「[クライアントの自動ホスト型キャッシュ検出をサービス接続ポイント別に構成する](10-Bc-Client-By-Scp.md)」を参照してください。
