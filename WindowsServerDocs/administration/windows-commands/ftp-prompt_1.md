---
title: ftp prompt
description: プロンプトモードのオンとオフを切り替える ftp prompt コマンドのリファレンス記事です。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 930df39b-45c4-4e0b-bfe2-1d1963be817a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dad75921ce6878d5a255edf92c5877238ffe899a
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86957594"
---
# <a name="ftp-prompt"></a>ftp prompt

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

プロンプトモードのオンとオフを切り替えます。 既定では、プロンプトモードはオンになっています。 プロンプトモードが有効になっている場合、ftp コマンドは複数のファイル転送中にプロンプトを表示して、ファイルを選択して取得または保存できるようにします。

> [!NOTE]
> プロンプトモードがオフになっている場合は、 [ftp の mget](ftp-mget.md)コマンドと[ftp mput](ftp-mput_1.md)コマンドを使用してすべてのファイルを転送できます。

## <a name="syntax"></a>構文

```
prompt
```

### <a name="examples"></a>例

プロンプトモードのオンとオフを切り替えるには、次のように入力します。

```
prompt
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
