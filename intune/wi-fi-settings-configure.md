---
title: Microsoft Intune でデバイス用の Wi-Fi プロファイルを作成する - Azure | Microsoft Docs
description: Microsoft Intune で Wi-Fi デバイスの構成プロファイルを作成する手順を説明します。 Android、Android エンタープライズ、Android キオスク、iOS、macOS、Windows 10 以降、Windows Holographic for Business 用のプロファイルを作成します。 これらのプロファイルは、証明書を使用するための Wi-Fi 接続の作成、EAP の種類の選択、認証方法の選択、プロキシの有効化、その他に使用します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 708c4d4572d84f17a711ac6deb16c02d82b9eea7
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61514982"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Microsoft Intune でデバイスに Wi-Fi 設定を追加して使用する

Wi-Fi は、多数のモバイル デバイスがネットワークにアクセスするために使用しているワイヤレス ネットワークです。 Microsoft Intune には、組織内のユーザーとデバイスに展開できる組み込みの Wi-Fi 設定が含まれています。 この設定のグループは "プロファイル" と呼ばれ、さまざまなユーザーとグループに割り当てることができます。 割り当てると、ユーザーは自分で構成しなくても組織の Wi-Fi ネットワークにアクセスできるようになります。

たとえば、Contoso Wi-Fi という新しい Wi-Fi ネットワークをインストールします。 そして、すべての iOS デバイスをこのネットワークに接続するように設定するものとします。 その手順は次のとおりです。

1. Contoso Wi-Fi ワイヤレス ネットワークに接続するための設定が含まれる Wi-Fi プロファイルを作成します。
2. iOS デバイスのすべてのユーザーを含むグループにそのプロファイルを割り当てます。
3. ユーザーは、自分のデバイスでワイヤレス ネットワークの一覧にある新しい Contoso Wi-Fi ネットワークを見つます。 ユーザーは、選択されている認証方法を使用して、ネットワークに接続できます。

この記事では、Wi-Fi プロファイルの作成手順を説明します。 また、各プラットフォームのさまざまな設定について説明されたリンクも含まれています。

## <a name="supported-device-platforms"></a>サポートされるデバイス プラットフォーム

Wi-Fi プロファイルでは次のデバイス プラットフォームをサポートしています。

- Android 4 以降
- Android エンタープライズ、キオスク
- iOS 8.0 以降
- macOS (Mac OS X 10.11 以降)
- Windows 10 以降、Windows 10 Mobile、Windows Holographic for Business

> [!NOTE]
> Windows 8.1 を実行しているデバイスの場合は、以前に別のデバイスからエクスポートした Wi-Fi 構成をインポートできます。

## <a name="create-a-device-profile"></a>デバイス プロファイルの作成

1. [Azure portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**Microsoft Intune** を選びます。 
2. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
3. Wi-Fi プロファイルの **[名前]** と **[説明]** を入力します。
4. **[プラットフォーム]** ドロップダウン リストで、Wi-Fi 設定を適用するデバイス プラットフォームを選択します。 次のようなオプションがあります。

    - **Android**
    - **Android エンタープライズ**
    - **Android**
    - **macOS**
    - **Windows 8.1 以降**
    - **Windows 10 以降**

5. **[プロファイルの種類]** で、**[Wi-Fi]** を選択します。

    - キオスクとして実行されている **Android エンタープライズ** デバイスの場合、**[デバイスの所有者のみ]** > **[Wi-Fi]** を選択できます。
    - **Windows 8.1 以降**の場合は、**[Wi-Fi インポート]** を選択できます。 このオプションを使用すると、以前に別のデバイスからエクスポートした Wi-Fi 設定を XML ファイルとしてインポートすることができます。

6. Wi-Fi 設定の一部は、プラットフォームごとに異なります。 特定のプラットフォームの設定を確認するには、以下を選択してください。

    - [Android](wi-fi-settings-android.md)
    - [Android エンタープライズ、キオスク](wi-fi-settings-android-enterprise.md)
    - [Android](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 以降](wi-fi-settings-windows.md)
    - [Windows 8.1 以降](wi-fi-settings-import-windows-8-1.md) (Windows Holographic for Business を含む)

    ほとんどのプラットフォームには、**Basic** と **Enterprise** の設定があります。 **Basic** には、ネットワーク名や SSID などの機能が含まれます。 **Enterprise** を使うと、拡張認証プロトコル (EAP) などの詳細情報を指定できます。

7. Wi-Fi 設定の追加が終わったら、**[プロファイルの作成]** > **[作成]** を選択して、構成プロファイルを追加します。 プロファイルが作成され、プロファイル一覧に表示されます (**[デバイス構成]** > **[プロファイル]**)。

## <a name="next-steps"></a>次の手順

プロファイルは作成されますが、何も実行されません。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
