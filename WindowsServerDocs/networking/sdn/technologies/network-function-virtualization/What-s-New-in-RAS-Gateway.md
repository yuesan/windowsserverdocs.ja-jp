---
title: RAS ゲートウェイの新機能
description: このトピックを使用すると、マルチ テナントとボーダー ゲートウェイ プロトコル (BGP) Windows Server 2016 での対応のルーターは、RAS ゲートウェイは、ソフトウェア ベースの新機能について説明します。
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 709cb192-313a-47b5-954e-eb5f6fee51a7
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 5cc7d8bab3f2783750dbd723da745b1df3c2e462
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59863023"
---
# <a name="whats-new-in-ras-gateway"></a>RAS ゲートウェイの新機能

>適用対象:Windows Server 2016 の Windows Server (半期チャネル)

このトピックを使用すると、マルチ テナントとボーダー ゲートウェイ プロトコル (BGP) Windows Server 2016 での対応のルーターは、RAS ゲートウェイは、ソフトウェア ベースの新機能について説明します。 RAS ゲートウェイのマルチ テナントの BGP ルーターは、クラウド サービス プロバイダー (Csp) や、HYPER-V ネットワーク仮想化を使用して複数のテナント仮想ネットワークをホストしている企業向けです。  
  
> [!NOTE]  
> Windows Server 2012 R2 では、RAS ゲートウェイは RRAS ゲートウェイの名前します。System Center Virtual Machine Manager では、RAS ゲートウェイの名前は Windows Server ゲートウェイ。  
  
このトピックは次のセクションで構成されます。  
  
