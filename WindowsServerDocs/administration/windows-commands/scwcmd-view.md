---
title: Scwcmd ビュー
description: 参照記事 * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7995959a-d93e-4865-a6a0-2ab18c2bb47f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cbae5f3d0157424fb9281d47cdf126bf106447c3
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932616"
---
# <a name="scwcmd-view"></a>Scwcmd: ビュー

> 適用対象: Windows Server 2012 R2、Windows Server 2012

指定した .xsl 変換を使用して .xml ファイルを表示します。 このコマンドは、さまざまなビューを使用して、.xml ファイルのセキュリティ構成ウィザード (SCW) を表示するために役立ちます。

## <a name="syntax"></a>構文

```
scwcmd view /x:<Xmlfile.xml> [/s:<Xslfile.xsl>]
```

#### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|x\<Xmlfile.xml>|表示する .xml ファイルを指定します。 このパラメーターを指定する必要があります。|
|/s\<Xslfile.xsl>|レンダリング プロセスの一環として、.xml ファイルに適用する .xsl 変換を指定します。 このパラメーターは、SCW の .xml ファイルでは省略可能です。 ときに、 **ビュー** コマンドを使用して、SCW の .xml ファイルを表示、読み込み、指定された .xml ファイルを正しい既定の変換に自動的に試みます。 .Xsl 変換が指定されている場合、変換が .xsl トランス フォームと同じディレクトリに .xml ファイルであることを前提として記述する必要があります。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>注釈

Scwcmd.exe は Windows Server 2008 R2、Windows Server 2008 または Windows Server 2003 を実行するコンピューターにできるだけです。

## <a name="examples"></a>例

表示するには Policyfile.xml Policyview.xsl 変換を使用して、次のように入力します。
```
scwcmd view /x:C:\policies\Policyfile.xml /s:C:\viewers\Policyview.xsl
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)