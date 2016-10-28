---

title: "Android for Work ポリシーの設定 | Microsoft Intune"
description: "Intune で管理する Android for Work デバイスの設定と機能を制御するポリシーを作成します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 35a53076-74d6-486d-b201-e0da2e170008
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 32bded5047b1a08738418e3e36382eeae1a5f3b4
ms.openlocfilehash: f7c676b25f5dd5b7ee1d1d7c1b51b75a41b5c102


---

# Microsoft Intune での Android for Work ポリシー設定

Intune には、Android for Work デバイスで構成できるさまざまな全般設定が組み込まれています。

## 全般構成ポリシー

Intune **Android for Work の全般構成ポリシー**を使用して、実際の Android for Work デバイスに合わせてセキュリティと仕事用プロファイルの設定を構成してください。

探している設定がこのトピックに含まれていない場合は、OMA-URI 設定を使用してデバイスを制御できる Android カスタム ポリシーを使用して作成できます。 詳細については、このトピックで後述する「[カスタム ポリシー設定](#custom-policy-settings)」を参照してください。

> [!TIP]
> 仕事用プロファイルをプロビジョニングすると、デバイスは自動的に暗号化されます。 この設定は変更できません。

### パスワードの設定

|設定の名前|説明|
|----------------|-|
|**モバイル デバイスのロックを解除するパスワードを要求する**|管理対象デバイスでパスワードを必須にするかどうかを指定します。 次の中から選択します。<br><br>- **[Complex]** (複合) – 少なくとも 1 文字の英字、数字、および記号を含める必要があります<br>- **[英数字]** - 少なくとも 1 文字の数字と 1 文字の英字を含める必要があります<br>- **[Alphabetic]** (英字) - 少なくとも 1 文字の英字または記号を含める必要があります<br>- **[Numeric complex]** (数値複素数) – 数値の繰り返しまたは連続がないようにする必要があります<br>- **Numeric**<br><br>この設定が有効な場合、複雑さの要件はありません。|
|**パスワードの最小文字数**|パスワードの最小文字数または桁数を指定します。|
|**デバイスがロックされるまでの非アクティブな時間**|デバイスが自動的にロックされるまでのユーザーが操作していない分数を指定します。|
|**Smart Lock やその他の信頼できるエージェントを許可する**<br>(Android 6 以降)|互換性のある Android デバイスで Smart Lock 機能を制御できます。 信頼エージェントとも呼ばれるこの電話機能では、デバイスが信頼できる場所にある場合 (デバイスが特定の Bluetooth デバイスに接続したときや、NFC タグの近くにある場合など)、デバイスのロック画面のパスワードを無効化またはバイパスすることができます。この設定を使用して、ユーザーが SmartLock を構成することを禁止できます。|
|**Number of repeated sign-in failures before the work profile is removed (仕事用プロファイルを削除するまでの連続サインイン エラーの回数)**|デバイスの仕事用プロファイルを削除するまでに何回のサインイン エラーを許可するかを指定します。 この設定では、完全なデバイスのワイプは実行されません。|
|**パスワードの履歴を記憶する**|以前に使用したパスワードの再利用を禁止します。|
|**パスワードの履歴を保存する** - **前のパスワードを再利用できないようにする**|記憶される以前に使用されていたパスワードの数を指定します。|
|**パスワードの有効期限 (日数)**|デバイスのパスワードの変更が必要になるまでの日数を指定します。|
|**指紋によるロック解除を使用する**<br>(Android 6 以降)|この機能をオンにすると、デバイスのロック解除に指紋を使用できるようになります。|


### 仕事用プロファイル設定

|設定の名前|説明|
|----------------|-|
|**仕事用プロファイルと個人プロファイル間でのデータ共有を許可する**|仕事用プロファイルのアプリと、ユーザーの個人プロファイルのアプリとでデータを共有できるようにします。 次の中から選択します。<br><br>- **境界を越えて共有できないようにする**<br>- **仕事用プロファイル内のアプリは、個人プロファイルからの共有要求を処理できます**<br>- **共有の制限なし**|
|**デバイスがロックされているときに仕事用プロファイルの通知を表示しない**<br>(Android 6 以降)|デバイスがロックされているときに仕事用プロファイルからの通知を表示するかどうかを制御します。|
|**アプリの既定のアクセス許可ポリシーを設定する**<br>(Android 6 以降)|仕事用プロファイル内のすべてのアプリに対して既定のアクセス許可ポリシーを設定します。|




## カスタム ポリシー設定
Microsoft Intune **Android for Work カスタム構成ポリシー**を使用して、Android for Work デバイスで各機能の制御に使用できる OMA-URI 設定を展開します。 これらの設定は、多くのデバイス製造元がデバイスの機能を制御するために使用する標準の設定です。

この機能は、Intune ポリシーで構成できない Android 設定を展開できるようにするためのものです。

> [!NOTE]
> 現時点で Android カスタム ポリシーは、事前共有キーを含む、Android デバイスの Wi-Fi 設定の構成のみをサポートしています。

### 全般設定

|設定の名前|説明|
    |----------------|--------------------|
    |**名前**|Android カスタム ポリシーの一意の名前を入力すると、Intune コンソール内で容易に識別できます。|
    |**説明**|Android カスタム ポリシーの概要や、ポリシーを特定するのに役立つその他の関連情報についての説明を入力します。|

### OMA-URI 設定

   |設定の名前|説明|
    |--------|--------------------|
    |**設定の名前**|OMA-URI 設定の一意の名前を入力すると、設定リスト内で容易に識別できます。|
    |**設定の説明**|設定の概要と、それを特定するために役立つその他の関連情報についての説明を入力します。|
    |**データ型**|この OMA-URI 設定を指定するデータ型を選択します。 **[文字列]、[文字列 (XML)]、[日付と時刻]、[整数]、[浮動小数点]**、または **[ブール値]** から選択します。|
    |**OMA-URI (大文字と小文字を区別する)**|設定対象の OMA-URI を指定します。|
    |**値**|以前に指定した OMA-URI に関連付ける値を指定します。|

### 例

- [事前共有キーを使用した Wi-Fi プロファイルの作成](pre-shared-key-wi-fi-profile.md)
- [カスタム ポリシーを使用して、Android デバイスにアプリごとの VPN プロファイルを作成する](per-app-vpn-for-android-pulse-secure.md)

### 関連項目
[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)


<!--HONumber=Oct16_HO2-->