-   [サイト対サイト接続オプション](#bkmk_s2s)  
  
-   [ゲートウェイ プール](#bkmk_pools)  
  
-   [ゲートウェイ プールの拡張性](#bkmk_gps)  
  
-   [ゲートウェイ プールの M+N 冗長性](#bkmk_m)  
  
-   [ルート Reflector](#bkmk_rr)  
  
## <a name="bkmk_s2s"></a>サイト対サイト接続オプション  
RAS ゲートウェイでは、3 種類の VPN サイト対サイト接続できるようになりました。インターネット キー交換バージョン 2 (IKEv2) サイト対サイト仮想プライベート ネットワーク (VPN)、レイヤー 3 (L3) VPN、および Generic Routing Encapsulation (GRE) トンネルの数します。  
  
GRE の詳細については、次を参照してください。 [Windows Server 2016 の GRE トンネリング](../../../../remote/remote-access/ras-gateway/gre-tunneling-windows-server.md)します。  
  
## <a name="bkmk_pools"></a>ゲートウェイ プール  
Windows Server 2016 では、さまざまな種類のゲートウェイ プールを作成できます。 ゲートウェイ プールでは、RAS ゲートウェイのインスタンスを多く含むし、物理および仮想ネットワーク間のネットワーク トラフィックをルーティングします。 ゲートウェイ プールは、個々 のゲートウェイの機能 - インターネット キー交換バージョン 2 (IKEv2) のいずれかを実行できるサイト対サイト仮想プライベート ネットワーク (VPN)、レイヤー 3 (L3) VPN、および汎用ルーティング カプセル化 (GRE) トンネルの数、またはプールは、これらのすべてを実行できます関数と混在のプールとして機能します。  
  
インフラストラクチャの要件に基づいて必要なすべてのロジックを使用してゲートウェイ プールを作成することができます。 たとえば、次の特性のいずれかに基づくゲートウェイ プールを作成できます。  
  
-   トンネルの種類 (IKEv2 VPN、L3 VPN、GRE VPN)  
  
-   容量  
  
-   冗長性レベル (テナントの課金プランに基づいて信頼性)  
  
-   顧客用にカスタマイズされた分離  
  
詳細については、次を参照してください。 [RAS ゲートウェイの高可用性](RAS-Gateway-High-Availability.md)します。  
  
## <a name="bkmk_gps"></a>ゲートウェイ プールの拡張性  
簡単にスケールできますゲートウェイ プール アップまたはスケール ダウンを追加または、プール内のゲートウェイ Vm の削除します。 ゲートウェイの追加や削除がプールによって提供されるサービスを妨害しません。 追加し、ゲートウェイの全体のプールを削除することができます。  
  
詳細については、次を参照してください。 [RAS ゲートウェイの高可用性](RAS-Gateway-High-Availability.md)します。  
  
## <a name="bkmk_m"></a>ゲートウェイ プールの M+N 冗長性  
すべてのゲートウェイ プールでは、冗長化の M と N です。 つまりは 'active ゲートウェイ仮想マシン (Vm) の数がスタンバイ ゲートウェイ Vm 数は' n ' でバックアップします。 M+N 冗長性を提供するより柔軟に RAS ゲートウェイを展開するときに必要な信頼性レベルを決定します。 Windows Server 2012 R2 でのみ構成オプションがアクティブの RAS ゲートウェイ VM あたり 1 つだけのスタンバイ RAS ゲートウェイを使用するのではなく、必要な数のスタンバイ Vm を構成できます。 ネットワーク コント ローラーのゲートウェイの Service Manager の機能は、スタンバイの RAS ゲートウェイ VM の容量を使用して、アクティブな RAS ゲートウェイ VM は障害が発生したり、接続を失った信頼性の高いフェールオーバーを提供する効率的にします。  
  
詳細については、次を参照してください。 [RAS ゲートウェイの高可用性](RAS-Gateway-High-Availability.md)します。  
  
## <a name="bkmk_rr"></a>ルート Reflector  
ボーダー ゲートウェイ プロトコル (BGP) ルート リフレクターが、RAS ゲートウェイを使用して含まれており、ルーター間のルートの同期に必要な BGP フル メッシュ トポロジの代替を提供します。 フル メッシュの同期では、すべての BGP ルーターは、ルーティング トポロジ内の他のすべてのルーターで接続する必要があります。 ルート Reflector を使用して、ただし、ルート Reflector は、すべての BGP クライアント、ルートの同期を簡略化およびネットワーク トラフィックの減少と呼ばれる、その他のルーターに接続している唯一のルーターが。 ルート Reflector は、すべてのルートを学習、最適なルートを計算し、その BGP クライアントへの最適なルートを再分配します。  
  
Windows Server 2016 では、RAS ゲートウェイの 1 つ以上の VM で終了する個々 のテナントのリモート アクセスのトンネルを構成できます。 これにより柔軟性の向上の RAS ゲートウェイ VM の 1 つを満たすことができない状況に直面した場合に、クラウド サービス プロバイダーのテナント接続の帯域幅要件をすべて。  
  
ただし、この機能は、ルートの管理の複雑さを増加し、テナントのリモート サイトとクラウド データ センター内の仮想リソース間のルートの有効な同期について説明します。 接続で複数の RAS ゲートウェイにテナントを提供することでは、各テナントのサイトが別のルーティングの近隣ノードがあるが、エンタープライズの最後に構成における複雑さが増大も導入されています。  
  
コントロール プレーンで BGP ルート Reflector は、これらの問題に対処し、エンタープライズ テナント、CSP 内部ファブリックの展開を透明します。 RAS ゲートウェイに含まれており、ネットワーク コント ローラーと統合されている BGP ルート Reflector に関する重要な点を次に示します。  
  
-   ソフトウェアによるネットワーク制御の展開で、ルート Reflector は、RAS ゲートウェイと、ネットワーク コント ローラーの間のコントロール平面上に位置する論理エンティティです。 ただしには参加データ プレーンのルーティングします。  
  
-   データ センターに新しいテナントを追加するとネットワーク コント ローラーはルート Reflector として RAS ゲートウェイの最初のテナントを自動的に構成します。  
  
-   各テナントは、対応するルート Reflector を備え、そのテナントに関連付けられている RAS ゲートウェイ Vm のいずれかに存在します。  
  
-   テナント ルート Reflector は、すべてのテナントに関連付けられている RAS ゲートウェイ Vm のルート Reflector として機能します。 RAS ゲートウェイのルート Reflector 以外のテナント ゲートウェイとは、ルート Reflector クライアントです。 ルート Reflector は、実際のデータ パスのルーティングを実行できるようにルート Reflector のすべてのクライアント間のルートの同期を実行します。  
  
-   A ルート Reflector は、RAS ゲートウェイが構成されているルート reflector サービスを提供しません。  
  
-   A ルート Reflector は、テナントのエンタープライズ サイトへの対応するエンタープライズ ルートとネットワーク コント ローラーを更新します。 これにより、テナントの仮想ネットワークをエンド ツー エンドのデータ パスのアクセスに必要な HYPER-V ネットワーク仮想化ポリシーを構成するネットワーク コント ローラーができます。  
  
-   BGP ルーティングを使用してカスタマー アドレス空間で、企業のお客様、RAS ゲートウェイのルート Reflector は、対応するテナントのサイトのすべての唯一の外部 (eBGP) の BGP 近隣ノードです。 これは、エンタープライズ テナントのトンネルの終了ポイントに関係なく当てはまります。 つまり、データ センターは、CSP でどの RAS ゲートウェイの VM に関係なく、テナント サイトのサイト対サイト VPN トンネルを終了、テナントのすべてのサイトの eBGP ピアはルート Reflector です。  
  
詳細については、次を参照してください。 [RAS ゲートウェイ展開アーキテクチャ](RAS-Gateway-Deployment-Architecture.md)コメント トピックでは、Internet Engineering Task Force (IETF) 要求[RFC 4456 BGP ルートのリフレクション。代わりにフル メッシュ内部 BGP (IBGP)](https://tools.ietf.org/html/rfc4456)します。  
  
