---
title: 電子メール通知を構成する
description: この記事では、電子メール通知の構成方法について説明します。
ms.date: 7/7/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: b80aef85d6f4a1d6bd8c05b56d7c1a12b456d1ed
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "85474189"
---
# <a name="configure-e-mail-notifications"></a>電子メール通知を構成する

> 適用対象: Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2

クォータおよびファイル スクリーンを作成した場合は、ユーザーのクォータ制限が近づいているときや、ユーザーがファイルを保存しようとしたがブロックされた後に、ユーザーに電子メール通知を送信することができます。 記憶域レポートを生成した場合は、特定の受信者にレポートを電子メールで送信することができます。 クォータおよびファイル スクリーン処理イベントを特定の管理者に定期的に通知する場合、または、記憶域レポートを送信する場合は、1 人以上の既定の受信者を構成できます。

このような通知や記憶域レポートを送信するには、電子メール メッセージの転送に使用する SMTP サーバーを指定する必要があります。

## <a name="to-configure-e-mail-options"></a>電子メールのオプションを構成するには、次の手順を実行します。

1. コンソール ツリーで、**[ファイル サーバー リソース マネージャー]** を右クリックし、**[オプションの構成]** をクリックします。 [**ファイル サーバー リソース マネージャーのオプション**] ダイアログ ボックスが開きます。

2. **[電子メールの通知]** タブの **[SMTP サーバー名または IP アドレス]** に、電子メール通知と記憶域レポートを転送する SMTP サーバーのホスト名または IP アドレスを入力します。

3. クォータまたはファイル スクリーン処理イベントを特定の管理者に定期的に通知する場合、または記憶域レポートを電子メールで送信する場合は、**[管理者である既定の受信者]** に各電子メール アドレスを入力します。

   形式を使用 <em>account@domain</em> します。 複数のアカウントはセミコロンで区切ります。

4. ファイル サーバー リソース マネージャーから送信する電子メール通知と記憶域レポートに異なる差出人アドレスを指定するには、**[既定の "差出人" 電子メール アドレス]** に、メッセージに表示する電子メール アドレスを入力します。

5. 設定をテストするには、**[テスト電子メールの送信]** をクリックします。

6. **[OK]** をクリックします。


## <a name="additional-references"></a>その他のリファレンス

-   [ファイル サーバー リソース マネージャーのオプションを設定する](setting-file-server-resource-manager-options.md)