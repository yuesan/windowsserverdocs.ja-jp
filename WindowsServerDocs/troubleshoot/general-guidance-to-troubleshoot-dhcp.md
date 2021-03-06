---
title: DHCP のトラブルシューティングに関する一般的なガイダンス
description: この artilce では、DHCP のトラブルシューティングに関する一般的なガイダンスについて説明します。
ms.prod: windows-server
ms.service: na
manager: dcscontentpm
ms.technology: server-general
ms.date: 5/26/2020
ms.topic: article
author: Deland-Han
ms.author: delhan
ms.openlocfilehash: c0460791fef2451722af09e8bbe08b51a605f01b
ms.sourcegitcommit: ef089864980a1d4793a35cbf4cbdd02ce1962054
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2020
ms.locfileid: "84150160"
---
# <a name="general-guidance-to-troubleshoot-dhcp"></a>DHCP のトラブルシューティングに関する一般的なガイダンス

トラブルシューティングを開始する前に、次の項目を確認してください。 これらは、問題の根本原因を見つけるのに役立ちます。

## <a name="checklist"></a>チェック リスト

  - 問題が発生し始めた時期

  - エラーメッセージはありますか。

  - DHCP サーバーが以前に動作していたか、または動作していないか。  
    以前に動作していた場合、問題が開始される前に何か変更が行われました。 たとえば、更新プログラムがインストールされているとします。 インフラストラクチャに変更が加えられたか。

  - 問題は永続的か断続的か。 断続的な場合、最後に発生したのはいつですか。

  - すべてのクライアントまたは単一スコープのサブネットなど、特定のクライアントに対してのみ、アドレスのリースエラーが発生していますか。

  - DHCP サーバーと同じネットワークサブネットにクライアントが存在するか。

  - クライアントが同じネットワークサブネットに存在する場合、クライアントは IP アドレスを取得できますか。

  - クライアントが同じネットワークサブネット上にない場合は、ルーターまたは VLAN スイッチが DHCP リレーエージェント (IP ヘルパーとも呼ばれる) を持つように正しく構成されているかどうかを確認します。

  - DHCP サーバーがスタンドアロンであるか、または分割スコープや DHCP フェールオーバーなどの高可用性用に構成されているか。

  - 中間デバイスで、問題の原因として知られている VRRP/HSRP、動的 ARP 検査、DHCP スヌーピングなどの機能を確認します。
