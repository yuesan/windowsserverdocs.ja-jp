---
title: ディスクの管理のトラブルシューティング
description: この記事では、ディスクの管理の問題のトラブルシューティングを行う方法について説明します
ms.date: 12/20/2019
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 7eeb462d31391a228ec0e89afb09673ef14b51cf
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "79323444"
---
# <a name="troubleshooting-disk-management"></a>ディスクの管理のトラブルシューティング

> **適用対象:** Windows 10、Windows 8.1、Windows 7、Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

このトピックでは、ディスクの管理を使用する場合に発生する可能性があるいくつかの一般的な問題と、試していただけるトラブルシューティングの手順を示します。

> [!TIP]
> これらの手順に従っているときにエラーを受け取ったり、何かが正しく機能しなかったりしても慌てないでください。 このトピックでは最初に試していただけることだけを示しています。また、[Microsoft コミュニティ](https://answers.microsoft.com/en-us/windows) サイトの「[ファイル、フォルダー、およびストレージ](https://answers.microsoft.com/en-us/windows/forum/windows_10-files?sort=lastreplydate&dir=desc&tab=All&status=all&mod=&modAge=&advFil=&postedAfter=&postedBefore=&threadType=all&isFilterExpanded=true&tm=1514405359639)」セクションには、対応する可能性のあるさまざまなハードウェアとソフトウェアの構成に関する大量の情報があります。 それでもヘルプが必要な場合は、そこで質問を投稿するか、[Microsoft サポートにお問い合わせください](https://support.microsoft.com/contactus/)。またはハードウェアの製造元にお問い合わせください。

## <a name="how-to-open-disk-management"></a>ディスクの管理を開く方法

難しいことを始める前に、ディスクの管理にまだ移動できていない場合には、次のような簡単な方法で移動できます。

1. タスクバーの検索ボックスに「**コンピューターの管理**」と入力し、 **[コンピューターの管理]** を長押しし (または右クリックし)、 **[管理者として実行]**  >  **[はい]** の順に選択します。
2. [コンピューターの管理] が開いたら、 **[ストレージ]**  >  **[ディスクの管理]** の順に移動します。

## <a name="disks-that-are-missing-or-not-initialized-plus-general-troubleshooting-steps"></a>不足しているディスクまたは初期化されていないディスク、および一般的なトラブルシューティング手順

![初期化する必要がある不明のディスクが示されているディスクの管理。](media/uninitialized-disk.PNG)

**原因**:エクスプローラーに表示されず、 *[初期化されていません]* としてディスクの管理に一覧表示されているディスクがある場合は、有効なディスク署名がディスクにないことが原因として考えられます。 基本的に、これは、ディスクが今までに初期化およびフォーマットされたことがないか、ドライブ フォーマットが何らかの理由で破損していることを意味します。 

また、ディスクでハードウェアの問題やプラグインの問題が発生している可能性もありますが、これについては後の段落で説明します。

**解決策:**    ドライブがまったくの新規で、そこにあるデータを消去して初期化する必要があるだけの場合、解決策は簡単です。「[新しいディスクの初期化](initialize-new-disks.md)」を参照してください。 ただし、お客様が既にこれを試していて、うまくいかなかった可能性があります。 あるいは、ディスクが重要なファイルでいっぱいであり、初期化してディスクを消去したくない場合もあります。

ディスクやメモリ カードが不足したり初期化に失敗したりする原因としてさまざまなことが考えられますが、一般的な原因は、ディスクで障害が発生しているというものです。 障害が発生しているディスクを修正するためにできることは限られていますが、再び機能させられるかどうかを確認するために試すことのできるいくつかの手順を次に示します。 これらの手順のいずれかを実行した後にディスクが機能するようになった場合は、その次の手順は実行せずに、必要に応じてバックアップの更新を行ってください。

1. ディスクの管理でディスクを確認します。 ここに示すように *[オフライン]* と表示される場合は、右クリックして、 **[オンライン]** を選択してみてください。

    ![オフラインと表示されているディスク](media/offline-disk.png)
2. ここに示すように、ディスクがディスクの管理に *[オンライン]* と表示され、 *[正常]* と一覧表示されているプライマリ パーティションを持っている場合、それは良い兆候です。

    ![正常なボリュームを持ちオンラインと示されているディスク](media/healthy-volume.png)
    - パーティションにファイル システムはあるが、ドライブ文字 (たとえば、E:) がない場合は、「[ドライブ文字を変更する](change-a-drive-letter.md)」を参照して、手動でドライブ文字を追加してください。
    - パーティションにファイル システム (NTFS、ReFS、FAT32、または exFAT ではなく RAW として表示) がなく、ディスクが空であることがわかっている場合は、パーティションを長押しして (または右クリックして)、 **[フォーマット]** を選択します。 ディスクをフォーマットするとディスク上のすべてのデータが消去されます。したがって、ディスクからファイルを回復しようとしている場合は、フォーマットを実行せずに、次の手順に進んでください。
    - パーティションが *[未割り当て]* として表示され、パーティションが空であることがわかっている場合は、未割り当てのパーティションを長押し (または右クリック) してから **[新しいシンプル ボリューム]** を選択し、手順に従って空き領域にボリュームを作成します。 パーティションからファイルを回復しようとしている場合は、この操作を行わないでください。代わりに、次の手順に進んでください。

    > [!NOTE]
    > **[EFI システム パーティション]** または **[回復パーティション]** として表示されているすべてのパーティションを無視します。 これらのパーティションは、PC が正常に動作するために必要なとても重要なファイルでいっぱいになっています。 これらは PC を起動したり問題からの回復を支援したりするジョブを実行させるために、そのままにしておくことをお勧めします。
3. 表示されていない外部ディスクがある場合は、そのディスクを取り外し、再び接続してから、 **[アクション]**  >  **[ディスクの再スキャン]** の順に選択します。 
4. PC をシャットダウンし、外部ハード ディスクの電源を切り (電源コードがある外部ディスクの場合)、次に PC とディスクの電源を再び入れます。
    Windows 10 で PC の電源を切るには、[スタート] ボタンを選択し、[電源] ボタンを選択してから、 **[シャットダウン]** を選択します。
5. (ハブではなく) お使いの PC に直接組み込まれている別の USB ポートにディスクを接続します。
    USB ディスクが一部のポートから十分な電力を得られない場合や特定のポートでその他の問題が発生する場合があります。 これは USB ハブでは特に一般的ですが、PC 上のポート間で違いがあることがあるので、異なるポートがいくつかある場合はそれらを試してみてください。
6. 別のケーブルを試してみます。
    関連しないように思われるかもしれませんが、ケーブルの障害は頻繁に起こるので、別のケーブルを使ってディスクを接続してみてください。 デスクトップ PC に内部ディスクがある場合は、ケーブルを切り替える前に、PC のシャットダウンが必要になる可能性があります。詳細については、お使いの PC のマニュアルを参照してください。
7. 問題がないかデバイス マネージャーを確認します。
    [スタート] ボタンを長押しし (または右クリックし)、コンテキスト メニューからデバイス マネージャーを選択します。 横に感嘆符が付いているか、他の問題があるデバイスを探し、そのデバイスをダブルクリックして、状態を読み取ります。

    こちらに[デバイス マネージャーのエラー コード](https://support.microsoft.com/help/310123/error-codes-in-device-manager-in-windows)の一覧があります。ただし、問題のあるデバイスを長押しし (または右クリックし)、 **[デバイスのアンインストール]** を選択し、次に **[アクション]**  >  **[ハードウェア変更のスキャン]** の順に選択する方法も有効な場合があります。

    ![不明の USB デバイスを表示しているデバイス マネージャー](media/device-manager.PNG)
8. ディスクを別の PC に接続します。
    
    ディスクが別の PC で機能しない場合は、お使いの PC ではなく、ディスクで何か問題が発生していることを示しています。 残念なことですが。 「[外部 USB ドライバー エラー "論理ディスク マネージャーがディスクにアクセスするには、それを初期化する必要があります"](https://social.technet.microsoft.com/Forums/windows/en-US/2b069948-82e9-49ef-bbb7-e44ec7bfebdb/forum-faq-external-usb-drive-error-you-must-initialize-the-disk-before-logical-disk-manager-can?forum=w7itprohardware)」には、この他にも試してみることができるいくつかの手順が記載されていますが、[Microsoft コミュニティ](https://answers.microsoft.com/en-us/windows/forum/windows_10-files?sort=lastreplydate&dir=desc&tab=All&status=all&mod=&modAge=&advFil=&postedAfter=&postedBefore=&threadType=all&isFilterExpanded=true&tm=1514405359639) サイトで検索してヘルプを求めるか、お使いのディスクの製造元または [Microsoft サポート](https://support.microsoft.com/contactus/)に問い合わせることをお勧めします。

    どうしても動作させることができない場合は、障害が発生しているディスクからデータの回復を試行できるアプリもあります。またはファイルが本当に重要なものである場合は、データ回復ラボに料金を支払って、それらの回復を試行することができます。 良い方法が見つかったら、下記のコメント セクションからお知らせください。

> [!IMPORTANT]
> ディスクでの障害はかなり頻繁に発生します。したがって、大切なファイルは定期的にバックアップしておくことが重要です。 場合によって表示されなかったりエラーを表示したりするディスクがある場合は、それを、お使いのバックアップ方法を再確認するためのリマインダーと考えてください。 少し遅れていたとしても問題はありません。誰しも同じことを経験してきました。 最適なバックアップ ソリューションは、ご自身が使うものですので、ご自分に合ったものを見つけて、それを使い続けてください。
> 
> [!TIP]
> Windows に組み込まれたアプリを使用してファイルを USB ドライブなどの外部ドライブにバックアップする方法については、[ファイルのバックアップと復元](https://support.microsoft.com/help/17143/windows-10-back-up-your-files)に関するページをご覧ください。 また、お使いの PC からクラウドにファイルを同期する Microsoft OneDrive にファイルを保存することもできます。 お使いのハード ディスクで障害が発生しても、OneDrive に格納されているファイルはすべて OneDrive.com から取得できます。 詳細については、「[PC の OneDrive](https://support.microsoft.com/help/17184/windows-10-onedrive)」をご覧ください。

## <a name="a-basic-or-dynamic-disks-status-is-unreadable"></a>ベーシック ディスクまたはダイナミック ディスクの状態が [読み取り不可] になっている

**原因:**   ベーシック ディスクまたはダイナミック ディスクにアクセスできません。ハードウェア障害、破損、または I/O エラーが発生している可能性があります。 システムのディスク構成データベースのディスク コピーが破損している可能性があります。 **[読み取り不可]** 状態と表示されているディスク上にエラー アイコンが表示されます。

ディスクがスピンアップしている間や、ディスクの管理がシステム上のすべてのディスクを再スキャンしているときにも、ディスクに **[読み取り不可]** 状態と表示される可能性があります。 また場合によっては、ディスクに障害が発生し、回復不能な場合にも、[読み取り不可] と表示されることがあります。 ダイナミック ディスクの場合、 **[読み取り不可]** 状態は、通常、ディスク全体の障害ではなく、ディスクの一部の破損または I/O エラーが原因です。

**解決策:**   ディスクを再スキャンするか、コンピューターを再起動して、ディスクの状態が変化するかどうかを確認します。 また、「[ディスクの状態が "初期化されていません" であるか、ディスクが完全に欠落している](#disks-that-are-missing-or-not-initialized-plus-general-troubleshooting-steps)」に記載されているトラブルシューティング手順も試してください。

## <a name="a-dynamic-disks-status-is-foreign"></a>ダイナミック ディスクの状態が [異形式] になっている

**原因:**   **[異形式]** の状態は、ダイナミック ディスクを別のコンピューター PC からローカル コンピューターに移動したときに発生します。 **[異形式]** 状態と表示されているディスク上に警告アイコンが表示されます。

場合によっては、以前にシステムに接続されていたディスクに **[異形式]** 状態と表示される場合があります。 ダイナミック ディスクの構成データは、すべてのダイナミック ディスク上に保存されているため、すべてのダイナミック ディスクで障害が発生すると、システムがどのディスクを所有しているかに関する情報が失われます。

**解決策:**   ディスク上のデータにアクセスできるように、コンピューターのシステム構成にディスクを追加します。 コンピューターのシステム構成にディスクを追加するには、異形式のディスクをインポートします (ディスクを長押しし (または右クリックし)、 **[形式の異なるディスクのインポート]** をクリック)。 ディスクをインポートすると、異形式ディスク上の既存のボリュームにアクセスできるようになります。 

## <a name="a-dynamic-disks-status-is-online-errors"></a>ダイナミック ディスクの状態が [オンライン (エラー)] になっている

**原因:**  ダイナミック ディスク上の領域で I/O エラーが発生しています。 エラーが発生しているダイナミック ディスクには警告アイコンが表示されます。

**解決策:**   I/O エラーが一時的である場合は、ディスクを再アクティブ化して、 **[オンライン]** 状態に戻します。

## <a name="a-dynamic-disks-status-is-offline-or-missing"></a>ダイナミック ディスクの状態が [オフライン] または [不足] になっている

**原因:**  **オフライン**のダイナミック ディスクは壊れているか、断続的に利用できなくなっている可能性があります。 オフラインのダイナミック ディスクにはエラー アイコンが表示されます。

ディスクの状態が **[オフライン]** で、ディスクの名前が **[不足]** に変更されている場合、ディスクはシステムで最近使用されたが、見つからなくなったか、識別できなくなっています。 不明ディスクは、破損しているか、電源が切られているか、または接続が解除されている可能性があります。

**解決策:** [オフライン] および [不足] のディスクを再びオンライン状態にするには、以下の手順を実行します。

1. ディスク、コントローラー、またはケーブルに関する問題を修復します。 
2. 物理ディスクが電源とコンピューターに接続されており、電源がオンになっていることを確認します。 
3. 次に、 **[ディスクの再アクティブ化]** コマンドを使用してディスクを再びオンラインにします。
4. 「[ディスクの状態が "初期化されていません" であるか、ディスクが完全に欠落している](#disks-that-are-missing-or-not-initialized-plus-general-troubleshooting-steps)」に記載されているトラブルシューティング手順を試してください。
5. ディスクの状態が **[オフライン]** のままで、ディスク名が **[不足]** のままであり、ディスクに修復できない問題があると判断した場合は、ディスクを長押しし (または右クリックし)、 **[ディスクの削除]** をクリックして、システムからディスクを削除することができます。 ただし、ディスクを削除するには、まずそのディスク上のすべてのボリューム (またはミラー) を削除しなければなりません。 ディスク上のミラー ボリュームを残すには、ボリューム全体を削除するのではなく、ミラーを削除します。 ボリュームを削除すると、そのボリューム内の全データが失われます。そのため、ディスク障害が永続的なもので、使用不能であることが確実になるまでは、ディスクを削除しないようにしてください。

**[オフライン] であるが、名前がまだ [ディスク \#] である ([不明] ではない) ディスクを再びオンラインにするには、以下の 1 つ以上の手順を試してください。**

1. ディスクの管理で、ディスクを長押しし (または右クリックし)、 **[ディスクの再アクティブ化]** をクリックして、ディスクをオンラインに戻します。 ディスクの状態が **[オフライン]** のままである場合は、ケーブルとディスク コントローラーを確認し、物理ディスクが正常であることを確認します。 問題を解決してから、ディスクの再アクティブ化をもう一度実行します。 ディスクの再アクティブ化に成功すると、ディスク上のボリュームは自動的に **[正常]** 状態に戻ります。
2. イベント ビューアーで、「No good config copies」などのディスクに関連するエラー イベント ログを確認します。 イベント ログにこのエラーが記録されている場合は、[マイクロソフト製品サポート サービス](https://msdn.microsoft.com/library/aa263468(v=vs.60).aspx)にお問い合わせください。

3. 別のコンピューターにディスクを移動してみます。 別のコンピューターでディスクを **[オンライン]** にすることができる場合、問題の原因は、ディスクを **[オンライン]** にすることができないコンピューター上の構成にある可能性が高くなります。

4. ダイナミック ディスクがある別のコンピューターにディスクを移動してみます。 そのコンピューターでディスクをインポートした後、ディスクが **[オンライン]** にならなかったコンピューターにディスクを戻します。 

## <a name="a-basic-or-dynamic-volumes-status-is-failed"></a>ベーシック ボリュームまたはダイナミック ボリュームの状態が [失敗] になっている

**原因:**   ベーシック ボリュームまたはダイナミック ボリュームを自動的に開始できないか、ディスクが破損しているか、ファイル システムが壊れています。 ディスクまたはファイル システムを修復できない場合、 **[失敗]** 状態はデータが失われることを示します。

**解決策:**

ボリュームがベーシック ボリュームで、 **[失敗]** 状態の場合:

- 基になる物理ディスクが電源とコンピューターに接続されており、電源がオンになっていることを確認します。
- 「[ディスクの状態が "初期化されていません" であるか、ディスクが完全に欠落している](#disks-that-are-missing-or-not-initialized-plus-general-troubleshooting-steps)」に記載されているトラブルシューティング手順を試してください。

ボリュームがダイナミック ボリュームで、 **[失敗]** 状態の場合:

-   基になるディスクがオンライン状態であることを確認します。 そうでない場合は、ディスクを **[オンライン]** 状態に戻します。 これが成功した場合、ボリュームは自動的に再起動し、 **[正常]** 状態に戻ります。 ダイナミック ディスクが **[オンライン]** 状態になっても、ダイナミック ボリュームが **[正常]** 状態に戻らない場合は、ボリュームを手動で再アクティブ化することができます。
-   ダイナミック ボリュームが古いデータを含むミラー ボリュームまたは RAID-5 ボリュームの場合は、ボリュームが存在しているディスクをオンライン状態に戻しても、ボリュームは自動的には再起動されません。 最新のデータが含まれているディスクが切断された場合、(データを同期できるように) それらのディスクを最初にオンラインにします。 それ以外の場合は、ミラー ボリュームまたは RAID-5 ボリュームを再起動し、エラー チェック ツールか Chkdsk.exe を実行してください。
- 「[ディスクの状態が "初期化されていません" であるか、ディスクが完全に欠落している](#disks-that-are-missing-or-not-initialized-plus-general-troubleshooting-steps)」に記載されているトラブルシューティング手順を試してください。

## <a name="a-basic-or-dynamic-volumes-status-is-unknown"></a>ベーシック ボリュームまたはダイナミック ボリュームの状態が [不明] になっている

**原因:**    **[不明]** 状態は、ボリュームのブート セクターが (ウイルスなどによって) 破損していて、ボリューム上のデータにアクセスできなくなっているときに発生します。 **[不明]** 状態は、新しいディスクをインストールしたが、ディスク署名を作成するウィザードを正常に完了していない場合にも発生します。

**解決策:**   ディスクを初期化します。 手順については、「[新しいディスクの初期化](initialize-new-disks.md)」をご覧ください。

## <a name="a-dynamic-volumes-status-is-data-incomplete"></a>ダイナミック ボリュームの状態が [不完全なデータ] になっている

**原因**:マルチディスク ボリュームのディスクの一部を移動しましたが、まだ移動していないディスクがあります。 このボリューム上のデータは、このボリュームを含む残りのディスクを移動し、インポートしない限り破棄されます。

**解決策:**

1. マルチディスク ボリュームを構成するすべてのディスクをこのコンピューターに移動します。
2. ディスクをインポートします。 ディスクを移動してインポートする方法を説明する手順については、「[ディスクを別のコンピューターに移動する](move-disks-to-another-computer.md)」をご覧ください。

マルチディスク ボリュームが不要になった場合は、ディスクをインポートし、そのディスクに新しいボリュームを作成できます。 そのためには、次の操作を実行します。

1. **[失敗]** または **[冗長の失敗]** 状態のボリュームを長押しし (または右クリックし)、 **[ボリュームの削除]** をクリックします。
2. ディスクを長押しし (または右クリックし)、 **[新しいボリューム]** をクリックします。

## <a name="a-dynamic-volumes-status-is-healthy-at-risk"></a>ダイナミック ボリュームの状態が [正常 (危険)] になっている

**原因:**   ダイナミック ボリュームは現在アクセスできますが、基になるダイナミック ディスクで I/O エラーが検出されたことを示しています。 ダイナミック ディスクの一部で I/O エラーが検出された場合、そのディスク上のすべてのボリュームが **[正常 (危険)]** 状態と表示され、ボリューム上に警告アイコンが表示されます。

ボリュームの状態が **[正常 (危険)]** である場合、基になるディスクの状態は通常 **[オンライン (エラー)]** です。

**解決策:**  
1. 基になるディスクを **[オンライン]** 状態に戻します。 ディスクが **[オンライン]** 状態になると、ボリュームは **[正常]** 状態に戻ります。 それでも **[正常 (危険)]** 状態が続く場合は、ディスクの障害が発生している可能性があります。 

2. できるだけ早くデータをバックアップし、ディスクを交換してください。

## <a name="cannot-manage-striped-volumes-using-disk-management-or-diskpart"></a>ディスクの管理や DiskPart を使用してストライプ ボリュームを管理できない

**原因:**    一部の Microsoft 以外のディスク管理製品では、Microsoft 論理ディスク マネージャー (LDM) が高度なディスク管理に置き換えられて、LDM が無効になっている場合があります。

**解決策:**    LDM を無効にした Microsoft 以外のディスク管理ソフトウェアを使用している場合は、その Microsoft 以外のディスク管理ソフトウェアのベンダーに連絡して、ディスク構成の問題をトラブルシューティングするためのサポートや支援について確認する必要があります。

## <a name="disk-management-cannot-start-the-virtual-disk-service"></a>ディスクの管理で仮想ディスク サービスを開始できない

**原因:**   リモート コンピューターで仮想ディスク サービス (VDS) がサポートされていない場合や、Windows ファイアウォールによってブロックされているためにリモート コンピューターへの接続を確立できない場合に、このエラーを受け取る可能性があります。

**解決策:**

1. リモート コンピューターが VDS をサポートしている場合は、VDS 接続を許可するように Windows Defender ファイアウォールを構成できます。 リモート コンピューターが VDS をサポートしていない場合は、リモート デスクトップ接続を使用して接続し、リモート コンピューター上で直接ディスクの管理を実行することができます。
2. VDS をサポートしているリモート コンピューター上のディスクを管理するには、(ディスクの管理を実行している) ローカル コンピューターとリモート コンピューターの両方で、Windows Defender ファイアウォールを構成する必要があります。
3. ローカル コンピューターで、リモート ボリューム管理例外を有効にするように Windows Defender ファイアウォールを構成します。

> [!NOTE]
> リモート ボリューム管理例外には、Vds.exe、Vdsldr.exe、TCP ポート 135 の例外が含まれます。

> [!NOTE]
> ワークグループ内のリモート接続はサポートされていません。 ローカル コンピューターとリモート コンピューターはいずれもドメインのメンバーである必要があります。

関連項目

- [Windows 10 のドライブの空き領域を増やす](https://support.microsoft.com/help/12425/windows-10-free-up-drive-space)」も参照してください