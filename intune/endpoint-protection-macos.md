---
title: Microsoft Intune - Azure で macOS のエンドポイント保護を追加する | Microsoft Docs
description: macOS デバイスで、ゲートキーパーを利用し、Mac App Store など、アプリをインストールできる場所を決定します。 他にも、ファイアウォールを有効にして (あるいは構成して) 特定のアプリを許可または禁止したり、ステルス モードを利用したり、さらには Microsoft Intune を利用し、特定の種類の着信接続をブロックしたりします。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2c3a33b996a68263550fc05d3af853c263c930a
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565942"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Intune の macOS エンドポイント保護設定

この記事では、macOS を実行するデバイスに構成できるすべてのエンドポイント保護設定について説明します。 これらの設定には、macOS を実行するデバイスのゲートキーパー設定とファイアウォール設定が含まれており、Microsoft Intune のデバイス プロファイルを利用して構成できます。

## <a name="gatekeeper"></a>ゲートキーパー

- **[これらの場所からダウンロードされたアプリを許可します]**: アプリがダウンロードされた場所によってアプリを制限します。 この意図はマルウェアからデバイスを守ることにあり、信頼されているソースからのアプリのみ許可します。 次の選択肢があります。 
  - **Mac App Store**
  - **[Mac App Store and identified developers]\(Mac App Store と確認済みの開発者\)**
  - **[どこでも]**

- **[ユーザーはゲートキーパーをオーバーライドできます]**: ユーザーがゲートキーパー設定をオーバーライドすることを禁止し、Control キーを押しながらクリックしてアプリをインストールすることを防止します。 有効にすると、ユーザーはあらゆるアプリを Control キーを押しながらクリックし、インストールできます。

## <a name="firewall"></a>ファイアウォール

ファイアウォールを利用し、ポート別ではなく、アプリケーション別に接続を制御します。 アプリケーション別の設定を利用することで、ファイアウォール保護の長所を簡単に引き出すことができます。 また、正しいアプリのために開いているネットワーク ポートが望ましくないアプリに支配されるのを防ぎます。

- **[アプリごとに接続を制御して、承認されていないネットワーク アクセスからデバイスを保護するためにファイアウォールを使用します。]**
  - **[ファイアウォール]**: ファイアウォールを有効にして、ご利用の環境における着信接続の処理方法を構成します。
  - **[着信接続]**: DHCP、Bonjour、IPSec など、基本的なインターネット サービスに必要な接続を除き、すべての着信接続をブロックします。 この機能によって、ファイル共有や画面共有など、あらゆるすべての共有サービスもブロックされます。 共有サービスを利用している場合、この設定を **[未構成]** にしてください。

- **[Allow or block incoming connections for specific apps]\(特定のアプリの着信接続を許可または禁止する\)**
  - **[許可されたアプリ]**: 着信接続を受け入れることが明示的に許可されているアプリを選択します。
  - **[ブロックされたアプリ]**: 着信接続を禁止しなければならないアプリを選択します。
  - **[ステルス モード]**: コンピューターがプローブ要求に応答するのを防ぐには、ステルス モードを有効にします。 デバイスは引き続き、許可されているアプリに関する着信要求に応答します。 ICMP (ping) などの予期しない要求は無視されます。
