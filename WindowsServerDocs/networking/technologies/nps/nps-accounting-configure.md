---
title: ネットワーク ポリシー サーバー アカウンティングを構成する
description: このトピックでは、テキスト ファイルと SQL Server の Windows Server 2016 でネットワーク ポリシー サーバーのログ記録に関する情報を提供します。
manager: dougkim
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: dfde2e21-f3d5-41e8-8492-cb3f0d028afb
ms.author: pashort
author: shortpatti
ms.date: 05/25/2018
ms.openlocfilehash: c732a9f42d942ad579468d1dd15d30324d6fea87
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59839703"
---
# <a name="configure-network-policy-server-accounting"></a>ネットワーク ポリシー サーバー アカウンティングを構成する

ネットワーク ポリシー サーバーのログ記録の 3 つの種類があります\(NPS\):

- **イベントのログ記録**します。 監査とトラブルシューティングの接続の試行に主に使用されます。 NPS イベントを NPS コンソールで、NPS のプロパティを取得することでログを構成できます。

- **ユーザー認証およびアカウンティング要求をローカル ファイルにログ記録**します。 接続の分析と課金のために主に使用します。 としても便利なセキュリティ調査ツールを攻撃を受けた後悪意のあるユーザーのアクティビティを追跡する手段が提供するため。 アカウンティング構成ウィザードを使用してローカル ファイル ログを構成することができます。

- **準拠している Microsoft SQL Server の XML データベースにユーザー認証およびアカウンティング要求を記録**します。 1 つのデータ ソースとする NPS を実行している複数のサーバーを許可するために使用します。 また、リレーショナル データベースを使用する利点を提供します。 SQL サーバーのログ記録を構成するには、アカウンティング構成ウィザードを使用します。

## <a name="use-the-accounting-configuration-wizard"></a>アカウンティングの構成ウィザードを使用

アカウンティング構成ウィザードを使用すると、次の 4 つのアカウンティング設定を構成できます。

- **SQL のログインのみ**します。 この設定を使用すると、NPS に接続し、アカウンティング データを SQL server に送信を許可する SQL Server へのデータ リンクを構成できます。 さらに、ウィザードでは、データベースが SQL の NPS サーバーのログ記録と互換性があることを確認する SQL Server でデータベースを構成できます。
- **テキスト ログのみ**します。 この設定を使用すると、アカウンティング データをテキスト ファイルに記録するように NPS を構成できます。
- **ログ記録を並列**します。 この設定を使用して、SQL Server データ リンクとデータベースを構成できます。 NPS は、テキスト ファイル、および SQL Server データベースに同時に記録するために、テキスト ファイル ログを構成することもできます。 
- **SQL ログのバックアップ**します。 この設定を使用して、SQL Server データ リンクとデータベースを構成できます。 さらに、SQL Server ログに失敗した場合、NPS が使用するテキスト ファイル ログを構成することができます。

これらの設定だけでなく SQL Server のログ記録とテキスト ログの両方、NPS は引き続きログが失敗した場合、接続要求を処理するかどうかを指定できます。 これを指定することができます、**エラー アクション セクションのログ記録**ローカル ファイル ログのプロパティ、SQL server ログ プロパティ、およびアカウンティングの構成ウィザードを実行しているときにします。

### <a name="to-run-the-accounting-configuration-wizard"></a>アカウンティング構成ウィザードを実行するには

アカウンティングの構成ウィザードを実行するには、次の手順を完了します。

1. NPS コンソールまたは NPS Microsoft 管理コンソール (MMC) スナップインを開きます。
2. コンソール ツリーで、クリックして**アカウンティング**します。
3. 詳細ウィンドウで [**アカウンティング**、] をクリックして**アカウンティングを構成**。

## <a name="configure-nps-log-file-properties"></a>NPS ログ ファイルのプロパティを構成します。

