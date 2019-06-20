---
ms.assetid: 77aa61bf-9c04-4889-a5d2-6f45bc1b8bd2
title: 変換要求規則を使用するタイミング
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 5ed8ee500582e0e687a2b52e83d99fc3cb8f147f
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2019
ms.locfileid: "66188345"
---
# <a name="when-to-use-a-transform-claim-rule"></a>変換要求規則を使用するタイミング
この規則を使用するには Active Directory フェデレーション サービスで\(AD FS\)値に基づいて出力方向の要求の種類に、受信要求の種類をマップし、発生させる出力を決定するアクションを適用する必要がある場合です入力方向の要求で開始されます。 この規則を使用する場合は、次の規則のロジックと一致する要求を、次の表で説明する規則の構成オプションのいずれかに基づいてパススルーまたは変換します。  
  
|規則のオプション|規則のロジック|  
|---------------|--------------|  
|すべての入力方向の要求をパススルーする|入力方向の要求の種類が "指定された要求の種類" ** に等しく、値が "任意の値" ** に等しい場合は、出力方向の種類が "指定された要求の種類" ** に等しい要求をパススルーします|  
|入力方向の要求の値を、別の出力方向の要求の値に置き換える|入力方向の要求の種類が "指定された要求の種類" ** に等しく、値が "指定された要求の値" ** に等しい場合は、新しい出力方向の要求の値 "指定された要求の値" ** と出力要求の種類 "指定された要求の種類" ** で要求を変換します|  
|受信した電子メールを置き換える\-メールで新しい電子メール サフィックス要求\-メール サフィックス|入力方向の要求の種類が "指定された要求の種類" ** に等しく、値が "任意のサフィックスの値" ** に等しい場合は、新しい出力方向の要求の値 "指定されたサフィックスの値" ** と出力要求の種類 "指定された要求の種類" ** で要求を変換します|  
  
次のセクションでは、要求規則の概要と、その規則を使用するタイミングについて詳しく説明します。  
  
## <a name="about-claim-rules"></a>要求規則について  
要求規則が入力方向の要求を実行を条件を適用するビジネス ロジックのインスタンスを表します\(x、y if\)条件パラメーターに基づいて出力方向の要求を生成します。 次の一覧に、このトピックを読む前に理解しておく必要のある、要求規則に関する重要なヒントを示します。  
  
-   AD FS 管理スナップインで\-要求規則テンプレートを使用してルールを作成することができますのみを要求  
  
-   要求規則プロセスが受信要求の要求プロバイダーから直接、 \(Active Directory または別のフェデレーション サービスなど\)または変換要求プロバイダー信頼規則、受け入れの出力から。  
  
-   要求規則は、要求発行エンジンによって、特定の規則セット内で時系列に従って処理されます。 規則に優先順位を設定すると、特定の規則セット内の先行する規則で生成された要求をさらに調整またはフィルター処理できます。  
  
-   要求規則テンプレートでは、常に入力方向の要求の種類を指定する必要があります。 ただし、1 つの規則を使用して、要求の種類が同じ複数の要求の値を処理できます。  
  
詳細については、要求規則および要求規則セットについてを参照してください。 [、要求規則の役割](The-Role-of-Claim-Rules.md)します。 ルールの処理方法の詳細については、次を参照してください。[要求エンジンの役割](The-Role-of-the-Claims-Engine.md)します。 要求規則セットを処理する方法の詳細については、次を参照してください。[要求パイプラインの役割](The-Role-of-the-Claims-Pipeline.md)します。  
  
## <a name="pass-through-all-claim-values"></a>すべての要求の値をパススルーする  
この操作を使用すると、指定した入力方向の要求の種類と適合するすべての入力方向の要求の値が、フェデレーション サービスによって署名されているトークンに出力方向の要求として送信される前に、指定された出力方向の要求の種類にマップされます。  
  
たとえば、規則が **[すべての要求の値のパススルー]** オプション ロジックで設定されている場合、入力方向の要求の種類が Group、出力要求の種類が Role として指定されていると、発行者からのすべての入力方向の要求の値が、要求の種類が Role の新しい出力方向の要求に個別にコピーされます。  
  
## <a name="transforming-a-claim"></a>要求の変換  
用語、ad FS、*クレーム変換*を 1 つの着信を置き換えることを意味します。 要求の値を、別の送信要求の値。 この機能を可能にするのが、入力方向の要求を変換規則です。 この規則のプロパティでは、指定した入力方向の要求の種類に基づいて、入力方向の値を、別の出力方向の要求の値に変換する条件を設定できます。  
  
たとえば、次の図に示すように、入力方向の値を別の出力方向の要求の値に置き換える条件で規則が設定されている場合、入力方向の要求の種類 Group すべてが、新しい出力方向の要求に種類 Role にマップされます。 この場合、入力方向の要求の値 Purchaser は、新しい出力方向の要求の値 Admin に置き換えられます。  
  
![変換を使用するときに](media/adfs2_transform.gif)  
  
指定した電子メールとすべての入力方向の要求を置き換える条件を適用する、このルールを使用することもできます。\-電子メール サフィックスの値を新しい値。 たとえば、sales.corp.fabrikam.com のサフィックスを持つすべての要求の値を fabrikam.com に変更する条件を、この規則で設定できます。  
  
