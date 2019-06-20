---
ms.assetid: 84754c23-f039-4de4-a378-853942e662df
title: 概要
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 8e2717af6183944b26a71e55b36f31cef51cf2e7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59831873"
---
# <a name="introduction"></a>概要

>適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

コンピューターがある限り単純または複雑なかどうかと、コンピューティング、インフラストラクチャに対する攻撃が存在しています。 ただし、この 10 年間において世界中で規模を問わず攻撃やセキュリティ侵害の被害にあった組織の数が増加の一途を辿っている現在、脅威の情勢は大きく変わりました。 サイバー戦争とサイバー犯罪は、過去最高の件数に達しています。 "Hacktivism、"さらの位置を攻撃のきっかけは、サービス拒否を作成する、組織の秘密情報を公開するためのもので、侵害の動機として主張またはインフラストラクチャを破棄する場合でもされました。 目標ひそかにパブリックおよびプライベートの機関に対する攻撃は組織の知的財産 (IP) をユビキタスになっています。  
  
組織のコンピューティング インフラストラクチャからの攻撃のエスカレーションの重要なセグメントを保護する適切なポリシー、プロセス、およびコントロールが実装されている場合は、攻撃に対して免疫組織情報技術 (IT) インフラストラクチャではありません。セキュリティ侵害を完了する侵入は不可避可能性があります。 組織の外部から攻撃の小数点以下桁数と数に、近年の内部に脅威がまで、ため、このドキュメント多くの場合、承認されたユーザーごとに環境の不正使用ではなく、外部の攻撃者がについて説明します。 それでも、原則と推奨事項がこのドキュメントに記載されたは、外部の攻撃者および間違った考えや悪意のある内部関係者から環境を保護するために対象としています。  
  
については、このドキュメントに記載された推奨事項は、複数のソースから抽出されたおり、侵害から Active Directory のインストールを保護するための手法から派生します。 Active Directory の攻撃対象領域を小さくと、コントロールを実装することはありません、攻撃を防ぐことが、攻撃者の格段に難しく、ディレクトリのセキュリティを侵害します。 このドキュメントで観察対象が侵害された環境と、Active Directory インストールのセキュリティを向上させるためにお客様に行いました最も一般的な推奨事項がある脆弱性の最も一般的な種類を表示します。  
  
## <a name="account-and-group-naming-conventions"></a>アカウントとグループの名前付け規則  
次の表では、グループと、文書全体で参照されるアカウントのこのドキュメントで使用される名前付け規則にガイドを提供します。 テーブルには、各アカウントとグループ、名前、およびこのドキュメントでこれらのアカウントまたはグループを参照する方法の場所です。  
  


|**アカウントとグループの場所**|**アカウント/グループの名前**|**このドキュメントでの参照方法**|
| --- | --- | --- |   
|Active Directory - 各ドメイン|管理者|ビルトイン Administrator アカウント|  
|Active Directory - 各ドメイン|管理者|組み込みの管理者 (BA) グループ|  
|Active Directory - 各ドメイン|Domain Admins|ドメイン管理者 (DA) のグループ|  
|Active Directory のフォレスト ルート ドメイン|Enterprise Admins|Enterprise Admins (EA) グループ|  
|ローカル コンピューターのセキュリティ アカウント マネージャー (SAM) データベースは Windows Server とワークステーションを実行するコンピューターでドメイン コント ローラーでないです。|管理者|ローカル管理者アカウント|  
|ローカル コンピューターのセキュリティ アカウント マネージャー (SAM) データベースは Windows Server とワークステーションを実行するコンピューターでドメイン コント ローラーでないです。|管理者|ローカルの Administrators グループ|  
  
## <a name="about-this-document"></a>このドキュメントについて  
一部の Microsoft 情報テクノロジ (MSIT) では、Microsoft の情報セキュリティおよびリスク管理 (ISRM) 組織は、収集、配布、およびポリシーを定義するには、内部のビジネス単位、外部の顧客および同業者と連携します。プラクティス、およびコントロール。 この情報は、Microsoft とお客様がセキュリティし、IT インフラストラクチャの攻撃対象領域を減らすために使用できます。 このドキュメントに記載された推奨事項は、さまざまな情報源と MSIT と ISRM 内で使用されるプラクティスに基づいています。 次のセクションでは、このドキュメントの配信元の詳細を示します。  
  
### <a name="microsoft-it-and-isrm"></a>Microsoft IT と ISRM  
さまざまなプラクティスとコントロールは、Microsoft の AD DS フォレストおよびドメインをセキュリティで保護するには、MSIT および ISRM 内で開発されています。 これらのコントロールが広範に適用される場合は、このドキュメントに統合されています。 SAFE T (最新のテクノロジのソリューション アクセラレータ) は、ISRM 憲章の導入を促進するには、セキュリティ要件と制御を定義して、新たなテクノロジを識別するためには、社内のチーム。  
  
