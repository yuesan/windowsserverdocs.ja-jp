---
ms.assetid: 4163cf03-3bff-426c-9844-4cc2d7897d52
title: AD DS の DNS の所有者の役割を割り当てる
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 8ef63fd9e53d20c812ff84e601e73d4276b304be
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80825265"
---
# <a name="assigning-the-dns-for-ad-ds-owner-role"></a>AD DS の DNS の所有者の役割を割り当てる

>適用対象: Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

フォレスト所有者は、フォレストの Active Directory Domain Services (AD DS) 所有者にドメインネームシステム (DNS) を割り当てます。 フォレストの AD DS 所有者の DNS は、AD DS インフラストラクチャの DNS の展開を監視し、必要に応じてドメイン名が適切なインターネット機関に登録されていることを確認する担当者 (またはユーザーのグループ) です。  
  
AD DS 所有者の DNS は、フォレストの AD DS 設計の DNS に責任を持ちます。 組織が現在 DNS サーバーサービスを運用している場合、既存の DNS サーバーサービスの dns デザイナーは AD DS 所有者の DNS と連携して、ドメインコントローラー上で実行されている DNS サーバーにフォレストルート DNS 名を委任します。  
  
フォレストの AD DS 所有者の DNS では、動的ホスト構成プロトコル (DHCP) グループと組織の DNS グループの連絡先も保持し、フォレスト内の各ドメイン (存在する場合) の個々の DNS 所有者の計画をこれらのグループと調整します。 フォレストの DNS 所有者は、各グループが DNS 設計計画を認識し、事前に入力を提供できるように、DHCP グループと DNS グループが AD DS 設計プロセスの DNS に関与していることを確認します。  
  


