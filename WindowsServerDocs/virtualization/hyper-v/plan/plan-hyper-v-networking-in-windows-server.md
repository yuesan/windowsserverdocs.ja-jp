---
title: Windows Server での Hyper-v ネットワークの計画
description: Hyper-v の基本的なネットワークに必要なものについて説明し、手順へのリンクを示します。
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.topic: article
author: kbdazure
ms.author: kathydav
ms.date: 10/04/2016
ms.openlocfilehash: 3127c9579493ad8b317667b61de88304fd14f6cf
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80860765"
---
# <a name="plan-for-hyper-v-networking-in-windows-server"></a>Windows Server での Hyper-v ネットワークの計画

>適用対象: Microsoft Hyper-V Server 2016、Windows Server 2016、Microsoft Hyper-V Server 2019、Windows Server 2019
  
Hyper-v でのネットワークについての基本的な理解は、仮想マシンのネットワークを計画するのに役立ちます。 この記事では、ライブマイグレーションを使用する場合や、他のサーバーの機能や役割で Hyper-v を使用する場合のネットワークの考慮事項についても説明します。  
  
## <a name="hyper-v-networking-basics"></a>Hyper-v ネットワークの基礎  
Hyper-v の基本的なネットワークは非常に単純です。 仮想スイッチと仮想ネットワークアダプターの2つの部分を使用します。 仮想マシンのネットワークを確立するには、少なくとも1つのが必要です。 仮想スイッチは、任意のイーサネットベースのネットワークに接続します。 仮想ネットワークアダプターは、仮想スイッチのポートに接続します。これにより、仮想マシンでネットワークを使用できるようになります。  
  
基本的なネットワークを確立する最も簡単な方法は、Hyper-v をインストールするときに仮想スイッチを作成することです。 その後、仮想マシンを作成するときに、スイッチに接続できます。 スイッチに接続すると、仮想ネットワークアダプターが仮想マシンに自動的に追加されます。 手順については、「 [hyper-v 仮想マシンの仮想スイッチを作成する](../get-started/Create-a-virtual-switch-for-Hyper-V-virtual-machines.md)」を参照してください。  
  
さまざまな種類のネットワークを処理するために、仮想スイッチと仮想ネットワークアダプターを追加できます。 すべてのスイッチは Hyper-v ホストの一部ですが、各仮想ネットワークアダプターは1つの仮想マシンにのみ属しています。  
  
仮想スイッチは、ソフトウェアベースのレイヤー2イーサネットネットワークスイッチです。 これには、トラフィックの監視、制御、およびセグメント化を行うための機能が組み込まれています。セキュリティと診断にも対応しています。  プラグイン (*拡張*機能とも呼ばれます) をインストールすることによって、一連の組み込み機能にを追加できます。 これらは、独立系ソフトウェアベンダーから入手できます。 スイッチと拡張機能の詳細については、「 [Hyper-v 仮想スイッチ](../../hyper-v-virtual-switch/Hyper-V-Virtual-Switch.md)」を参照してください。  
  
### <a name="switch-and-network-adapter-choices"></a>スイッチとネットワークアダプターの選択  
Hyper-v には、3種類の仮想スイッチと2種類の仮想ネットワークアダプターが用意されています。 作成時に、どちらを選択するかを選択します。 Hyper-v マネージャーまたは Windows PowerShell 用 Hyper-v モジュールを使用して、仮想スイッチと仮想ネットワークアダプターを作成および管理できます。 拡張ポートアクセス制御リスト (Acl) などの一部の高度なネットワーク機能は、Hyper-v モジュールのコマンドレットを使用してのみ管理できます。  
  
仮想スイッチまたは仮想ネットワークアダプターは、作成後にいくつかの変更を加えることができます。 たとえば、既存のスイッチを別の種類に変更することはできますが、その場合は、そのスイッチに接続されているすべての仮想マシンのネットワーク機能に影響します。  そのため、間違っている場合や、何かをテストする必要がある場合を除いて、このようなことはありません。 別の例として、仮想ネットワークアダプターを別のスイッチに接続することもできます。これは、別のネットワークに接続する場合に実行することができます。 ただし、仮想ネットワークアダプターをある種類から別の種類に変更することはできません。 種類を変更するのではなく、別の仮想ネットワークアダプターを追加し、適切な種類を選択します。  
  
