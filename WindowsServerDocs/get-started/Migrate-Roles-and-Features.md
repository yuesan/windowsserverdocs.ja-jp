---
title: 役割と機能の移行
description: 役割と機能を新しいバージョンの Windows Server に移行する方法について説明します。
ms.prod: windows-server
ms.date: 08/28/2019
ms.technology: server-general
ms.topic: article
ms.assetid: 0f78ef4c-dd12-4b1b-8c6e-251dd803c5d1
author: jasongerend
ms.author: jgerend
manager: dougkim
ms.localizationpriority: medium
ms.openlocfilehash: 33c1aa654e4c660b4fe2f3305bfaf78b5191220a
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "70119200"
---
# <a name="migrating-roles-and-features-in-windows-server"></a>Windows Server の役割と機能を移行する

> 適用先:Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

このページでは、新しいバージョンの Windows Server への役割と機能の移行に役立つ情報やツールへのリンクを示します。 [記憶域の移行サービス](../storage/storage-migration-service/overview.md)を使用してファイル サーバーと記憶域を移行できますが、その他の多くの役割と機能は、Windows Server 2008 R2 で役割と機能の移行のために導入された一連の PowerShell コマンドレットである Windows Server 移行ツールを使用して移行できます。

移行ガイドは、2 台のサーバー間で、指定した役割や機能を移行する作業について記載されています (インプレース アップグレードは対象外です)。 ガイドの中で特に断りのない限り、移行は物理コンピューターと仮想コンピューターの間において、完全なインストール オプションの Windows Server と Server Core インストール オプションを実行しているサーバー間でサポートされます。

## <a name="before-you-begin"></a>開始する前に

役割と機能の移行を開始する前に、移行元と移行先の両方のサーバーが、それぞれのオペレーティング システムで利用可能な最新のサービス パックを実行していることを確認します。 

