---
ms.assetid: cd4d4902-dcdf-49dd-8059-82a56bf4b585
title: サーバー認証証明書の秘密キーの部分をエクスポートする
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 7837f1aeb5def401e199bf49d6fd5a204859fc4b
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86965894"
---
# <a name="export-the-private-key-portion-of-a-server-authentication-certificate"></a>サーバー認証証明書の秘密キーの部分をエクスポートする

Active Directory フェデレーションサービス (AD FS) AD FS ファーム内のすべてのフェデレーションサーバーは、 \( \) サーバー認証証明書の秘密キーへのアクセス権を持っている必要があります。 フェデレーションサーバーまたは Web サーバーのサーバーファームを実装する場合は、1つの認証証明書が必要です。 この証明書は、エンタープライズ証明機関の CA によって発行されている必要があり、 \( \) エクスポート可能な秘密キーを持っている必要があります。 サーバー認証証明書の秘密キーは、ファーム内のすべてのサーバーが利用できるように、エクスポート可能である必要があります。  
  
この同じ概念は、ファーム内のすべてのフェデレーションサーバープロキシが同じサーバー認証証明書の秘密キー部分を共有する必要があるという意味で、フェデレーションサーバープロキシファームにも当てはまります。  
  
> [!NOTE]  
> AD FS 管理スナップインは、 \- サービス通信証明書としてのフェデレーションサーバーのサーバー認証証明書を参照します。  
  
このコンピューターが再生する役割に応じて、サーバー認証証明書を秘密キーと共にインストールしたフェデレーションサーバーコンピューターまたはフェデレーションサーバープロキシコンピューターで、この手順を実行します。 手順を完了すると、ファーム内の各サーバーの既定の Web サイトでこの証明書をインポートできるようになります。 詳細については、「[サーバー認証証明書を既定の Web サイトにインポートする](Import-a-Server-Authentication-Certificate-to-the-Default-Web-Site.md)」を参照してください。  
  
この手順を完了するには、ローカル コンピューター上の **Administrators** または同等のメンバーシップが最低限必要です。  適切なアカウントおよびグループメンバーシップの使用方法の詳細については、「[ローカルおよびドメインの既定のグループ](https://go.microsoft.com/fwlink/?LinkId=83477)」を参照してください。   
  
### <a name="to-export-the-private-key-portion-of-a-server-authentication-certificate"></a>サーバー認証証明書の秘密キーの部分をエクスポートするには  
  
1. **スタート**画面で、「**インターネットインフォメーションサービス \( IIS \) Manager**」と入力し、enter キーを押します。  
  
2. コンソール ツリーで、[**コンピューター名**] をクリックします。  
  
3. 中央のウィンドウで、 \- [**サーバー証明書**] をダブルクリックします。  
  
4. 中央のウィンドウで、 \- エクスポートする証明書を右クリックし、[**エクスポート**] をクリックします。  
  
5. [**証明書のエクスポート**] ダイアログボックスで、[.. **.** ] をクリックします。 ボタンを選択します。  
  
6. [**ファイル名**] に「 **C \\ :**<em>nameofcertificate</em>」と入力し、[**開く**] をクリックします。  
  
7. 証明書のパスワードを入力し、確認したら、[**OK**] をクリックします。  
  
8. エクスポートが成功したかどうかを検証するには、指定したファイルが指定した場所に作成されていることを確認します。  
  
   > [!IMPORTANT]  
   > この証明書を新しいサーバー上のローカル証明書ストアにインポートできるように、ファイルを物理メディアに転送すると共に、新しいサーバーへの移送中にそのセキュリティを保護する必要があります。 秘密キーのセキュリティを保護することはきわめて重要です。 このキーが侵害される \( と、組織内およびリソースパートナー組織内のリソースを含む AD FS デプロイ全体のセキュリティ \) が侵害されます。  
  
9. フェデレーション サービスをインストールする前に、新しいサーバー上の証明書ストアにサーバー認証証明書をインポートします。 証明書をインポートする方法の詳細については、「サーバー証明書のインポート \( [http: \/ \/ go.microsoft.com \/ fwlink \/ ?」を参照してください。LinkId \= 108283](https://go.microsoft.com/fwlink/?LinkId=108283) \) 。  
  
## <a name="additional-references"></a>その他のリファレンス  
[チェックリスト:フェデレーション サーバーのセットアップ](Checklist--Setting-Up-a-Federation-Server.md)  
  
[チェックリスト:フェデレーション サーバー プロキシのセットアップ](Checklist--Setting-Up-a-Federation-Server-Proxy.md)  
  
[フェデレーション サーバーの証明書の要件](../design/certificate-requirements-for-federation-servers.md)  
  
[フェデレーション サーバー プロキシの証明書の要件](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807054(v=ws.11))  
  
