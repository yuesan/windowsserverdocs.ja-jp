---
title: subst
description: パスをドライブ文字に関連付ける方法について説明します。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3e69234c-2312-4343-868b-afc1017c622a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 62ba0de33e69998e7d3e343b1e53c1de7e630e10
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721607"
---
# <a name="subst"></a>subst



ドライブ文字をパスに関連付けます。 パラメーターを指定せずに使用する場合 **subst** 仮想ドライブの名前が有効で表示されます。



## <a name="syntax"></a>構文

```
subst [<Drive1>: [<Drive2>:]<Path>] 
subst <Drive1>: /d
```

### <a name="parameters"></a>パラメーター

|パラメーター|[説明]|
|---------|-----------|
|\<Drive1>:|パスに割り当てる仮想ドライブを指定します。|
|[\<Drive2>:]\<パス>|物理ドライブと仮想ドライブに指定するパスを指定します。|
|/d|置き換えられた (仮想) ドライブを削除します。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>Remarks

-   次のコマンドは機能しません。 **subst**コマンドで指定されているドライブでは使用できません。

    **chkdsk**

    **diskcomp**

    **diskcopy**

    **format**

    **label**

    **recover**
-   *ドライブ 1* パラメーターがで指定された範囲内である必要があります、 **リソース** コマンドです。 ない場合は、 **subst** 次のエラー メッセージが表示されます。

    `Invalid parameter - drive1:`

## <a name="examples"></a><a name="BKMK_examples"></a>例

仮想ドライブ Z B:\User\Betty\Forms のパスを作成するには、次のように入力します。
```
subst z: b:\user\betty\forms 
```
完全なパスを入力する代わりに次のように、コロンで後に仮想ドライブの文字を入力してこのディレクトリに移動することができます。
```
z: 
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)