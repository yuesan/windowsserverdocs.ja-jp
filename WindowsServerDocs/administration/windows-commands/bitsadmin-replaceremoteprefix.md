---
title: bitsadmin replaceremoteprefix
description: Bitsadmin replaceremoteprefix コマンドの参照記事。必要に応じて、ジョブ内のすべてのファイルのリモート URL を*oldprefix*から*newprefix*に変更します。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d0e0abb1-bdb4-4c74-abbc-16c809f5fd81
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e2453ac4c223baa049980578c81d9bc6539baac7
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927979"
---
# <a name="bitsadmin-replaceremoteprefix"></a>bitsadmin replaceremoteprefix

必要に応じて、ジョブ内のすべてのファイルのリモート URL を*oldprefix*から*newprefix*に変更します。

## <a name="syntax"></a>構文

```
bitsadmin /replaceremoteprefix <job> <oldprefix> <newprefix>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| oldprefix | 既存の URL プレフィックス。 |
| newprefix | 新しい URL プレフィックス。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブ内のすべてのファイルのリモート URL をに変更するには、をからに変更し *http://stageserver* *http://prodserver* ます。

```
bitsadmin /replaceremoteprefix myDownloadJob http://stageserver http://prodserver
```

## <a name="additional-information"></a>関連情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
