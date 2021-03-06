---
title: wscript
description: Wscript のリファレンス記事。ユーザーは、さまざまなオブジェクトモデルを使用してタスクを実行するさまざまな言語でスクリプトを実行できる環境を提供します。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2fbaf193-cdbd-414c-84c9-bb5720f84c29
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 08/21/2018
ms.openlocfilehash: a07ad9b33000b17f5c6f41835a1a36531b3945af
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86958884"
---
# <a name="wscript"></a>wscript



Windows スクリプトホストは、さまざまなオブジェクトモデルを使用してタスクを実行するさまざまな言語のスクリプトをユーザーが実行できる環境を提供します。

## <a name="syntax"></a>構文

```
wscript [<scriptname>] [/b] [/d] [/e:<engine>] [{/h:cscript|/h:wscript}] [/i] [/job:<identifier>] [{/logo|/nologo}] [/s] [/t:<number>] [/x] [/?] [<ScriptArguments>]
```

#### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|スクリプト名|スクリプトファイルのパスとファイル名を指定します。|
|/b|アラート、スクリプトエラー、入力プロンプトを表示しないバッチモードを指定します。 これは **/i**とは逆です。|
|/d|デバッガーを起動します。|
|/e|スクリプトの実行に使用するエンジンを指定します。 これにより、カスタムファイル名拡張子を使用するスクリプトを実行できます。 /E パラメーターを指定しない場合は、登録されているファイル名拡張子を使用するスクリプトのみを実行できます。 たとえば、次のコマンドを実行しようとするとします。<br>```cscript test.admin```<br>このエラーメッセージが表示されます。入力エラー: ファイル拡張子のスクリプトエンジンがありません。管理者です。<br>非標準のファイル名拡張子を使用する利点の1つは、誤ってスクリプトをダブルクリックして、実際には実行したくないものを実行することです。 <br>この場合、管理者のファイル名拡張子と VBScript の間に永続的な関連付けは作成されません。 . Admin ファイル名拡張子を使用するスクリプトを実行するたびに、/e パラメーターを使用する必要があります。|
|/h: cscript|スクリプトを実行するための既定のスクリプトホストとして**cscript.exe**を登録します。|
|/h: wscript|スクリプトを実行するための既定のスクリプトホストとして**wscript.exe**を登録します。 これは、 **/h**オプションを省略した場合の既定値です。|
|/i|アラート、スクリプトエラー、および入力プロンプトを表示する対話モードを指定します。</br>これは既定値であり、 **/b**と逆になります。|
|/ジョブ (\<identifier>|**Wsf**スクリプトファイル内の*識別子*によって識別されるジョブを実行します。|
|/ロゴ|スクリプトを実行する前に、Windows スクリプトホストバナーをコンソールに表示することを指定します。</br>これは、既定値であり、 **/nologo**と逆になります。|
|/nologo|スクリプトを実行する前に、Windows スクリプトホストバナーを表示しないように指定します。 これは、**ロゴ**の反対です。|
|/s|現在のユーザーの現在のコマンドプロンプトオプションを保存します。|
|/t: \<number>|スクリプトを実行できる最長時間を秒単位で指定します。 最大32767秒を指定できます。</br>既定では、時間制限はありません。|
|/x|デバッガーでスクリプトを開始します。|
|ScriptArguments|スクリプトに渡される引数を指定します。 各スクリプト引数の前にはスラッシュ (/) を付ける必要があります。|
|/?|コマンド プロンプトでヘルプを表示します。|

## <a name="remarks"></a>注釈

-   このタスクを実行するときは、管理資格情報は必要ありません。 そのため、セキュリティ対策として、このタスクは管理資格情報のないユーザーとして実行することを検討してください。
-   コマンド プロンプトを開くには、**スタート**画面で、「**cmd**」と入力し、**[コマンド プロンプト]** をクリックします。
-   各パラメーターは省略可能です。ただし、スクリプトを指定せずにスクリプトの引数を指定することはできません。 スクリプトまたはスクリプトの引数を指定しない場合、 **wscript.exe**に [ **Windows スクリプトホストの設定**] ダイアログボックスが表示されます。このダイアログボックスを使用して、ローカルコンピューター上で**wscript.exe**実行されるすべてのスクリプトのグローバルなスクリプトプロパティを設定できます。
-   **/T**パラメーターを指定すると、タイマーを設定することによって、スクリプトの過剰な実行を防ぐことができます。 時間が指定された値を超えると、 **wscript**はスクリプトエンジンを中断し、プロセスを終了します。
-   Windows スクリプトファイルは、通常、次のファイル名拡張子のいずれかに**なります。 wsf**、 **.vbs**、 **.js**。
-   拡張子が関連付けられていないスクリプトファイルをダブルクリックすると、[**ファイルを開くアプリケーション**の選択] ダイアログボックスが表示されます。 [ **Wscript** ] または [ **cscript**] を選択し、[この**ファイルの種類を開くには常にこのプログラムを使用する**] を選択します。 これにより、このファイルの種類のファイルの既定のスクリプトホストとして**wscript.exe**または**cscript.exe**が登録されます。
-   個々のスクリプトのプロパティを設定できます。 詳細については、「 [Windows スクリプトホストの概要](/previous-versions/windows/it-pro/windows-server-2003/cc738350(v=ws.10))」を参照してください。
-   Windows スクリプトホストでは **、wsf**スクリプトファイルを使用できます。 各**wsf**ファイルは、複数のスクリプトエンジンを使用して複数のジョブを実行できます。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