### <a name="active-directory-security-assessments"></a>Active Directory セキュリティ評価  
Microsoft ISRM、評価、コンサルティング、およびチームのエンジニア リング (ACE) およびと組み合わせて使用内部の Microsoft の事業部外部の顧客と戦術的かつ戦略的なガイダンスを提供するアプリケーションとインフラストラクチャのセキュリティの評価を向上させる内で、組織のセキュリティ対策です。 1 つの ACE サービス内容は、Active Directory セキュリティ評価 (ADSA)、これは人、プロセス、およびテクノロジを評価し、顧客固有の推奨事項を生成する、組織の AD DS 環境の全体的な評価です。 お客様には、組織の固有の特性、プラクティス、およびリスク選好度に基づいて推奨事項が提供されます。 ADSAs だけでなく、お客様の Microsoft の Active Directory インストールに対して実行します。 時間の経過と共にさまざまなサイズおよび業界のお客様に適用される推奨の数が検出されました。  
  
### <a name="content-origin-and-organization"></a>内容の元情報と組織  
このドキュメントの内容の多くは、ADSA とセキュリティを侵害された顧客および重要なセキュリティ侵害が発生していない顧客に対して実行されるその他の ACE チーム評価から派生します。 特定された最もよく悪用された脆弱性を収集しましたが、個々 の顧客データは、このドキュメントの作成に使用されませんでした、評価と推奨事項で行いましたお客様に、AD DS のセキュリティを強化するにはインストール。 すべての脆弱性がすべての環境に該当するとは限らず、またすべての推奨事項をすべての組織に実装できるとも限りません。  
  
このドキュメントは、次のように構成されています。  
  
## <a name="executive-summary"></a>概要  
Executive 概要、スタンドアロン ドキュメントとしてと組み合わせて、完全なドキュメント読み取り可能なは、このドキュメントの概要を提供します。 お客様の環境、新しい AD DS をデプロイする予定のお客様の Active Directory のインストール、および基本的な目的を保護するための推奨事項の概要を侵害するために使用がわかっています、最も一般的な攻撃ベクトルは Executive の概要も含まれますフォレストまたは今後のようになりました。  
  
### <a name="introduction"></a>概要  
これは、セクションを読み取るようになりました。  
  
### <a name="avenues-to-compromise"></a>セキュリティ侵害に至る過程  
このセクションでは、ほとんどの一部についての情報が一般的に攻撃者が使用して、お客様のインフラストラクチャを侵害するが見つかった脆弱性を活用を提供します。 このセクションの脆弱性とを最初に顧客のインフラストラクチャに侵入、追加のシステム間でセキュリティ侵害を伝達および最終的に完了するため、AD DS とドメイン コント ローラーが活用される方法の一般的なカテゴリから始まります組織のフォレストのコントロールです。  
  
このセクションでは、Active Directory を直接ターゲットに使用されない、脆弱性を領域で特にの脆弱性の種類ごとにアドレス指定に関する詳細な推奨事項は提供されません。 ただし、各種類の脆弱性には、対策を開発し、組織の攻撃対象領域の削減に使用できる追加情報へのリンクを提供しますが。  
  
### <a name="reducing-the-active-directory-attack-surface"></a>Active Directory の攻撃を削減する  
このセクションでは役立ちますが、セキュリティで保護して、特権を持つグループの管理、後続の推奨事項の理由を明確に情報を提供する Active Directory の特権アカウントとグループに関する背景情報を提供することで開始し、アカウント。 Enterprise Admins (EA)、ドメイン管理者 (DA) や組み込みなどのグループに付与される特権のレベルを必要としない日常的な管理は、高い特権を持つアカウントを使用する必要性が軽減する方法について説明しますActive Directory でグループを管理者 (BA)。 次に、特権を持つグループとアカウントを保護するため、安全な管理手順とシステムを実装するためのガイダンスを紹介します。  
  
このセクションには、これらの構成設定に関する詳細情報が用意されていますも含めましたに使用される「は」そのままにすることができますかで変更できるステップ バイ ステップの構成手順が記載された各推奨事項は、付録、組織の必要があります。 このセクションでは、情報を安全に展開し、インフラストラクチャに最も厳密にセキュリティで保護されたシステム間でとして使用するドメイン コント ローラーの管理を提供することで完了します。  
  
### <a name="monitoring-active-directory-for-signs-of-compromise"></a>Active Directory の侵害の兆候を監視する  
堅牢なセキュリティ情報と、環境で (SIEM) の監視イベントを実装するか、またはインフラストラクチャのセキュリティを監視する他のメカニズムを使用しているかどうか、このセクションでは、Windows 上のイベントを識別するために使用できる情報を提供しますシステムは、組織が攻撃を受けることがある可能性があります。 Windows 7 および Windows Vista オペレーティング システムの監査サブカテゴリの効果的な構成を含む、従来と高度な監査ポリシーについて説明します。 ここでは、オブジェクトとを監査するには、システムの包括的な一覧と関連の付録には、監視する必要があります目標は、セキュリティ侵害の試みを検出する場合のイベントが一覧表示します。  
  
