---
title: doskey
description: 以前に入力したコマンドラインコマンドを再呼び出しし、コマンドラインを編集し、マクロを作成する、doskey コマンドと Doskey.exe のリファレンス記事です。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4874fd43-d5ea-45f3-ae24-388ae925ed76
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4a92c9e1d6ffe1f8d7ace5500179697b2a00df1b
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85930553"
---
# <a name="doskey"></a>doskey

は Doskey.exe を呼び出します。これにより、以前に入力したコマンドラインコマンドを再呼び出し、コマンドラインを編集し、マクロを作成します。

## <a name="syntax"></a>構文

```
doskey [/reinstall] [/listsize=<size>] [/macros:[all | <exename>] [/history] [/insert | /overstrike] [/exename=<exename>] [/macrofile=<filename>] [<macroname>=[<text>]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| /reinstall | Doskey.exe の新しいコピーをインストールし、コマンド履歴バッファーをクリアします。 |
| /listsize =`<size>` | 履歴バッファー内のコマンドの最大数を指定します。 |
| /マクロ | すべての**doskey**マクロの一覧を表示します。 /マクロでリダイレクトシンボル () を使用して `>` 、リストをファイルにリダイレクトすることができ **/macros**ます。 **/マクロ**は、 **/m**に省略できます。 |
| /マクロ: すべて | すべての実行可能ファイルの**doskey**マクロを表示します。 |
| マクロ`<exename>` | *Exename*によって指定された実行可能ファイルの**doskey**マクロが表示されます。 |
| /history | メモリに格納されているすべてのコマンドを表示します。 /History でリダイレクトシンボル () を使用して、 `>` リストをファイルにリダイレクトすることができます。 **/history** **/History**は、 **/h**として省略できます。 |
| /挿入 | 入力した新しいテキストを古いテキストで挿入することを指定します。 |
| /overstrike | 新しいテキストが古いテキストを上書きすることを指定します。 |
| /exename =`<exename>` | **Doskey**マクロを実行するプログラム (つまり、実行可能ファイル) を指定します。 |
| /マクロファイル =`<filename>` | インストールするマクロを含むファイルを指定します。 |
| `<macroname>`=[`<text>`] | *テキスト*で指定されたコマンドを実行するマクロを作成します。 *MacroName*マクロに割り当てる名前を指定します。 *Text*記録するコマンドを指定します。 *テキスト*を空白のままにした場合、割り当てられたコマンドの*MacroName*はクリアされます。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- プログラムデバッガーやファイル転送プログラム (FTP) など、特定の文字ベースの対話型プログラムは、自動的に Doskey.exe を使用します。 Doskey.exe を使用するには、プログラムがコンソールプロセスであり、バッファーされた入力を使用する必要があります。 プログラムキーの割り当ては、 **doskey**キーの割り当てをオーバーライドします。 たとえば、プログラムが関数に対して F7 キーを使用している場合、ポップアップウィンドウで**doskey**コマンド履歴を取得することはできません。

- Doskey.exe を使用して現在のコマンドラインを編集することはできますが、プログラムのコマンドプロンプトからコマンドラインオプションを使用することはできません。 プログラムを開始する前に、 **doskey**コマンドラインオプションを実行する必要があります。 プログラム内で Doskey.exe を使用すると、そのプログラムのキー割り当てが優先され、一部の Doskey.exe 編集キーが機能しない可能性があります。

- Doskey.exe では、開始または繰り返しを行う各プログラムのコマンド履歴を保持できます。 プログラムのプロンプトで前のコマンドを編集し、プログラム用に作成された**doskey**マクロを開始することができます。 同じコマンドプロンプトウィンドウからプログラムを終了して再起動すると、前のプログラムセッションのコマンド履歴が使用可能になります。

- コマンドを呼び出すには、Doskey.exe を開始した後で、次のいずれかのキーを使用できます。

  | Key | 説明 |
  | --- | ----------- |
  | ↑ | 表示される前に使用したコマンドを取り消します。 |
  | ↓ | 表示されたコマンドの後に使用したコマンドを取り消します。 |
  | PageUp | 現在のセッションで使用した最初のコマンドを呼び出します。 |
  | PageDown | 現在のセッションで使用していた最新のコマンドを呼び出します。 |

- 次の表に、 **doskey**の編集キーとその機能を示します。

  | キーまたはキーの組み合わせ | 説明 |
  | ---------------------- | ----------- |
  | ← | 挿入ポイントを1文字前に移動します。 |
  | → | 挿入ポイントを1文字前に移動します。 |
  | Ctrl + ← | 挿入ポイントを1ワード左に移動します。 |
  | Ctrl + → | 挿入ポイントを1ワード前に移動します。 |
  | ホーム | カーソル位置を行の先頭に移動します。 |
  | End | カーソル位置を行の末尾に移動します。 |
  | ESC | 表示からコマンドをクリアします。 |
  | F1 | テンプレート内の列の1文字を、コマンドプロンプトウィンドウの同じ列にコピーします。 (テンプレートは、入力した最後のコマンドが格納されているメモリバッファーです)。 |
  | F2 | F2 キーを押した後に入力する次のキーを、テンプレート内で前方に検索します。 Doskey.exe によって、指定した文字までのテンプレートからテキストが挿入されます。 |
  | F3 | テンプレートの残りの部分をコマンドラインにコピーします。 Doskey.exe は、コマンドラインでの挿入ポイントによって示される位置に対応するテンプレート内の位置から文字のコピーを開始します。 |
  | F4 | F4 キーを押した後に入力した文字が次に出現する位置までの、現在の挿入位置からのすべての文字を削除します。 |
  | F5 | テンプレートを現在のコマンドラインにコピーします。 |
  | F6 | 現在の挿入ポイントの位置に、ファイルの終端文字 (CTRL + Z) を配置します。 |
  | F7 | メモリに格納されているこのプログラムのすべてのコマンドをダイアログボックスに表示します。 上方向キーと下方向キーを使用して目的のコマンドを選択し、ENTER キーを押してコマンドを実行します。 コマンドの前に並んでいる番号をメモし、この数値を F9 キーと組み合わせて使用することもできます。 |
  | Alt + F7 | 現在の履歴バッファーのメモリに格納されているすべてのコマンドを削除します。 |
  | F8 | 現在のコマンドの文字で始まる履歴バッファー内のすべてのコマンドを表示します。 |
  | F9 | 履歴バッファーのコマンド番号の入力を求め、指定した番号に関連付けられたコマンドを表示します。 Enter キーを押してコマンドを実行します。 すべての数値とそれに関連付けられたコマンドを表示するには、F7 キーを押します。 |
  | Alt + F10 | すべてのマクロ定義を削除します。 |

- 挿入キーを押すと、テキストを置き換えずに、既存のテキストの途中で**doskey**コマンドラインにテキストを入力できます。 ただし、ENTER キーを押すと、Doskey.exe によってキーボードが**置換**モードに戻ります。 **挿入モードに**戻るには、もう一度 insert キーを押す必要があります。

- 挿入キーを使用して、あるモードから別のモードに変更すると、挿入ポイントの形状が変わります。

- プログラムで Doskey.exe がどのように動作するかをカスタマイズし、そのプログラムの**doskey**マクロを作成する場合は、Doskey.exe を変更してプログラムを起動するバッチプログラムを作成できます。

- Doskey.exe を使用して、1つまたは複数のコマンドを実行するマクロを作成できます。 次の表に、マクロを定義するときにコマンド操作を制御するために使用できる特殊文字を示します。

  | 文字 | 説明 |
  |---------- | ----------- |
  | `$G` または `$g` | 出力をリダイレクトします。 これらの特殊文字のいずれかを使用して、画面ではなく、デバイスまたはファイルに出力を送信します。 この文字は、output () のリダイレクトシンボルに相当し `>` ます。 |
  | `$G$G` または `$g$g` | ファイルの末尾に出力を追加します。 これらの2つの文字のいずれかを使用して、ファイル内のデータを置き換えるのではなく、既存のファイルに出力を追加します。 これらの2つの文字は、output () の追加リダイレクトシンボルに相当し `>>` ます。 |
  | `$L` または `$l` | 入力をリダイレクトします。 これらの特殊文字のいずれかを使用して、キーボードからではなく、デバイスまたはファイルからの入力を読み取ります。 この文字は、input () のリダイレクトシンボルに相当し `<` ます。 |
  | `$B` または `$b` | マクロ出力をコマンドに送信します。 これらの特殊文字は、パイプとを使用することと同じです `(` `*` 。 |
  | `$T` または `$t` | コマンドを区切ります。 **Doskey**コマンドラインでマクロまたは型コマンドを作成するときに、これらの特殊文字のいずれかを使用してコマンドを区切ります。 これらの特殊文字は、コマンドラインでアンパサンド () を使用することと同じです `&` 。 |
  | `$$` | ドル記号 () を指定し `$` ます。 |
  | `$1`行い`$9` | マクロを実行するときに指定する任意のコマンドライン情報を表します。 を使用した特殊文字 `$1` `$9` は、マクロを実行するたびにコマンドラインで異なるデータを使用できるようにするバッチパラメーターです。 `$1` **Doskey**コマンド内の文字は、 `%1` バッチプログラムの文字に似ています。 |
  | `$*` | マクロ名を入力するときに指定するすべてのコマンドライン情報を表します。 特殊文字 `$*` は、からのバッチパラメーターに似た置換可能なパラメーターですが `$1` `$9` 、1つの重要な違いがあります。マクロ名をマクロで置換した後にコマンドラインで入力するすべてのもの。 `$*` |

- マクロを実行するには、最初の位置から開始して、コマンドプロンプトでマクロ名を入力します。 マクロがを使用して定義されている場合、またはでバッチパラメーターを使用している場合は、 `$*` `$1` `$9` スペースを使用してパラメーターを区切ります。 バッチプログラムから**doskey**マクロを実行することはできません。

- 特定のコマンドを特定のコマンドラインオプションと共に使用する場合は、コマンドと同じ名前のマクロを作成できます。 マクロまたはコマンドを実行するかどうかを指定するには、次のガイドラインに従います。

  - マクロを実行するには、コマンドプロンプトでマクロ名を入力します。 マクロ名の前にスペースを追加しないでください。

  - コマンドを実行するには、コマンドプロンプトで1つまたは複数のスペースを挿入し、コマンド名を入力します。

### <a name="examples"></a>例

マクロおよび **/history**コマンドラインオプション**は、マクロ**とコマンドを保存するバッチプログラムを作成する場合に便利です。 たとえば、現在のすべての**doskey**マクロを格納するには、次のように入力します。

```
doskey /macros > macinit
```

Macinit に格納されているマクロを使用するには、次のように入力します。

```
doskey /macrofile=macinit
```

最近使用したコマンドを含む Tmp.bat という名前の batch プログラムを作成するには、次のように入力します。

```
doskey /history> tmp.bat
```

複数のコマンドを含むマクロを定義するには、次のようにを使用し `$t` てコマンドを区切ります。

```
doskey tx=cd temp$tdir/w $*
```

前の例では、TX マクロは現在のディレクトリを Temp に変更し、ディレクトリの一覧をワイド表示形式で表示します。 Tx オプションを実行するときに、マクロの末尾にを使用して、 `$*` 他のコマンドラインオプションを**dir**に追加することができます。

次のマクロでは、新しいディレクトリ名にバッチパラメーターを使用しています。

```
doskey mc=md $1$tcd $1
```

マクロは、新しいディレクトリを作成し、現在のディレクトリから新しいディレクトリに変更します。

上記のマクロを使用して、 *Books*という名前のディレクトリを作成し、変更するには、次のように入力します。

```
mc books
```

*Ftp.exe*と呼ばれるプログラムの**doskey**マクロを作成するには、次のように、 **/exename**を含めます。

```
doskey /exename=ftp.exe go=open 172.27.1.100$tmget *.TXT c:\reports$tbye
```

上記のマクロを使用するには、FTP を開始します。 FTP プロンプトで、次のように入力します。

```
go
```

FTP では、 **open**、 **mget**、および**bye**コマンドを実行します。

すばやく無条件にディスクをフォーマットするマクロを作成するには、次のように入力します。

```
doskey qf=format $1 /q /u
```

ドライブ A でディスクをすばやく無条件にフォーマットするには、次のように入力します。

```
qf a:
```

*Vlist*というマクロを削除するには、次のように入力します。

```
doskey vlist =
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
