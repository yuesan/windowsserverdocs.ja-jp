---
title: RAS ゲートウェイ GRE トンネルのスループットとパフォーマンス
description: このトピックは、情報技術 (IT) の専門家を対象としており、RAS ゲートウェイの汎用ルーティングカプセル化 (GRE) トンネルに関するスループットパフォーマンス情報を提供します。
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: c051b2ec-de0f-49d1-82b9-5742b259cd7c
ms.author: lizross
author: eross-msft
ms.openlocfilehash: b20f26673cc5f56632717f9889bfd03b81173661
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86961874"
---
# <a name="ras-gateway-gre-tunnel-throughput-and-performance"></a>RAS ゲートウェイ GRE トンネルのスループットとパフォーマンス

>適用対象: Windows Server \( 半期チャネル\)

このトピックでは、 \( \) ソフトウェアで \( \) 定義されていないネットワーク \( SDN ベースのテスト環境における、Windows Server Version 1709 でのリモートアクセスサーバー RAS ゲートウェイ汎用ルーティングカプセル化 GRE のパフォーマンス \) について説明します。

RAS ゲートウェイは、シングルテナントモードまたはマルチテナントモードで使用できるソフトウェアルーターとゲートウェイです。 このトピックでは、フェールオーバークラスタリングを使用したシングルテナントモードの高可用性構成について説明します。 このトピックに記載されている GRE トンネルパフォーマンス統計は、singele テナントモードとマルチテナントモードの両方で、RAS ゲートウェイに対して有効です。

>[!NOTE]
>フェールオーバークラスタリングは、複数のサーバーを1つのフォールトトレラントクラスターにグループ化できるようにする Windows Server の機能です。 詳細については、「[フェールオーバークラスタリング](../../../failover-clustering/failover-clustering-overview.md)」を参照してください。

シングルテナントモードでは、任意のサイズの組織がゲートウェイを外部またはインターネットに \- 接続するエッジ仮想プライベートネットワーク VPN サーバーとしてデプロイでき \( \) ます。 シングルテナントモードでは、物理サーバーまたは仮想マシン VM に RAS ゲートウェイを展開でき \( \) ます。 このトピックで \( \) は、フェールオーバークラスターに構成されている2つの Virtual Machines vm での RAS ゲートウェイの展開について説明します。

>[!IMPORTANT]
>GRE トンネルはカプセル化を提供しますが暗号化は行わないため、GRE で構成された RAS ゲートウェイをインターネットエッジゲートウェイとして使用しないでください。 GRE トンネルを使用した RAS ゲートウェイの最適な使用方法については、 [Windows Server での Gre トンネリング](gre-tunneling-windows-server.md)に関するページを参照してください。

GRE は、インターネットプロトコルのインターネット接続を介して、仮想ポイント \- からポイントへのリンク内のさまざまなネットワークレイヤープロトコルをカプセル化できる軽量なトンネリングプロトコルです \- 。 Microsoft GRE 実装では、IPv4 と IPv6 の両方がカプセル化されています。