## <a name="configuring-this-rule-on-a-claims-provider-trust"></a>要求プロバイダー信頼でのこの規則の構成  
要求プロバイダー信頼を使用する場合、この規則は、要求プロバイダーからの入力方向の要求を、信頼できる同等のものに変換するように構成できます。 組織における要求の種類と要求の値の意味は、要求プロバイダー組織で使用されている意味とは異なる場合があります。 この規則を使用すると、要求プロバイダーの要求の種類と値を正規化できます。これにより、その出力方向の要求と同等のものを証明書利用者が理解することができます。  
  
## <a name="configuring-this-rule-on-a-relying-party-trust"></a>証明書利用者の信頼でのこの規則の構成  
証明書利用者信頼を使用する場合、この規則は、特定の証明書利用者の要求を変換するように構成できます。 証明書利用者によっては、要求の種類または要求の値の意味が異なる場合があります。この規則を使用すると、1 つの証明書利用者に対して、出力方向の要求の種類と値を変更することができます。  
  
## <a name="how-to-create-this-rule"></a>この規則の作成方法  
要求規則言語を使用してまたはを使用して、この規則を作成する、**入力方向の要求を変換**規則テンプレートの AD FS 管理スナップインで\-でします。 この規則テンプレートには、次の構成オプションがあります。  
  
-   要求規則名を指定する  
  
-   特定の入力方向の要求の種類を、指定した出力方向の要求の種類に変換する  
  
-   すべての要求の値をパススルーする  
  
-   入力方向の要求の値を、別の出力方向の要求の値に置き換える  
  
-   受信した電子メールを置き換える\-メールで新しい電子メール サフィックス要求\-メール サフィックス  
  
このテンプレートを作成する方法の詳細については、次を参照してください。[入力方向の要求を変換する規則を作成](https://technet.microsoft.com/library/dd807068.aspx)AD FS Deployment guide の「します。  
  
## <a name="using-the-claim-rule-language"></a>要求規則言語の使用  
出力方向の要求を複数の入力方向の要求のコンテンツから作成する必要がある場合は、代わりにカスタム規則を使用する必要があります。 出力方向の要求の値が、入力方向の要求の値に基づく必要がある場合も、その他のコンテンツを使用して、そのコンテキストでカスタム規則を使用する必要があります。 詳細については、「 [When to Use a Custom Claim Rule](When-to-Use-a-Custom-Claim-Rule.md)」を参照してください。  
  
### <a name="examples-of-how-to-construct-a-transform-rule-syntax"></a>変換規則の構文を作成する方法の例  
要求規則言語の構文を使用して要求を変換する場合、変換された要求のプロパティを、新しいリテラル値に設定できます。 たとえば、次の規則は、役割要求の値 "Administrators" を "root" に変更します。このとき、要求の種類は同じままです。  
  
```  
c:[type == “https://schemas.microsoft.com/ws/2008/06/identity/claims/role”, value == “Administrators”]  => issue(type = c.type, value = “root”);  
```  
  
正規表現を使用して、要求を変換することもできます。 たとえば、次の規則は設定ドメイン windows ユーザー名の要求でドメインで\\を FABRIKAM にユーザーの形式。  
  
```  
c:[type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name"] => issue(type = c.type, value = regexreplace(c.value, "(?<domain>[^\\]+)\\(?<user>.+)", "FABRIKAM\${user}"));  
```  
  
### <a name="best-practices-for-creating-custom-rules"></a>カスタム規則を作成するためのベスト プラクティス  
要求変換は、基本的なフィルタリング機能を使用して、選択した要求に選択的に適用できます。 フィルタリングに使用する各要求プロパティに値を割り当てることができますが、次の点に注意する必要があります。  
  
|要求のプロパティ|説明|  
|------------------|---------------|  
|Type、Value、ValueType|これらのプロパティは、割り当てによく使用されます。 少なくとも種類と値を、変換結果の要求に対して指定する必要があります。|  
|発行者|要求規則言語で要求の Issuer を設定できますが、一般的にこれはお勧めできません。 要求の発行者は、トークンでシリアル化されません。 トークンを受信すると、すべての要求の Issuer プロパティが、そのトークンに署名したフェデレーション サーバーの識別子に設定されます。 したがって、規則で要求の発行者を設定しても、トークンのコンテンツには影響がなく、その設定は、要求がトークンにパッケージされた時点で失われます。 唯一要求の発行者を設定することが理にかなっている状況は、要求プロバイダーの規則セットでこのプロパティが特定の値に設定され、証明書利用者の規則セットが、この特定の値を参照する規則を使用して作成されている場合です。 Issuer プロパティが要求規則の値に明示的に設定されていない場合、このプロパティは、要求規則要求発行エンジンによって "LOCAL AUTHORITY" に設定されます。|  
|OriginalIssuer|Issuer と同様、一般的には、OriginalIssuer にも明示的に値を割り当てないでください。 Issuer とは異なり、OriginalIssuer プロパティはトークンでシリアル化されますが、これが設定されている場合、トークンのコンシューマーは、このプロパティに、この要求を最初に発行したフェデレーション サーバーの識別子が設定されることを期待します。|  
|プロパティ|前のセクションで説明したように、要求のプロパティ バッグはトークンでは保持されません。したがって、プロパティへの割り当ては、以降のローカル ポリシーが、そのプロパティに格納されている情報を参照する場合にのみ実行します。|  
  
要求規則言語を使用する方法の詳細については、次を参照してください。[要求規則言語の役割](The-Role-of-the-Claim-Rule-Language.md)します。  
  
