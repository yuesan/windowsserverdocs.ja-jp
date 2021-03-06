---
title: 手順 4. クラスターを確認する
description: このトピックは、「Windows Server 2016 のクラスターにリモートアクセスを展開する」の一部です。
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: f22dcf10-b453-4664-a9ef-e40e95c72f63
ms.author: lizross
author: eross-msft
ms.openlocfilehash: c31db158856eb3c3881a36c29e40d1227116201f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855265"
---
# <a name="step-4-verify-the-cluster"></a>手順 4. クラスターを確認する

>適用対象: Windows Server (半期チャネル)、Windows Server 2016

このトピックでは、DirectAccess クラスターの展開が正しく構成されていることを確認する方法について説明します。  
  
### <a name="to-verify-access-to-internal-resources-through-the-cluster"></a>クラスターを介して内部リソースへのアクセスを確認するには  
  
1.  DirectAccess クライアント コンピューターを企業ネットワークに接続し、グループ ポリシーを取得します。  
  
2.  クライアント コンピューターを外部ネットワークに接続して、内部リソースへのアクセスを試行します。  
  
    すべての企業リソースにアクセスできます。  
  
3.  クラスター内の各サーバーを使用して接続をテストします。これを行うには、クラスターサーバーの1つではなく、外部ネットワークから電源をオフにするか、接続を切断します。 クライアントコンピューターで、会社のリソースへのアクセスを試みます。 別のクラスターサーバーでテストを繰り返します。  
  
    各クラスターサーバーを介して、すべての企業リソースにアクセスできる必要があります。  
  