### <a name="planning-for-compromise"></a>侵害対策を計画する  
このセクションでは、まず基本原則と、ユーザー、アプリケーション、およびだけでなく、IT インフラストラクチャに最も重要なシステムを識別するために実装できるプロセスに重点を置く技術的な詳細からの「ステップ バック」が、ビジネスにします。 安定性と、組織の運営にとって最も重要な新機能を識別するには後の知的財産や、人、システムでかどうか分離して、これらの資産をセキュリティ保護に集中できます。 分離して、資産の保護を実行する可能性がありますで場合によっては、既存の AD DS 環境でその他のケースで検討してください、小規模の独立した「セル」を実装する重要な資産をセキュリティで保護された境界を確立し、それらを監視できるようにします。資産重要度の低いコンポーネントよりも厳密します。 「創造的な破棄、」は、従来のアプリケーションとシステムを新しいソリューションの作成で解消できますメカニズムであるという概念が説明されているとでより安全な環境を維持するために役立つ推奨事項を終わるセクションビジネスと IT の情報は通常の動作状態の詳細な図を作成する組み合わせ。 組織の通常とは何ですかを知ることでは、攻撃や侵害を示す可能性のある異常をより簡単に識別します。  
  
### <a name="summary-of-best-practice-recommendations"></a>ベスト プラクティスの推奨事項の概要  
このセクションでは、このドキュメントの推奨事項をまとめた表を提供し、各推奨事項の詳細についてを参照して、ドキュメント、およびその付録場所へのリンクを提供するだけでなく、相対的な優先順位に並べ替えられます。  
  
### <a name="appendices"></a>付録  
ドキュメントの本文に含まれる情報を強化するには、このドキュメントでは、付録が含まれます。 付録とそれぞれの簡単な説明の一覧が含まれる次の表にします。  
  
 
|**付録**|**説明**|
| --- | --- | 
|[付録 b:Active Directory の特権アカウントとグループ](../../../ad-ds/plan/security-best-practices/Appendix-B--Privileged-Accounts-and-Groups-in-Active-Directory.md)|ユーザーと攻撃者が侵害され、でも、Active Directory のインストールを破棄して、利用できるため、セキュリティで保護することに注意すべきグループを識別するために役立つ背景情報を提供します。|  
|[付録 c:保護されたアカウントと Active Directory のグループ](../../../ad-ds/plan/security-best-practices/Appendix-C--Protected-Accounts-and-Groups-in-Active-Directory.md)|Active Directory の保護されたグループに関する情報が含まれています。 保護グループと見なされ、AdminSDHolder および SDProp によって影響を受けるグループの限定的なカスタマイズ (削除) の情報も含まれています。|  
|[付録 d:Active Directory でビルトイン Administrator アカウントのセキュリティ保護](../../../ad-ds/plan/security-best-practices/Appendix-D--Securing-Built-In-Administrator-Accounts-in-Active-Directory.md)|フォレスト内の各ドメインの Administrator アカウントをセキュリティ保護するためのガイドラインについて説明します。|  
|[付録 e:Active Directory の Enterprise Admins グループのセキュリティ保護](../../../ad-ds/plan/security-best-practices/Appendix-E--Securing-Enterprise-Admins-Groups-in-Active-Directory.md)|フォレストの Enterprise Admins グループのセキュリティを保護するためのガイドラインについて説明します。|  
|[付録 f:Active Directory の Domain Admins グループのセキュリティ保護](../../../ad-ds/plan/security-best-practices/Appendix-F--Securing-Domain-Admins-Groups-in-Active-Directory.md)|フォレスト内の各ドメインの Domain Admins グループのセキュリティを保護するためのガイドラインについて説明します。|  
|[付録 g:Active Directory の管理者グループのセキュリティ保護](../../../ad-ds/plan/security-best-practices/Appendix-G--Securing-Administrators-Groups-in-Active-Directory.md)|フォレスト内の各ドメインで組み込みの Administrators グループのセキュリティを保護するためのガイドラインについて説明します。|  
|[付録 h:ローカル管理者アカウントとグループをセキュリティで保護します。](../../../ad-ds/plan/security-best-practices/Appendix-H--Securing-Local-Administrator-Accounts-and-Groups.md)|セキュリティで保護されたローカル管理者アカウントとドメインに参加しているサーバーおよびワークステーションで管理者グループのためのガイドラインが含まれています。|  
|[付録 i:Active Directory 内の保護されたアカウントとグループ アカウントの管理の作成](../../../ad-ds/manage/component-updates/Appendix-I--Creating-Management-Accounts-for-Protected-Accounts-and-Groups-in-Active-Directory.md)|限られた特権と、厳密制御できますが、一時的な昇格が必要な場合は、Active Directory で権限を持つグループを設定するために使用するアカウントを作成する情報を提供します。|  
|[付録 l:監視するイベント](../../../ad-ds/plan/Appendix-L--Events-to-Monitor.md)|環境内で監視する必要がありますをイベントの一覧を表示します。|  
|[付録 m:ドキュメントのリンクと推奨資料](../../../ad-ds/manage/Appendix-M--Document-Links-and-Recommended-Reading.md)|推奨資料の一覧が含まれています。 このドキュメントのハード コピーの読者の皆さんがこの情報にアクセスできるように、外部ドキュメントへのリンクの一覧とその Url もあります。|  
  