仮想スイッチの種類は次のとおりです。  
  
-   **外部仮想スイッチ**-物理ネットワークアダプターにバインドすることによって、ワイヤード (有線) 物理ネットワークに接続します。  
  
-   **内部仮想スイッチ**-仮想スイッチを持つホストで実行されている仮想マシン、およびホストと仮想マシンの間でのみ使用できるネットワークに接続します。  
  
-   **プライベート仮想スイッチ**-仮想スイッチを持つホスト上で実行されている仮想マシンのみが使用できるネットワークに接続します。ただし、ホストと仮想マシン間のネットワークは提供しません。  
  
仮想ネットワークアダプターの種類は次のとおりです。  
  
-   **Hyper-v 固有のネットワークアダプター** -第1世代と第2世代の両方の仮想マシンで使用できます。 これは Hyper-v 専用に設計されており、Hyper-v 統合サービスに含まれるドライバーが必要です。 ネットワークで起動する必要がある場合や、サポートされていないゲストオペレーティングシステムを実行している場合以外は、この種類のネットワークアダプターの方が高速で、推奨される選択肢です。 必要なドライバーは、サポートされているゲストオペレーティングシステムに対してのみ提供されます。 Hyper-v マネージャーとネットワークコマンドレットでは、この種類はネットワークアダプターと呼ばれることに注意してください。  
  
-   **レガシネットワークアダプター** -第1世代の仮想マシンでのみ使用できます。 Intel 21140 ベースの PCI 高速イーサネットアダプターをエミュレートし、Windows 展開サービスなどのサービスからオペレーティングシステムをインストールできるように、ネットワークを起動するために使用できます。  
  
## <a name="hyper-v-networking-and-related-technologies"></a>Hyper-v ネットワークと関連テクノロジ  
最新の Windows Server リリースでは、Hyper-v のネットワークを構成するためのオプションが追加されました。 たとえば、Windows Server 2012 では、収束ネットワークのサポートが導入されました。 これにより、1つの外部仮想スイッチを経由してネットワークトラフィックをルーティングすることができます。 Windows Server 2016 は、Hyper-v 仮想スイッチにバインドされているネットワークアダプターでリモートダイレクトメモリアクセス (RDMA) を許可することにより、これに基づいています。 この構成は、スイッチ埋め込みチーミング (SET) の有無にかかわらず、使用できます。 詳細については、「[リモート&#40;ダイレクト&#41;メモリアクセス RDMA と&#40;スイッチ&#41;埋め込みチーミングセット](../../hyper-v-virtual-switch/RDMA-and-Switch-Embedded-Teaming.md)」を参照してください。  
  
一部の機能は、特定のネットワーク構成に依存しているか、特定の構成でより適切に機能します。 ネットワークインフラストラクチャを計画または更新するときに、これらを考慮してください。  
  
**フェールオーバークラスタリング**-クラスタートラフィックを分離し、仮想スイッチで Hyper-v のサービスの品質 (QoS) を使用することをお勧めします。 詳細については、「 [Hyper-v クラスターのネットワーク推奨事項](https://technet.microsoft.com/library/dn550728.aspx)」を参照してください。  
  
**ライブマイグレーション**-パフォーマンスオプションを使用して、ネットワークと CPU の使用率を減らし、ライブマイグレーションを完了するのにかかる時間を短縮します。 手順については、「[フェールオーバークラスタリングを使用しないライブマイグレーションのホストの設定](../deploy/set-up-hosts-for-live-migration-without-failover-clustering.md)」を参照してください。  
  
**記憶域スペースダイレクト**-この機能は、smb 3.0 ネットワークプロトコルと RDMA に依存しています。 詳細については、「 [Windows Server 2016 の記憶域スペースダイレクト](../../../storage/storage-spaces/storage-spaces-direct-overview.md)」を参照してください。