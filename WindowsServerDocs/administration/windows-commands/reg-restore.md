---
title: reg restore
description: レジストリに保存されたサブキーとエントリを書き込む reg restore コマンドの参照記事です。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a51f1c0c-969b-4b76-930a-c8bb14dea26e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1483fc6998d7b286a81dc3cb1df021afb7e66650
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931039"
---
# <a name="reg-restore"></a>reg restore

書き込みが保存されたサブキーとエントリは、レジストリをバックアップします。

## <a name="syntax"></a>構文

```
reg restore <keyname> <filename>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<keyname>` | 復元するサブキーの完全なパスを指定します。 復元操作は、ローカルコンピューターでのみ機能します。 *Keyname*には、有効なルートキーを含める必要があります。 ローカルコンピューターの有効なルートキーは、 **HKLM**、 **HKCU**、 **HKCR**、 **HKU**、および**HKCC**です。 レジストリキー名にスペースが含まれている場合は、キー名を引用符で囲みます。 |
| `<filename>` | レジストリに書き込まれるコンテンツを含むファイルのパスと名前を指定します。 このファイルは、事前に**reg save**コマンドを使用して作成する必要があり、.hiv 拡張子を持つ必要があります。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- レジストリエントリを編集する前に、 **reg save**コマンドを使用して親サブキーを保存する必要があります。 編集に失敗した場合は、 **reg 復元**操作を使用して元のサブキーを復元できます。

- **Reg 復元**操作の戻り値は次のとおりです。

    | 値 | [説明] |
    |--|--|
    | 0 | 成功 |
    | 1 | 障害 |

### <a name="examples"></a>例

キー、HKLM\Software\Microsoft\ResKit NTRKBkUp.hiv をという名前のファイルを復元し、キーの既存の内容を上書きする、次のように入力します。

```
reg restore HKLM\Software\Microsoft\ResKit NTRKBkUp.hiv
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [reg save コマンド](reg-save.md)