リモート認証ダイヤルイン ユーザー サービス (RADIUS) のユーザー認証要求、アクセス許可メッセージ、アクセス拒否メッセージ、アカウンティング要求および応答、アカウンティングと定期的に実行するように、ネットワーク ポリシー サーバー (NPS) を構成します。ステータスの更新。 アカウンティング データを格納するログ ファイルを構成するのには、この手順を使用することができます。

ログ ファイルの解釈に関する詳細については、次を参照してください。[解釈 NPS データベース形式のログ ファイル](https://technet.microsoft.com/library/cc771748.aspx)します。

ログ ファイルがハード ドライブの情報を入力することを防ぐためには、システム パーティションから別のパーティションに保存することを強くお勧めします。 NPS のアカウンティングを構成する方法の詳細を次に示します。

- コレクションのログ ファイルのデータを別のプロセスで送信するには、名前付きパイプに書き込むように NPS を構成できます。 名前付きパイプを使用するログ ファイルのフォルダーを設定\\. \pipe または\\ComputerName\pipe します。 名前付きパイプ サーバー プログラムと呼ばれる名前付きパイプを作成する\\.\pipe\iaslog.log データを受け入れるようにします。 作成、新しいログ ファイルを選択しない (無制限のファイルのサイズ) で、ローカル ファイルのプロパティ ダイアログ ボックスで名前付きパイプを使用するとします。

- ログ ファイルのディレクトリは、%systemdrive%、%systemroot% や %windir% など、(ユーザー変数) ではなくシステム環境変数を使用して作成できます。 など、環境変数、%windir% を使用して、次のパスがサブフォルダー \System32\Logs にシステム ディレクトリにあるログ ファイルを検索 (つまり、%windir%\System32\Logs\)します。

- ログ ファイルの形式の切り替えを作成する新しいログは発生しません。 変更時にアクティブになっているファイルが 2 つの形式の組み合わせを含むログ ファイルの形式を変更する場合 (最初のログのレコードには、以前の形式が使用およびログの最後のレコードには、新しい形式になります)。

- RADIUS アカウンティングは、完全なハード ディスク ドライブまたはその他の原因により失敗した場合、NPS では、ユーザーがネットワーク リソースにアクセスするを妨げて接続要求の処理が停止します。

- NPS は、ローカル ファイルにログ記録に加え、またはの代わりに、Microsoft® SQL Server™ データベースに記録する機能を提供します。

メンバーシップ、 **Domain Admins**グループはこの手順を実行するために必要な最小値。


### <a name="to-configure-nps-log-file-properties"></a>NPS ログ ファイルのプロパティを構成するには

1. NPS コンソールまたは NPS Microsoft 管理コンソール (MMC) スナップインを開きます。
2. コンソール ツリーで、クリックして**アカウンティング**します。
3. 詳細ウィンドウで [**ログ ファイルのプロパティ**、] をクリックして**ログ ファイルのプロパティの変更**。 **ログ ファイルのプロパティ** ダイアログ ボックスが表示されます。
4. **ログ ファイルのプロパティ**の**設定**] タブの [ **、次の情報をログ**アカウンティングの目標を達成するための十分な情報をログに選択することを確認します。 たとえば、ログは、セッションの関連付けを実行する場合に、すべてのチェック ボックスを選択します。
5. **失敗したアクションのログ記録**を選択します**ログが失敗した、接続要求を破棄**NPS ログ ファイルがいっぱいになったりを何らかの理由がアクセス要求メッセージの処理を停止する場合。 NPS ログが失敗した場合、接続要求を処理を続行する場合では、このチェック ボックスはオンされません。
6. **ログ ファイルのプロパティ**ダイアログ ボックスで、をクリックして、**ログ ファイル**タブ。
7. **ログ ファイル**] タブの [**ディレクトリ**、NPS ログ ファイルを格納する場所を入力します。 既定の場所は、systemroot\System32\LogFiles フォルダーです。<br>内のステートメントの完全なパスを指定しないかどうかは**ログ ファイル ディレクトリ**既定のパスを使用します。 たとえば、入力した**NPSLogFile**で**ログ ファイル ディレクトリ**、%systemroot%\system32\npslogfile にファイルがあります。
8. **形式**、 をクリックして**DTS 準拠**します。 場合は、代わりに、従来のファイル形式を選択できますなど**ODBC\(レガシ\)** または**IAS\(レガシ\)** します。<br>**ODBC**と**IAS**レガシ ファイルの種類は、NPS は、その SQL Server データベースに送信される情報のサブセットを含めることができます。 **DTS 準拠**ファイルの種類の XML 形式では、NPS を使用して、SQL Server データベースにデータをインポートする XML 形式と同じです。 そのため、 **DTS 準拠**ファイル形式は、NPS の標準の SQL Server データベースにデータより効率的かつ完全転送を提供します。
9. **新しいログ ファイル作成**、指定した間隔で新しいログ ファイルの開始、使用する間隔 をクリックするように NPS を構成します。
    - 大量のトランザクションとアクティビティのログ記録は、次のようにクリックします。**毎日**します。
    - 低いトランザクション ボリュームとログ記録アクティビティは、次のようにクリックします。**毎週**または**毎月**します。
    - のすべてのトランザクションを 1 つのログ ファイルを保存 をクリックして**Never\(無制限のファイル サイズ\)** します。
    - 各ログ ファイルのサイズを制限するには、次のようにクリックします。**ログ ファイルがこのサイズに達したとき**、し、新しいログの作成後、ファイル サイズを入力します。 既定のサイズは、10 メガバイト (MB です)。
10. ハード ディスクが容量の近くにある場合は、新しいログ ファイルのディスク領域を作成する古いログ ファイルを削除するように NPS を実行する場合に、ことを確認します。**とディスクは、古いログ ファイルの完全な削除**が選択されています。 このオプションは使用できません、ただし場合の値**新しいログ ファイル作成**は**Never\(無制限のファイル サイズ\)** します。 また、最も古いログ ファイルが現在のログ ファイルの場合は削除されません。

## <a name="configure-nps-sql-server-logging"></a>NPS の SQL Server ログを構成します。

Microsoft SQL Server を実行しているローカルまたはリモートのデータベースに RADIUS アカウンティング データをログには、この手順を使用することができます。

>[!NOTE]
>NPS に送信される XML ドキュメントとしてアカウンティング データを書式設定、 **report_event** NPS で指定した SQL Server データベースでストアド プロシージャ。 SQL Server が正常に機能するログ記録、という名前のストアド プロシージャが必要**report_event**受信したり、NPS からの XML ドキュメントを解析する SQL Server データベースにします。

Domain Admins、またはそれと同等のメンバーシップは、この手順を実行するために必要な最小値です。

### <a name="to-configure-sql-server-logging-in-nps"></a>NPS に SQL Server ログを構成するには

1. NPS コンソールまたは NPS Microsoft 管理コンソール (MMC) スナップインを開きます。
2. コンソール ツリーで、クリックして**アカウンティング**します。
3. 詳細ウィンドウで [ **SQL Server ログ プロパティ**、] をクリックして**SQL Server ログ プロパティの変更**します。 **SQL Server ログ プロパティ** ダイアログ ボックスが表示されます。
4. **、次の情報をログ**、ログに記録情報を選択します。 
    - すべてのアカウンティング要求をログに次のようにクリックします。**アカウンティング要求**します。
    - 認証要求をログ、クリックを**認証要求**します。
    - 定期的なアカウンティングの状態をログに次のようにクリックします。**定期的なアカウンティングの状態**します。
    - 中間のアカウンティング要求などの定期的な状態がログに次のようにクリックします。**定期的なステータス**します。
5. NPS および SQL Server を実行しているサーバーの間で許可される同時セッションの数を構成するには、数値を入力**同時セッションの最大数**します。
6. SQL Server データ ソースを構成する**SQL サーバーのログ記録**、 をクリックして**構成**します。 **データ リンク プロパティ** ダイアログ ボックスが表示されます。 **接続** タブで、次を指定します。 
    - データベースが格納されているサーバーの名前を指定するには、入力またはで名前を選択**を選択するか、サーバー名を入力**します。
    - サーバーにログオンに使用する認証方法を指定するには、次のようにクリックします。**統合セキュリティを使用して Windows NT**します。 または、をクリックして**特定のユーザー名とパスワードを使用して、** での資格情報を入力し、**ユーザー名**と**パスワード**します。
    - 空白のパスワードを許可する をクリックして**空白のパスワード**します。
    - パスワードを保存するには、次のようにクリックします。**パスワードを保存する**します。
    - SQL Server を実行しているコンピューター上に接続するデータベースを指定する をクリックして**サーバー上のデータベースを選択します。**、し、一覧からデータベース名を選択します。
7. NPS と SQL Server 間の接続をテストするには、クリックして**接続のテスト**します。 クリックして**OK**を閉じる**データ リンク プロパティ**します。
8. **失敗したアクションのログ記録**を選択します**フェールオーバー用のテキスト ファイルのログ記録を有効にする**NPS に SQL Server ログに失敗した場合に、テキスト ファイル ログを続行するかどうか。 
9. **失敗したアクションのログ記録**を選択します**ログが失敗した、接続要求を破棄**NPS ログ ファイルがいっぱいになったりを何らかの理由がアクセス要求メッセージの処理を停止する場合。 NPS ログが失敗した場合、接続要求を処理を続行する場合では、このチェック ボックスはオンされません。

## <a name="ping-user-name"></a>Ping のユーザー名

一部の RADIUS プロキシ サーバーとネットワーク アクセス サーバーに定期的に、NPS がネットワーク上に存在することを確認 (ping 要求と呼ばれます) の認証およびアカウンティング要求を送信します。 こうした ping 要求には、架空のユーザー名が含まれます。 NPS では、これらの要求を処理するとき、イベントおよびアカウンティング ログになる有効なレコードを追跡するのにはより難しく、アクセス拒否記録が格納されます。

レジストリ エントリを構成するとき**ユーザー名を ping**NPS で他のサーバーに対して ping 要求でユーザー名の値のレジストリ エントリの値に一致します。 A**ユーザー名を ping**レジストリ エントリは、RADIUS プロキシ サーバーとネットワーク アクセス サーバーによって送信される架空のユーザー名 (または、ユーザー名のパターン、変数を使用して、架空のユーザー名と一致する) を指定します。 NPS が一致する ping 要求を受信すると、**ユーザー名を ping**レジストリ エントリの値、NPS は、要求を処理することがなく認証要求を拒否します。 NPS では、イベント ログを解釈する容易に任意のログ ファイルでは、架空のユーザー名に関連するトランザクションは記録されません。

**ユーザー名を ping**が既定でインストールされていません。 追加する必要があります**ユーザー名を ping**をレジストリにします。 レジストリ エディターを使用してレジストリにエントリを追加できます。

>[!CAUTION]
>レジストリを正しく編集しないと、システムが正常に動作しなくなる場合があります。 レジストリを変更する前に、コンピューター上の重要なデータのバックアップを作成する必要があります。

### <a name="to-add-ping-user-name-to-the-registry"></a>Ping user-name をレジストリに追加するには

Ping user-name はローカルの Administrators グループのメンバーによって、文字列値として次のレジストリ キーに追加できます。

`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\IAS\Parameters`

- **名前**: `ping user-name`
- **型**: `REG_SZ`
- **データ**:*ユーザー名*

>[!TIP]
>1 つ以上のユーザー名を示すために、**ユーザー名を ping**値には、DNS 名にワイルドカード文字を含めるなどの名前パターンを入力します**データ**します。