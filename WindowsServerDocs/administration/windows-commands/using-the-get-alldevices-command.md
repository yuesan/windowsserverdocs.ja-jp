---
title: 取得-AllDevices
description: すべての事前設定されたコンピューターの Windows 展開サービスのプロパティを表示する、get AllDevices のリファレンス記事。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5824b3d2-2df1-4ed6-a289-e6c47c13fea2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b5eae53c2dcd39a7f3587f4c3c6bf96d4782ea05
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85935219"
---
# <a name="get-alldevices"></a>取得-AllDevices

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

すべての事前設定されたコンピューターの Windows 展開サービス プロパティを表示します。 事前登録されたコンピューターとは、active directory ドメインサービスのコンピューターアカウントにリンクされている物理コンピューターのことです。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Get-AllDevices [/forest:{Yes | No}] [/ReferralServer:<Server name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/forest: {Yes &#124; No}]|Windows 展開サービスがフォレスト全体またはローカル ドメインでコンピューターを返すかどうかを指定します。 既定の設定は **いいえ**, 、ローカル ドメイン内のコンピューターのみが返されることを意味します。|
|[/ReferralServer:<Server name>]|指定されたサーバーの事前登録されているコンピューターのみを返します。|
## <a name="examples"></a>例
すべてのコンピューターを表示するには、次のいずれかを入力します。
```
wdsutil /Get-AllDevices
wdsutil /verbose /Get-AllDevices /forest:Yes /ReferralServer:MyWDSServer
```
## <a name="additional-references"></a>その他の参照情報
- [コマンドライン構文のキー](command-line-syntax-key.md) 
[サブコマンド: デバイス](subcommand-set-device.md) 
 の設定[デバイスの追加コマンド](using-the-add-device-command.md) 
 の使用[Get デバイスコマンドの使用](using-the-get-device-command.md)
