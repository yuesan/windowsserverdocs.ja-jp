---
title: msiexec
description: Msiexec コマンドのリファレンス記事。コマンドラインから Windows インストーラーのインストール、変更、操作を実行するための手段を提供します。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 122eb0ce-ecbc-4909-a52a-15c3413619af
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b1224d4dfeefd850dcc29e523972351b8cdd9778
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86956874"
---
# <a name="msiexec"></a>msiexec

コマンドラインから Windows インストーラーのインストール、変更、操作を実行するための手段を提供します。

## <a name="install-options"></a>インストール オプション

インストールパッケージを起動するためのインストールの種類を設定します。

### <a name="syntax"></a>構文

```
msiexec.exe [/i][/a][/j{u|m|/g|/t}][/x] <path_to_package>
```

#### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ------- | -------- |
| /i | 通常のインストールを指定します。 |
| /a | 管理インストールを指定します。 |
| /ju | 現在のユーザーに製品を提供します。 |
| /jm | 製品をすべてのユーザーに提供します。 |
| /j/g | 提供パッケージによって使用される言語識別子を指定します。 |
| /j/t | 提供パッケージに変換を適用します。 |
| /x | パッケージをアンインストールします。 |
| `<path_to_package>` | インストールパッケージファイルの場所と名前を指定します。 |

#### <a name="examples"></a>例

通常のインストールプロセスを使用して、C: ドライブから*example.msi*という名前のパッケージをインストールするには、次のように入力します。

```
msiexec.exe /i "C:\example.msi"
```

## <a name="display-options"></a>表示オプション

ターゲット環境に応じて、インストールプロセス中にユーザーに表示される内容を構成できます。 たとえば、手動でインストールするためにパッケージをすべてのクライアントに配布する場合は、完全な UI が必要です。 ただし、ユーザーの操作を必要としないグループポリシーを使用してパッケージを配置する場合は、UI は必要ありません。

### <a name="syntax"></a>構文

```
msiexec.exe /i <path_to_package> [/quiet][/passive][/q{n|b|r|f}]
```

#### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ------- | -------- |
| `<path_to_package>` | インストールパッケージファイルの場所と名前を指定します。 |
| スイッチを | 非表示モードを指定します。これは、ユーザー操作が不要であることを意味します。 |
| /passive | 無人モードを指定します。これは、インストール時に進行状況バーのみを表示することを意味します。 |
| /qn | インストールプロセス中に UI が存在しないことを指定します。 |
| /qn + | 最後のダイアログボックスを除いて、インストール処理中に UI が存在しないことを指定します。 |
| /qb | インストールプロセス中に基本的な UI があることを指定します。 |
| /qb + | インストール処理中に基本的な UI があることを指定します。最後には最後のダイアログボックスも含まれます。 |
| /qr | インストールプロセス中の UI エクスペリエンスの縮小を指定します。 |
| /qf | インストールプロセス中の完全な UI エクスペリエンスを指定します。 |

##### <a name="remarks"></a>注釈

- インストールがユーザーによって取り消された場合、モーダルボックスは表示されません。 **Qb +!** または、 **[キャンセル**] ボタンを非表示**にします**。

#### <a name="examples"></a>例

通常のインストールプロセスと UI を使用せずにパッケージ*C:\example.msi*をインストールするには、次のように入力します。

```
msiexec.exe /i "C:\example.msi" /qn
```

## <a name="restart-options"></a>再起動オプション

インストールパッケージによってファイルが上書きされる場合、または使用中のファイルを変更しようとする場合は、インストールが完了する前に再起動が必要になることがあります。

### <a name="syntax"></a>構文

```
msiexec.exe /i <path_to_package> [/norestart][/promptrestart][/forcerestart]
```

#### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ------- | -------- |
| `<path_to_package>` | インストールパッケージファイルの場所と名前を指定します。 |
| /norestart | インストールが完了した後、デバイスの再起動を停止します。 |
| /promptrestart | 再起動が必要かどうかをユーザーに確認します。 |
| /forcerestart | インストールの完了後にデバイスを再起動します。 |

#### <a name="examples"></a>例

パッケージ*C:\example.msi*をインストールするには、最後に再起動せずに通常のインストールプロセスを使用して、次のように入力します。

```
msiexec.exe /i "C:\example.msi" /norestart
```

## <a name="logging-options"></a>[ログ オプション]

インストールパッケージをデバッグする必要がある場合は、パラメーターを設定して、特定の情報を含むログファイルを作成できます。

### <a name="syntax"></a>構文

```
msiexec.exe [/i][/x] <path_to_package> [/L{i|w|e|a|r|u|c|m|o|p|v|x+|!|*}] <path_to_log>
```

#### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ------- | -------- |
| /i | 通常のインストールを指定します。 |
| /x | パッケージをアンインストールします。 |
| `<path_to_package>` | インストールパッケージファイルの場所と名前を指定します。 |
| /li | ログ記録をオンにし、出力ログファイルにステータスメッセージを含めます。 |
| /lw | ログ記録をオンにし、出力ログファイルに致命的ではない警告を含めます。 |
| /le | ログ記録をオンにし、すべてのエラーメッセージを出力ログファイルに含めます。 |
| /la | ログ記録をオンにし、出力ログファイルでアクションが開始された時刻に関する情報を含めます。 |
| /lr | ログ記録をオンにし、出力ログファイルにアクション固有のレコードを含めます。 |
| /lu | ログ記録をオンにし、出力ログファイルにユーザー要求情報を含めます。 |
| /lc | ログ記録をオンにし、出力ログファイルに初期 UI パラメーターを含めます。 |
| /lm | ログ記録をオンにし、出力ログファイルにメモリ不足または致命的な終了情報を含めます。 |
| /lo | ログ記録をオンにし、ディスク領域不足のメッセージを出力ログファイルに含めます。 |
| /lp | ログ記録をオンにし、出力ログファイルにターミナルのプロパティを含めます。 |
| /lp | ログ記録をオンにし、出力ログファイルにターミナルのプロパティを含めます。 |
| /lv | ログ記録をオンにし、出力ログファイルに詳細出力を含めます。 |
| /lp | ログ記録をオンにし、出力ログファイルにターミナルのプロパティを含めます。 |
| /lx | ログ記録をオンにし、出力ログファイルに追加のデバッグ情報を含めます。 |
| /l + | ログ記録をオンにして、既存のログファイルに情報を追加します。 |
| /l! | ログ記録をオンにし、各行をログファイルにフラッシュします。 |
| /l | ログ記録をオンにし、詳細情報 (**/lv**) または追加のデバッグ情報 (**/lx**) を除くすべての情報をログに記録します。 |
| `<path_to_logfile>` | 出力ログファイルの場所と名前を指定します。 |

#### <a name="examples"></a>例

パッケージ*C:\example.msi*をインストールするには、すべてのログ情報 (詳細出力を含む) を使用して通常のインストールプロセスを実行し、出力ログファイルを*C:\package.log*に格納するには、次のように入力します。

```
msiexec.exe /i "C:\example.msi" /L*V "C:\package.log"
```

## <a name="update-options"></a>更新のオプション

インストールパッケージを使用して、更新プログラムを適用または削除することができます。

### <a name="syntax"></a>構文

```
msiexec.exe [/p][/update][/uninstall[/package<product_code_of_package>]] <path_to_package>
```

#### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ------- | -------- |
| /p | 修正プログラムをインストールします。 サイレントモードでインストールする場合は、REINSTALLMODE プロパティを*ecmus*に設定して、*すべて*に再インストールする必要もあります。 それ以外の場合、パッチはターゲットデバイスにキャッシュされた MSI のみを更新します。 |
| /update | [更新プログラムのインストール] オプション。 複数の更新プログラムを適用している場合は、セミコロン (;) で区切る必要があります。 |
| /package | 製品をインストールまたは構成します。 |

#### <a name="examples"></a>例

```
msiexec.exe /p "C:\MyPatch.msp"
msiexec.exe /p "C:\MyPatch.msp" /qb REINSTALLMODE="ecmus" REINSTALL="ALL"
msiexec.exe /update "C:\MyPatch.msp"
```

```
msiexec.exe /uninstall {1BCBF52C-CD1B-454D-AEF7-852F73967318} /package {AAD3D77A-7476-469F-ADF4-04424124E91D}
```

最初の GUID は patch GUID、もう1つはパッチが適用された MSI 製品コードです。

## <a name="repair-options"></a>修復オプション

このコマンドを使用すると、インストールされているパッケージを修復できます。

### <a name="syntax"></a>構文

```
msiexec.exe [/f{p|o|e|d|c|a|u|m|s|v}] <product_code>
```

#### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ------- | -------- |
| /fp | ファイルが見つからない場合にパッケージを修復します。 |
| /fo | ファイルが見つからない場合、または古いバージョンがインストールされている場合に、パッケージを修復します。 |
| /fe | ファイルが見つからない場合、または同等またはそれ以前のバージョンがインストールされている場合は、パッケージを修復します。 |
| /fd | ファイルが見つからない場合、または別のバージョンがインストールされている場合に、パッケージを修復します。 |
| /fc | ファイルが見つからない場合、またはチェックサムが計算された値と一致しない場合は、パッケージを修復します。 |
| /fa | すべてのファイルを強制的に再インストールします。 |
| /fu | すべての必要なユーザー固有のレジストリエントリを修復します。 |
| /fm | 必要なコンピューター固有のレジストリエントリをすべて修復します。 |
| /fs | 既存のショートカットをすべて修復します。 |
| /fc | ソースから実行し、ローカルパッケージを再キャッシュします。 |

#### <a name="examples"></a>例

修復する MSI 製品コードに基づいてすべてのファイルを強制的に再インストールするには、 *{AAD3D77A-7476-469F-ADF4-04424124E91D}* を入力します。

```
msiexec.exe /fa {AAD3D77A-7476-469F-ADF4-04424124E91D}
```

## <a name="set-public-properties"></a>パブリックプロパティの設定

このコマンドを使用してパブリックプロパティを設定できます。 使用可能なプロパティとその設定方法の詳細については、「[パブリックプロパティ](/windows/win32/msi/public-properties)」を参照してください。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [Msiexec.exe のコマンドラインオプション](/windows/win32/msi/command-line-options)

- [標準インストーラーのコマンドラインオプション](/windows/win32/msi/standard-installer-command-line-options)