> [!NOTE]
> Windows Server のどのバージョンに移行またはアップグレードする場合も、[サポート ライフサイクル ポリシー](https://support.microsoft.com/lifecycle)および対象バージョンのサポート期間を確認し把握したうえで、それに応じて計画を立てる必要があります。 特定の Windows Server リリースのライフサイクルについては、[こちらでご検索ください](https://support.microsoft.com/lifecycle)。

## <a name="windows-server-2019"></a>Windows Server 2019

ファイル サーバーと記憶域を Windows Server 2019 または Windows Server 2016 に移行するには、[記憶域の移行サービス](../storage/storage-migration-service/overview.md)を使用することをお勧めします。 他の役割を移行するには、Windows Server 2016 および Windows Server 2012 R2 のガイダンスを参照してください。

## <a name="windows-server-2016"></a>Windows Server 2016

ここでは、Windows Server 2016 の移行ガイドを示します。 多くの場合、Windows Server 2012 R2 の移行ガイドを使用することもできます。

- [リモート デスクトップ サービス](https://technet.microsoft.com/windows-server-docs/compute/remote-desktop-services/migrate-rds-role-services)
- [Web サーバー (IIS)](https://www.iis.net/downloads/microsoft/web-deploy)
- [Windows Server Update Services](https://technet.microsoft.com/library/hh852339.aspx)
- [MultiPoint Services](https://technet.microsoft.com/windows-server-docs/compute/remote-desktop-services/multipoint-services/multipoint-services-migrate)

ファイル サーバーを Windows Server 2019 または Windows Server 2016 に移行するには、[記憶域の移行サービス](../storage/storage-migration-service/overview.md)を使用することをお勧めします。

## <a name="windows-server-2012-r2"></a>Windows Server 2012 R2

Windows Server 2003、Windows Server 2008、Windows Server 2008 R2、Windows Server 2012、Windows Server 2012 R2 のいずれかを実行しているサーバーの役割と機能を Windows Server 2012 R2 に移行する場合は、以下のガイドの手順に従ってください。 Windows Server 2012 R2 の Windows Server 移行ツールでは、クロス サブネットの移行がサポートされています。

- [Windows Server 移行ツールのインストール、使用、および削除](https://technet.microsoft.com/library/jj134202.aspx)
- [Windows Server 2012 R2 用 Active Directory 証明書サービス移行ガイド](https://technet.microsoft.com/library/dn486797.aspx)
- [Windows Server 2012 R2 への Active Directory フェデレーション サービス役割サービスの移行](https://technet.microsoft.com/library/dn486815.aspx)
- [Active Directory Rights Management サービスの移行およびアップグレード ガイド](https://technet.microsoft.com/library/cc754277.aspx)
- [Windows Server 2012 R2 へのファイル サービスおよび記憶域サービスの移行](https://technet.microsoft.com/library/dn479292.aspx)
- [Windows Server 2012 から Windows Server 2012 R2 への Hyper-V の移行](https://technet.microsoft.com/library/dn486799.aspx)
- [Windows Server 2012 へのネットワーク ポリシー サーバーの移行](https://technet.microsoft.com/library/hh831652)
- [Windows Server 2012 R2 へのリモート デスクトップ サービスの移行](https://technet.microsoft.com/library/dn479239.aspx)
- [Windows Server 2012 R2 への Windows Server Update Services の移行](https://technet.microsoft.com/library/hh852339.aspx)
- [Windows Server 2012 R2 へのクラスターの役割の移行](https://technet.microsoft.com/library/dn530779.aspx)
- [Windows Server 2012 R2 への DHCP サーバーの移行](https://technet.microsoft.com/library/dn495425.aspx)

Windows Server 2012 R2 と Windows Server 2012 の移行ガイドは、電子書籍版が提供されています。 詳細および電子書籍のダウンロードについては、「[E-Book Gallery for Microsoft Technologies (マイクロソフト テクノロジ電子書籍ギャラリー)](https://social.technet.microsoft.com/wiki/contents/articles/11608.e-book-gallery-for-microsoft-technologies.aspx#MigrateRoles)をご覧ください。

## <a name="windows-server-2012"></a>Windows Server 2012

Windows Server 2003、Windows Server 2008、Windows Server 2008 R2、Windows Server 2012 のいずれかを実行しているサーバーの役割と機能を Windows Server 2012 に移行する場合は、以下のガイドの手順に従ってください。 Windows Server 2012 の Windows Server 移行ツールでは、クロス サブネットの移行がサポートされています。

- [Windows Server 移行ツールのインストール、使用、および削除](https://technet.microsoft.com/library/jj134202)
- [Windows Server 2012 への Active Directory フェデレーション サービス (AD FS) 役割サービスの移行](https://technet.microsoft.com/library/jj647765)
- [Windows Server 2012 への正常性登録機関の移行](https://technet.microsoft.com/library/hh831513)
- [Windows 2008 R2 から Windows Server 2012 への Hyper-V の移行](https://technet.microsoft.com/library/jj574113)
- [Windows Server 2012 への IP 構成の移行](https://technet.microsoft.com/library/jj574133)
- [Windows Server 2012 へのネットワーク ポリシー サーバーの移行](https://technet.microsoft.com/library/hh831652)
- [Windows Server 2012 への印刷とドキュメント サービスの移行](https://technet.microsoft.com/library/jj134150)
- [Windows Server 2012 へのリモート アクセスの移行](https://technet.microsoft.com/library/hh831423)
- [Windows Server 2012 への Windows Server Update Services の移行](https://technet.microsoft.com/library/hh852339)
- [Active Directory ドメイン コントローラーを Windows Server 2012 にアップグレードする](https://technet.microsoft.com/library/hh994618.aspx)
- [クラスター化されたサービスとアプリケーションの Windows Server 2012 への移行](https://technet.microsoft.com/library/dn486790.aspx)
 

移行に関するその他の資料については、「[Windows Server への役割と機能の移行](https://technet.microsoft.com/library/jj134039)」をご覧ください。

## <a name="windows-server-2008-r2"></a>Windows Server 2008 R2

Windows Server 2003、Windows Server 2008、Windows Server 2008 R2 のいずれかを実行しているサーバーの役割と機能を Windows Server 2008 R2 に移行する場合は、以下のガイドの手順に従ってください。 Windows Server 2008 R2 の Windows Server 移行ツールでは、クロス サブネットの移行はサポートされていません。

- [Windows Server 移行ツールのインストール、アクセス、および削除](https://technet.microsoft.com/library/dd379545)
- [Active Directory 証明書サービス移行ガイド](https://technet.microsoft.com/library/ee126170)
- [Active Directory Domain Services とドメイン ネーム システム (DNS) サーバーの移行ガイド](https://technet.microsoft.com/library/dd379558)
- [BranchCache 移行ガイド](https://technet.microsoft.com/library/dd548365)
- [動的ホスト構成プロトコル (DHCP) サーバーの移行ガイド](https://technet.microsoft.com/library/dd379535)
- [ファイル サービスの移行ガイド](https://technet.microsoft.com/library/dd379487)
- [HRA 移行ガイド](https://technet.microsoft.com/library/ee791829)
- [Hyper-V 移行ガイド](https://technet.microsoft.com/library/ee849855)
- [IP 構成移行ガイド](https://technet.microsoft.com/library/dd379537)
- [ローカル ユーザーとグループ移行のガイド](https://technet.microsoft.com/library/dd379531)
- [NPS 移行ガイド](https://technet.microsoft.com/library/ee791849)
- [印刷サービス移行ガイド](https://technet.microsoft.com/library/dd379488)
- [リモート デスクトップ サービスの移行ガイド](https://technet.microsoft.com/library/ff849223)
- [RRAS 移行ガイド](https://technet.microsoft.com/library/ee822825)
- [Windows Server の移行に関する一般的なタスクと情報](https://technet.microsoft.com/library/ff400258)
- [Windows Server Update Services 3.0 SP2 移行ガイド](https://technet.microsoft.com/library/ee822826)
 
移行に関するその他の資料については、「[Migrate Roles and Features to Windows Server 2008 R2 (Windows Server 2008 R2 への役割と機能の移行)](https://technet.microsoft.com/library/dd365353)」をご覧ください。
