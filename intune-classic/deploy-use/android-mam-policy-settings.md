---
title: "Android MAM ポリシーの設定 | Microsoft Docs"
description: "このトピックでは、Android デバイス用のモバイル アプリ管理ポリシーの設定について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 017c316ce102b71b3ef9552d8fe69181b79473de
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="android-app-protection-policy-settings-in-microsoft-intune"></a>Microsoft Intune の Android アプリ保護ポリシー設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

このトピックで説明するアプリ ポリシーの設定は、Azure Portal の **[設定]** ブレードで[構成](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)することができます。
ポリシー設定には、データ再配置設定とアクセス設定の 2 つのカテゴリがあります。 このトピックの "_**ポリシーで管理されているアプリ**_" という用語は、アプリ保護ポリシーで構成されるアプリを示します。

##  <a name="data-relocation-settings"></a>データ再配置設定

| Setting | 使用方法 | 既定値 |
|------|------|------|
| **[Android でのバックアップを禁止する]** | **[はい]** を選択すると、このアプリで職場や学校のデータを [Android バックアップ サービス](https://developer.android.com/google/backup/index.html)にバックアップできなくなります。**[いいえ]** を選択すると、このアプリで職場や学校のデータをバックアップできるようになります。| [はい] |
| **[アプリで他のアプリへのデータ転送を許可する]** | このアプリからデータを受け取ることができるアプリを指定します。 <ul><li> **ポリシーで管理されているアプリ**: 他のポリシーで管理されているアプリへの転送のみを許可します。</li> <li>**すべてのアプリ**: すべてのアプリへの転送を許可します。 </li> <li>**なし**: 他のポリシーで管理されているアプリを含め、アプリへのデータ転送を許可しません。</li></ul> <p>Intune でデータ転送先として許可される可能性のある除外対象アプリとサービスがいくつかあります。 アプリとサービスの完全な一覧については、「[データ転送の除外対象](#Data-transfer-exemptions)」を参照してください。| すべてのアプリ |
| **[アプリで他のアプリからのデータの受信を許可する]** | このアプリにデータを転送できるアプリを以下のように指定します。 <ul><li>**ポリシーで管理されているアプリ**: 他のポリシーで管理されているアプリからの転送のみを許可します。</li><li>**すべてのアプリ**: すべてのアプリからのデータ転送を許可します。</li><li>**なし**: 他のポリシーで管理されているアプリを含め、アプリからのデータ転送を許可しません。 </li></ul> <p>Intune でデータ転送元として許可される可能性のある除外対象アプリとサービスがいくつかあります。 アプリとサービスの完全な一覧については、「[データ転送の除外対象](#Data-transfer-exemptions)」を参照してください。 | すべてのアプリ |
| **[名前を付けて保存] を禁止する** | このアプリで [名前を付けて保存] オプションの使用を無効にするには、**[はい]** を選択します。 [名前を付けて保存] の使用を許可する場合は、**[いいえ]** を選択します。 <p><br>**会社のデータを保存できるストレージ サービスの選択** <br>ユーザーは、選択したサービス (OneDrive for Busines、SharePoint、ローカル ストレージ) に保存できます。 他のすべてのサービスはブロックされます。</p> | いいえ <br><br> 0 件選択済み |
| **[切り取り、コピー、および他のアプリでの貼り付けを制限する]** | このアプリで切り取り、コピー、および貼り付け操作をいつ使用できるようにするかを指定します。 次の中から選択します。 <ul><li>**ブロック**: このアプリと他のアプリの間で、切り取り、コピー、および貼り付け操作を許可しません。</li><li>**ポリシーで管理されているアプリ**: このアプリと他のポリシーで管理されているアプリ間で、切り取り、コピー、および貼り付け操作を許可します。</li><li>**貼り付けを使用する、ポリシーで管理されているアプリ**: このアプリと他のポリシーで管理されているアプリ間で切り取りまたはコピーを許可します。 任意のアプリからこのアプリへのデータの貼り付けを許可します。</li><li>**すべてのアプリ**: このアプリに対する切り取り、コピー、貼り付けに制限はありません。 | すべてのアプリ |
|**Web コンテンツを管理対象ブラウザーで表示するように制限する** | **[はい]** を選択すると、アプリ内の Web リンクが Managed Browser アプリで強制的に開かれます。 <br><br> Intune に登録していないデバイスの場合は、ポリシーで管理されているアプリ内の Web リンクを Managed Browser アプリでのみ開くことができます。 <br><br> デバイスの管理に Intune を使用している場合は、「[Microsoft Intune と Managed Browser のポリシーを使用したインターネット アクセスの管理](manage-internet-access-using-managed-browser-policies.md)」を参照してください。 | いいえ |
| **[アプリ データの暗号化]** | **[はい]** を選択すると、このアプリの職場や学校のデータを暗号化できます。 Intune では、Android キーストア システムと共に OpenSSL の 128 ビット AES 暗号化スキームを使用して、アプリ データを安全に暗号化します。 データは、ファイル I/O タスク中に同期的に暗号化されます。 デバイス ストレージ上のコンテンツは常に暗号化されます。 <br><br> この暗号化方法は FIPS 140-2 で認定されて**いません**。  | [はい] |
| **[連絡先の同期を無効にする]** | **[はい]** を選択すると、アプリでデバイス上のネイティブ連絡先アプリにデータを保存できなくなります。 **[いいえ]** を選択した場合は、アプリでデバイス上のネイティブ連絡先アプリにデータを保存できます。 <br><br>選択的ワイプを実行し、アプリから職場または学校のデータを削除すると、アプリからネイティブ連絡先アプリに直接同期されている連絡先が削除されます。 ネイティブ アドレス帳から別の外部ソースに同期された連絡先はワイプできません。 現在、これは Microsoft Outlook アプリにのみ適用されます。 | いいえ |
| **印刷を無効にする** | **[はい]** を選択すると、アプリで職場または学校のデータを印刷できなくなります。 | いいえ |

  >[!NOTE]
  >**[アプリケーション データを暗号化する]** 設定の暗号化方法は、FIPS 140-2 で認定されて**いません**。


  ## <a name="data-transfer-exemptions"></a>データ転送の除外対象

  Intune アプリ保護ポリシーによってデータ転送が許可される可能性のある除外対象のアプリとプラットフォーム サービスがいくつかあります。 たとえば、Android 上のすべての Intune 対応アプリは、モバイル デバイス画面のテキストを読み上げることができるように、Google テキスト読み上げとの間でデータを転送できる必要があります。 このリストは、セキュリティで保護された生産性向上に役立つと考えられるサービスとアプリを表しており、変更される可能性があります。

  ### <a name="full-exemptions"></a>完全除外対象

  これらのアプリとサービスは、Intune で管理されたアプリとの間のデータ転送を完全に許可されます。

  |アプリ/サービス名 | 説明 |
  | ------ | ---- |
  | com.android.phone | ネイティブの電話アプリ
  | com.android.vending | Google Play ストア |
  | com.android.documentsui | Android ドキュメント ピッカー|
  | com.google.android.webview | Outlook を含む多くのアプリに必要な [WebView](https://developer.android.com/reference/android/webkit/WebView.html)。 |
  | com.android.webview |Outlook を含む多くのアプリに必要な [WebView](https://developer.android.com/reference/android/webkit/WebView.html)。|
  | com.google.android.tts | Google テキスト読み上げ |
  | com.android.providers.settings | Android システム設定 |
  | com.azure.authenticator | 多くのシナリオで認証の成功に必要な Azure Authenticator アプリ。 |
  | com.microsoft.windowsintune.companyportal | Intune [ポータル サイト]|

  ### <a name="conditional-exemptions"></a>条件付き除外対象
  これらのアプリとサービスは、特定の条件下でのみ Intune で管理されたアプリとの間のデータ転送を許可されます。

  |アプリ/サービス名 | 説明 | 除外条件|
  | ------ | ---- | --- |
  | com.android.chrome | Google Chrome ブラウザー | Chrome は、Android 7.0 以降の一部の WebView コンポーネントで使用され、ビューから非表示になることはありません。 ただし、アプリとの間のデータ フローは常に制限されます。
  | com.skype.raider | Skype | Skype アプリは、電話を呼び出す特定のアクションでのみ使用できます。 |
  | com.android.providers.media | Android のメディア コンテンツ プロバイダー | メディア コンテンツ プロバイダーは、着信音の選択アクションでのみ使用できます。 |
  | com.google.android.gms、com.google.android.gsf | Google Play Services パッケージ | これらのパッケージは、プッシュ通知など、Google Cloud Messaging のアクションで使用できます。 |



##  <a name="access-settings"></a>アクセス設定

| Setting | 使用方法 | 既定値 |
|------|------|------|
| **[アクセスのために PIN を要求する]** | **[はい]** を選択すると、このアプリを使用する際に PIN が要求されます。 ユーザーは、職場または学校のコンテキストでアプリを初めて実行するときに、この PIN のセットアップを求められます。 既定値 = **はい**。<br><br> PIN 強度について、次の設定を構成します。 <ul><li>**PIN をリセットするまでの試行回数**: ユーザーが PIN をリセットするまでに許可される入力試行回数を指定します。 既定値は **5** です。</li><li> **単純な PIN を許可する:** **[はい]** を選択すると、1234 や 1111 などの単純な PIN シーケンスを使用できるようになります。 **[いいえ]** を選択すると、単純なシーケンスは使用できなくなります。 既定値 = **はい**。 </li><li> **PIN の長さ**: PIN シーケンスの最小桁数を指定します。 既定値 = **4**。 </li><li> **PIN の代わりに指紋を許可する (Android 6.0 以降):** **[はい]** を選択すると、アプリへのアクセスに、PIN の代わりに[指紋認証](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication)を使用できるようになります。 既定値 = **はい**。</li></ul> Android デバイスでは、PIN の代わりに [Android の指紋認証](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication)を使用して、ユーザーの身元を確かめることができます。 ユーザーが職場または学校のアカウントでこのアプリを使用しようとすると、PIN を入力する代わりに指紋認証を求められます。 </li></ul>| PIN が必要: はい <br><br> PIN のリセットの試行回数: 5 <br><br> 単純な PIN を許可する: はい <br><br> PIN の長さ: 4 <br><br> 指紋を許可する: はい |
| **[アクセスには会社の資格情報が必要]** | **[はい]** を選択すると、ユーザーは、アプリへのアクセスに、PIN を入力する代わりに職場または学校のアカウントでのサインインが求められます。 これを **[はい]** に設定すると、PIN またはタッチ ID の要件が上書きされます。  | いいえ |
| **脱獄されたデバイスまたは root 化されたデバイスで管理対象アプリが実行されることを禁止する** |このアプリが脱獄または root 化されたデバイスで実行されないようにする場合は、**[はい]** を選択します。 ユーザーは、引き続き個人のタスクにこのアプリを使用できますが、このアプリの職場または学校のデータにアクセスする場合は別のデバイスを使用する必要があります。 | Yes |
| **[(分数) 後に、アクセス要件を再確認する]** | 次の設定を構成します。 <ul><li>**タイムアウト**: これは、(ポリシーで前に定義した) アクセス要件が再確認するまでの分数です。 たとえば、管理者がポリシーの PIN をオンにした場合、ユーザーは MAM アプリを開いたときに、PIN を入力する必要があります。 この設定を使用する場合、ユーザーは任意の MAM アプリでその後の **30 分** (既定値) PIN を入力する必要がありません。</li><li>**オフラインの猶予期間**: MAM デバイスをオフラインで実行できる分数です。アプリのアクセス要件を再確認するまでの時間 (分単位) を指定します。 既定値は、**720** 分 (12 時間) です。 これが期限切れになると、アプリを実行し続けることができるよう、ユーザーはアプリにより AAD に対する認証を求められます。</li></ul>| タイムアウト: 30 <br><br> オフライン: 720 |
| **アプリ データをワイプするまでのオフライン間隔 (日)** | アプリがこの日数オフラインで実行されると (日数は管理者が定義)、アプリ自体で選択的ワイプが実行されます。 この選択的ワイプは、MAM ワイプ ワークフローで管理者が開始するのと同じワイプです。 <br><br> | 90 日間 |
| **[スクリーン キャプチャと Android Assistant をブロックする (Android 6.0 以降)]** | **[はい]** を選択すると、このアプリを使用するときに、デバイスのスクリーン キャプチャ機能と **Android Assistant** 機能がブロックされます。 また、**[はい]** を選択すると、職場または学校のアカウントでこのアプリを使用するときに、使用中のアプリ一覧プレビュー イメージがぼかし表示になります。 | いいえ |
| **Disable app PIN when device PIN is managed (デバイスの PIN が管理されるときはアプリの PIN を無効にする)** | 登録されているデバイスでデバイス ロックが検出された場合にアプリの PIN を無効にするには、**[はい]** を選択します。 | いいえ |