詳細については[、ras ゲートウェイに関するトピックの](./ras-gateway.md#bkmk_deploy)「 **Ras ゲートウェイの展開シナリオ**」セクションを参照してください。 

次の図に示すように、このテストシナリオでは、測定されたトラフィックフローが組織のイントラネット2から組織のイントラネット1に移動します。 テナントワークロード Vm は、RAS ゲートウェイを使用して、イントラネット2からイントラネット1にネットワークトラフィックを送信します。

![RAS ゲートウェイ GRE トンネルテストシナリオの概要](../../media/GRE-Tunnel-Perf/Gre-Infrastructure.jpg)

## <a name="test-environment-configuration"></a>テスト環境の構成

このセクションでは、テスト環境と RAS ゲートウェイの構成について説明します。

テスト環境では、 \- 高可用性を実現するために、フェールオーバークラスター内の hyper-v ホストに RAS ゲートウェイ vm が展開されます。

### <a name="hyper-v-host-configuration"></a>Hyper-v \- ホストの構成

2つの Hyper-v \- ホストは、次の方法でテストシナリオをサポートするように構成されています。 

- 2台のデュアル \- ホーム物理コンピューターが Windows Server バージョン1709で構成されています。
- 2台のサーバーそれぞれに2つの物理ネットワークアダプターが接続されています。これらはどちらも、組織のイントラネットのサブネットを表しています。 ネットワークとサポートするハードウェアの両方に 10 GBps の容量があります。
- 物理サーバー上のハイパースレッディングが無効になっています。 これにより、物理 Nic からの最大スループットが得られます。
- Hyper-v \- サーバーの役割は両方のサーバーにインストールされ、2つの外部 Hyper-v \- 仮想スイッチ (物理ネットワークアダプターごとに1つ) を使用して構成されます。
- 両方のサーバーが同じイントラネットに接続されているため、サーバーは相互に通信できます。
- Hyper-v ホストは、 \- イントラネットネットワーク経由でフェールオーバークラスターに構成されます。 

>[!NOTE]
>詳しくは、「[Hyper-V 仮想スイッチの概要](../../../virtualization/hyper-v-virtual-switch/hyper-v-virtual-switch.md)」を参照してください。

### <a name="vm-configuration"></a>VM 構成

2つの Vm は、次の方法でテストシナリオをサポートするように構成されています。

- 各サーバーで、Windows Server バージョン1709を実行している VM がインストールされている。 各 VM には、10個のコアと 8 GB の RAM が構成されています。
- 各 VM は、2つの仮想ネットワークアダプターで構成されます。 1つの仮想ネットワークアダプターがイントラネット1仮想スイッチに接続され、もう一方の仮想ネットワークアダプターがイントラネット2仮想スイッチに接続されています。
- 各 VM には、RAS ゲートウェイがインストールされ、GRE ベースの VPN サーバーとして構成されてい \- ます。
- ゲートウェイ Vm は、フェールオーバークラスターで構成されます。 クラスター化されている場合、1つの VM がアクティブになり、もう一方の vm はパッシブになります。

### <a name="workload-hyper-v-hosts-and-vms"></a>ワークロード \- の Hyper-v ホストと vm

このテストでは、2つのワークロード Hyper-v \- ホストがイントラネットにインストールされ、各ホストに1つの VM がインストールされています。 このテストを独自のテスト環境で複製する場合は、目的に応じて、ワークロードサーバーと Vm をいくつでもインストールできます。

- ワークロードの Hyper-v \- ホストには、組織のイントラネットに接続された1つの物理ネットワークアダプターがインストールされています。
- Hyper-v \- 仮想スイッチでは、各ホスト上に1つの仮想スイッチが作成されます。 スイッチは外部にあり、イントラネットに接続されている1つのネットワークアダプターにバインドされています。
- ワークロード Vm は、2 GB RAM と2コアで構成されます。
- ワークロード Vm にはそれぞれ、イントラネット仮想スイッチに接続されている仮想ネットワークアダプターが1つあります。

### <a name="traffic-generator-tool"></a>Traffic Generator ツール

このテストで使用されているトラフィックジェネレーターツールは、Ctstrの Ic ツールです。 このツールの Git リポジトリはにあり [https://github.com/Microsoft/ctsTraffic](https://github.com/Microsoft/ctsTraffic) ます。

## <a name="ras-gateway-performance"></a>RAS ゲートウェイのパフォーマンス

このセクションの図は、複数の TCP 接続を使用した GRE トンネルスループットのタスクマネージャーの表示を示しています。

GRE RAS ゲートウェイとして構成されているマルチコア Vm で最大 2.0 Gbps のスループットを実現でき \- ます。

### <a name="gre-tunnel-performance-with-multiple-tcp-sessions"></a>複数の TCP セッションを使用した GRE トンネルパフォーマンス

複数の TCP セッションがある場合、CPU 使用率は100% に達し、GRE トンネルの最大スループットは 2.0 Gbps です。

次の図は、両方の RAS ゲートウェイ Vm の CPU 使用率を示しています。 アクティブ VM、RAS ゲートウェイ VM #1 が左側にあり、パッシブ VM、RAS ゲートウェイ VM #2 が右側にあります。

![タスクマネージャーでのゲートウェイ VM の CPU 使用率](../../media/GRE-Tunnel-Perf/Gre-Tunnel-01.jpg)

次の図は、RAS ゲートウェイ Vm でのイーサネットネットワークスループットを示しています。 アクティブ VM、RAS ゲートウェイ VM #1 が左側にあり、パッシブ VM、RAS ゲートウェイ VM #2 が右側にあります。

![タスクマネージャーでのゲートウェイ VM イーサネットネットワークスループット](../../media/GRE-Tunnel-Perf/Gre-Tunnel-02.jpg)


### <a name="gre-tunnel-performance-with-one-tcp-connection"></a>1つの TCP 接続を使用した GRE トンネルのパフォーマンス

テスト構成を複数の TCP セッションから1つの TCP セッションに変更すると、1つの CPU コアのみが RAS ゲートウェイ Vm の最大容量に到達します。

GRE トンネルの最大スループットは 400-500 Mbps です。

次の図は、両方の RAS ゲートウェイ Vm の CPU 使用率を示しています。 アクティブ VM、RAS ゲートウェイ VM #1 が左側にあり、パッシブ VM、RAS ゲートウェイ VM #2 が右側にあります。

![タスクマネージャーでのゲートウェイ VM の CPU 使用率](../../media/GRE-Tunnel-Perf/Gre-Tunnel-03.jpg)


次の図は、RAS ゲートウェイ Vm でのイーサネットネットワークスループットを示しています。 アクティブ VM、RAS ゲートウェイ VM #1 が左側にあり、パッシブ VM、RAS ゲートウェイ VM #2 が右側にあります。

![タスクマネージャーでのゲートウェイ VM イーサネットネットワークスループット](../../media/GRE-Tunnel-Perf/Gre-Tunnel-04.jpg)

RAS ゲートウェイのパフォーマンスの詳細については、「[ソフトウェア定義ネットワークにおける Hnv ゲートウェイのパフォーマンスチューニング](../../../administration/performance-tuning/subsystem/software-defined-networking/hnv-gateway-performance.md)」を参照してください。
