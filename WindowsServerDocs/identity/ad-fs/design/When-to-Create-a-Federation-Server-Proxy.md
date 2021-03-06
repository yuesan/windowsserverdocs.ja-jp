---
ms.assetid: aa20c8b3-7f01-4165-8b73-92642bff9676
title: フェデレーション サーバー プロキシを作成する状況
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 13ca7d49e8044273c9f40e58c06e705e758c68bf
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858485"
---
# <a name="when-to-create-a-federation-server-proxy"></a>フェデレーション サーバー プロキシを作成する状況

組織でフェデレーションサーバープロキシを作成すると、Active Directory フェデレーションサービス (AD FS) \(AD FS\) 展開にセキュリティ層が追加されます。 次のような場合に、組織の境界ネットワークにフェデレーションサーバープロキシを展開することを検討してください。  
  
-   外部クライアントコンピューターがフェデレーションサーバーに直接アクセスできないようにします。 境界ネットワークにフェデレーションサーバープロキシを展開することで、フェデレーションサーバーを効果的に分離して、外部クライアントコンピューターの代理として機能するフェデレーションサーバープロキシ経由で企業ネットワークにログインしているクライアントコンピューターからのみアクセスできるようにします。 フェデレーション サーバー プロキシは、トークンの生成に使用される秘密キーにアクセスしません。 詳細については、次を参照してください。 [フェデレーション サーバー プロキシを配置する場所](Where-to-Place-a-Federation-Server-Proxy.md)します。  
  
-   Windows 統合認証を使用して企業ネットワークからアクセスしているユーザーではなく、インターネットからのユーザーに対して、使用中の\-サインインを区別するための便利な方法を提供します。 フェデレーションサーバープロキシは、インターネットクライアントコンピューターから資格情報またはホーム領域の詳細を収集します。これには、フェデレーションサーバープロキシに格納されているページ\) のログオン、ログアウト、および id プロバイダーの検出 \(ます。  
  
    これに対して、企業ネットワークからのクライアントコンピューターでは、フェデレーションサーバーの構成に基づいて異なるエクスペリエンスが発生します。 企業ネットワークフェデレーションサーバーは、多くの場合、Windows 統合認証用に構成されています。これにより、企業ネットワーク上のユーザーにシームレスなサインイン\-が提供されます。  
  
フェデレーションサーバープロキシが組織内で果たす役割は、フェデレーションサーバープロキシをアカウントパートナー組織に配置するか、リソースパートナー組織に配置するかによって異なります。 たとえば、アカウントパートナーの境界ネットワークにフェデレーションサーバープロキシを配置する場合、その役割は、ブラウザークライアントからユーザー資格情報を収集することです。 フェデレーションサーバープロキシは、リソースパートナーの境界ネットワークに配置されると、セキュリティトークン要求をリソースフェデレーションサーバーにリレーし、そのアカウントパートナーによって提供されるセキュリティトークンに応答して組織のセキュリティトークンを生成します。  
  
詳細については、「 [Review the Role of the Federation Server Proxy in the Account Partner](Review-the-Role-of-the-Federation-Server-Proxy-in-the-Account-Partner.md) 」と「 [Review the Role of the Federation Server Proxy in the Resource Partner](Review-the-Role-of-the-Federation-Server-Proxy-in-the-Resource-Partner.md)」を参照してください。  
  
## <a name="how-to-create-a-federation-server-proxy"></a>フェデレーション サーバー プロキシの作成方法  
フェデレーションサーバープロキシは、AD FS フェデレーションサーバープロキシ構成ウィザードまたは Fsconfig .exe コマンド\-ラインツールのいずれかを使用して作成できます。 これを行う方法については、「 [Configure a Computer for the Federation Server Proxy Role](../../ad-fs/deployment/Configure-a-Computer-for-the-Federation-Server-Proxy-Role.md)」を参照してください。  
  
フェデレーション サーバー プロキシの展開に必要なすべての前提条件を設定する方法の詳細については、「 [Checklist: Setting Up a Federation Server Proxy](../../ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server-Proxy.md)」を参照してください。  
  
## <a name="see-also"></a>参照
[Windows Server 2012 での AD FS 設計ガイド](AD-FS-Design-Guide-in-Windows-Server-2012.md)
