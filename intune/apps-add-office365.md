---
title: Microsoft Intune で Windows 10 デバイスに Office 365 アプリを割り当てる
titleSuffix: ''
description: Microsoft Intune を使用し、Office 365 アプリを Windows 10 デバイスにインストールする方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: c640e3e02d7d016785b87d681443b2c49f7a6281
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61507139"
---
# <a name="assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Microsoft Intune で Windows 10 デバイスに Office 365 アプリを割り当てる

アプリの割り当て、監視、構成、または保護を行うには、対象のアプリを事前に Intune に追加しておく必要があります。 使用できる[種類のアプリ](apps-add.md#app-types-in-microsoft-intune)の 1 つに Windows 10 向け Office 365 アプリがあります。 Intune でこの種類のアプリを選択することで、Windows 10 を実行し、自分で管理しているデバイスに Office 365 アプリを割り当て、インストールできます。 ライセンスを所有している場合は、Microsoft Project Online デスクトップ クライアントおよび Microsoft Visio Online Plan 2 のアプリを割り当て、インストールすることもできます。 利用できる Office 365 は、Azure 内の Intune コンソールのアプリ一覧に単一のエントリとして表示されます。

> [!NOTE]
> Microsoft Intune で展開された Office 365 ProPlus アプリをアクティブ化するには、Office 365 ProPlus ライセンスを使用する必要があります。 現時点では、Office 365 Business Edition は Intune ではサポートされていません。

## <a name="before-you-start"></a>開始する前に

> [!IMPORTANT]
> .msi Office アプリがエンド ユーザー デバイスにある場合、それらのアプリを安全にアンインストールするには **MSI 削除**機能を使用する必要があります。 そうしないと、Intune 配信の Office 365 アプリをインストールできません。

- これらのアプリを展開するデバイスでは、Windows 10 Creators Update 以降を実行している必要があります。
- Intune は、Office 365 スイートの Office アプリの追加のみをサポートします。
- Intune でアプリ スイートをインストールするときに、Office アプリが開いている場合は、インストールが失敗し、ユーザーは保存されていないファイルのデータを失う可能性があります。
- このインストール方法は、Windows 10S、Windows Home、Windows Team、Windows Holographic、Windows Holographic for Business の各デバイスではサポートされていません。
- Intune では、Intune を使用して Office 365 アプリを既に展開しているデバイス上の Microsoft Store から Office 365 デスクトップ アプリ (Office Centennial アプリとして知られる) をインストールすることをサポートしていません。 この構成をインストールすると、データが損失したり壊れたりする可能性があります。
- 必須または使用可能なアプリを複数割り当てる場合、後の割り当ては前の割り当てに追加されるのではありません。 後のアプリ割り当ては、それより前にインストールされて存在するアプリの割り当てを上書きします。 たとえば、Office アプリの最初のセットに Word が含まれ、後のセットには含まれない場合、Word はアンインストールされます。 この条件は、Visio または Project アプリケーションには適用されません。
- **[Office バージョン]**: Office の 32 ビットまたは 64 ビット バージョンのどちらを割り当てるかを選択します。 32 ビットと 64 ビットのどちらのデバイスでも 32 ビット バージョンをインストールできますが、64 ビットのデバイスには 64 ビット バージョンしかインストールできません。
- **[Remove MSI from end-user devices]** \(エンドユーザーのデバイスから MSI を削除する\): エンドユーザーのデバイスから、既にある Office .MSI アプリを削除するかどうか選択します。 エンドユーザーのデバイスに、既に .MSI アプリがある場合、インストールは成功しません。 インストールされるアプリは、**[アプリ スイートの構成]** でインストール対象として選択されたアプリに限りません。すべての Office (MSI) アプリがエンド ユーザー デバイスから削除されます。 詳細については、「[Remove existing MSI versions of Office when upgrading to Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version)」 (Office 365 ProPlus へのアップグレード時に Office の既存の MSI バージョンを削除する) を参照してください。 エンドユーザーのコンピューターに Office が Intune によって再インストールされる場合、エンド ユーザーには前の .MSI Office インストールで使用していたのと同じ言語パックが自動的に提供されます。

## <a name="get-started"></a>作業開始

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[クライアント アプリ]** を選択します。
4. **[クライアント アプリ]** ワークロード ウィンドウで、**[管理]** の **[アプリ]** を選択します。
5. **[追加]** を選択します。
6. **[アプリの追加]** ウィンドウの **[アプリの種類]** の一覧で、**[Office 365 スイート]** の **[Windows 10]** を選びます。

## <a name="select-settings-format"></a>設定の形式を選択する

**[設定の形式]** を選択することで、アプリ設定を構成するための方法を選択できます。 [設定の形式] オプション:
- 構成デザイナー
- XML データを入力する

**[構成デザイナー]** を選択すると、**[アプリの追加]** ブレードが変更され、2 つの設定オプションが追加されます。
- アプリ スイートの構成
- アプリ スイートの設定

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

**[XML データを入力する]** を選択すると、**[アプリの追加]** ブレードに **[XML データを入力する]** オプションが表示されます。 これを選択すると、**[構成ファイル]** ブレードが表示されます。 

![Office 365 構成デザイナーの追加](./media/apps-add-office365/apps-add-office365-01.png)
    
**[XML データを入力する]** オプションに関する詳細については、下の「[XML データを入力する](apps-add-office365.md#enter-xml-format)」を参照してください。

## <a name="configure-app-suite-information"></a>アプリ スイートの情報を構成する

この手順では、アプリ スイートに関する情報を指定します。 この情報は、Intune でアプリ スイートを識別し、ユーザーが会社のポータルでアプリを探す場合に役立ちます。

1. **[アプリの追加]** ウィンドウで、**[アプリ スイートの情報]** を選びます。
2. **[アプリ スイートの情報]** ウィンドウで、次のようにします。
    - **[スイート名]**: 会社のポータルに表示される、アプリ スイートの名前を入力します。 使用するスイート名はすべて一意にします。 同じアプリ スイート名が 2 つ存在する場合、会社のポータルではそのアプリのいずれかのみがユーザーに表示されます。
    - **[スイートの説明]**: アプリ スイートの説明を入力します。 たとえば、含めるように選択したアプリを一覧表示できます。
    - **[発行元]**: Microsoft が発行者として表示されます。
    - **[カテゴリ]**: (省略可能) 1 つ以上の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 この設定を行うと、会社のポータルを閲覧するときに、ユーザーがアプリ スイートを探しやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]**: ユーザーがアプリを参照するとき、会社のポータルのメイン ページにアプリ スイートが目立つように表示するには、このオプションを選びます。
    - **[情報 URL]**: このアプリに関する情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[プライバシー URL]**: このアプリのプライバシー情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[開発者]**: Microsoft が開発者として表示されます。
    - **[所有者]**: Microsoft が所有者として表示されます。
    - **[メモ]**: このアプリに関連付けるメモを入力します。
    - **[ロゴ]**: ユーザーがポータル サイトを閲覧するとき、アプリと一緒に Office 365 のロゴが表示されます。
3. **[OK]** を選択します。

## <a name="configure-app-suite"></a>アプリ スイートの構成

**[設定の形式]** ドロップダウン ボックスで **[構成デザイナー]** オプションを選択した場合、**[アプリの追加]** ブレードに **[アプリ スイートの構成]** オプションが表示されます。 デバイスに割り当てる Office アプリを選びます。

1. **[アプリの追加]** ウィンドウで、**[アプリ スイートの構成]** を選びます。
2. **[アプリ スイートの構成]** ウィンドウで、デバイスに割り当てる標準の Office アプリを選びます。  
    さらに、ライセンスを所有している場合は、Microsoft Project Online デスクトップ クライアントおよび Microsoft Visio Online Plan 2 のアプリをインストールできます。
3. **[OK]** を選択します。

## <a name="configure-app-suite-settings"></a>アプリ スイート設定の構成

**[設定の形式]** ドロップダウン ボックスで **[構成デザイナー]** を選択した場合、**[アプリの追加]** ブレードに **[アプリ スイートの設定]** オプションが表示されます。 この手順では、アプリ スイートのインストール オプションを構成します。 この設定は、スイートに追加したすべてのアプリに適用されます。

1. **[アプリの追加]** ウィンドウで、**[アプリ スイートの設定]** を選びます。
2. **[アプリ スイートの設定]** ウィンドウで、次のようにします。
    - **[Office バージョン]**: Office の 32 ビットまたは 64 ビット バージョンのどちらを割り当てるかを選択します。 32 ビットと 64 ビットのどちらのデバイスでも 32 ビット バージョンをインストールできますが、64 ビットのデバイスには 64 ビット バージョンしかインストールできません。
    - **[更新プログラム チャネル]**: デバイス上で Office を更新する方法を選択します。 さまざまな更新プログラム チャネルについて詳しくは、「[Office 365 ProPlus 更新プログラム チャネルの概要](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)」をご覧ください。 次の中から選択します。
        - **毎月**
        - **Monthly (Targeted)** \(毎月 (対象指定)\)
        - **Semi-Annual**\(半期\)
        - **Semi-Annual (Targeted)** \(半期 (対象指定)\)

        チャネルの選択後、オプションで **[特定]** を選択すると、選択されているチャネルで特定のバージョンの Office がエンド ユーザー デバイスにインストールされます。 次いで、使用する Office の **[特定バージョン]** を選択します。
        
        使用できるバージョンは随時変更されます。 そのため、新しいデプロイを作成するとき、利用できるバージョンが新しく、特定の古いバージョンを利用できないことがあります。 現在のデプロイでは引き続き古いバージョンをデプロイできますが、バージョンの一覧はチャネル単位で継続的に更新されます。
        
        デバイスのピン設定されているバージョンが更新される場合 (または他の任意のプロパティが更新される場合)、それが利用可能としてデプロイされる場合、デバイスのチェックインが発生するまでに前のバージョンがインストールされた場合は、インストール済みであるという状態が報告されます。 デバイスのチェックインが起こった場合、状態は一時的に不明に変わりますが、これはユーザーには表示されません。 ユーザーがより新しいバージョンのインストールを開始した場合、ユーザーには状態が [インストール済み] と変更され表示されます。
        
        詳細については、「[Office 365 ProPlus 更新プログラム チャネルの概要](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)」をご覧ください。

    - **[Remove MSI from end-user devices]** \(エンドユーザーのデバイスから MSI を削除する\): エンドユーザーのデバイスから、既にある Office .MSI アプリを削除するかどうか選択します。 エンドユーザーのデバイスに、既に .MSI アプリがある場合、インストールは成功しません。 インストールされるアプリは、**[アプリ スイートの構成]** でインストール対象として選択されたアプリに限りません。すべての Office (MSI) アプリがエンド ユーザー デバイスから削除されます。 詳細については、「[Remove existing MSI versions of Office when upgrading to Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version)」 (Office 365 ProPlus へのアップグレード時に Office の既存の MSI バージョンを削除する) を参照してください。 エンドユーザーのコンピューターに Office が Intune によって再インストールされる場合、エンド ユーザーには前の .MSI Office インストールで使用していたのと同じ言語パックが自動的に提供されます。 
    - **[アプリのソフトウェア ライセンス条項を自動的に受け入れる]**: エンド ユーザーにライセンス契約への承諾を要求しない場合は、このオプションを選びます。 その後、Intune で契約書を自動的に承諾します。
    - **[共有コンピューターのライセンス認証を使用]**: 複数のユーザーでコンピューターを共有する場合は、このオプションを選びます。 詳細については、[Office 365 に対する共有コンピューターのライセンス認証の概要](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus)に関するページを参照してください。
    - **[言語]**: Office は、エンド ユーザーのデバイス上の Windows にインストールされている任意のサポート言語で自動的にインストールされます。 アプリ スイートと共に追加の言語をインストールする場合は、このオプションを選択します。 <p></p>
    Intune によって管理されている Office 365 Pro Plus アプリに追加の言語を展開することができます。 使用可能な言語のリストには、言語パックの **種類** (コア、部分、校正) が含まれます。 Azure Portal で、**[Microsoft Intune]** > **[クライアント アプリ]** > **[アプリ]** > **[追加]** の順に選びます。 **[アプリの追加]** ブレードの **[アプリの種類]** 一覧で、**[Office 365 スイート]** の **[Windows 10]** を選びます。 **[アプリ スイートの設定]** ブレードで **[言語]** を選びます。 詳細については、「[Office 365 ProPlus での言語の展開の概要](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus)」を参照してください。

## <a name="enter-xml-format"></a>XML 形式を入力する

**[設定の形式]** ドロップダウン ボックスで **[XML データを入力する]** を選択した場合、**[アプリの追加]** ブレードに **[Enter XML format]\(XML 形式を入力する\)** オプションが表示されます。 詳細については、「[Office 展開ツールのオプションの構成](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)」を参照してください。

## <a name="finish-up"></a>完了

終わったら、**[アプリの追加]** ウィンドウで **[追加]** を選びます。 作成したアプリがアプリの一覧に表示されます。

## <a name="errors-during-installation-of-the-app-suite"></a>アプリ スイートのインストール中のエラー

次の表は、発生する可能性がある一般的なエラー コードとその意味を一覧表示しています。

### <a name="status-for-office-csp"></a>Office CSP の状態

| 状態 | フェーズ | 説明 |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460 (ERROR_TIMEOUT) | ダウンロード | Office 展開ツールのダウンロードに失敗しました |
| 13 (ERROR_INVALID_DATA) | - | ダウンロードした Office 展開ツールの署名を確認できません |
| CertVerifyCertificateChainPolicy からのエラー コード | - | ダウンロードした Office 展開ツールの証明書の確認に失敗しました |
| 997 | WIP | インストール |
| 0 | インストール後 | インストールが正常に完了しました |
| 1603 (ERROR_INSTALL_FAILURE) | - | 前提条件のチェックでエラーになりました。例: SaS (2016 MSI がインストールされたときに、インストールを試行した) バージョンがそれ以外と一致しない |
| 0x8000ffff (E_UNEXPECTED) | - | マシン上にクイック実行 Office がないときに、アンインストールしようとしました |
| 17002 | - | シナリオ (インストール) の完了に失敗しました。 考えられる理由: ユーザーによるインストールの取り消し、別のインストールによるインストールの取り消し、インストール中のディスク容量不足、不明な言語 ID |
| 17004 | - | 不明な SKU |


### <a name="office-deployment-tool-error-codes"></a>Office 展開ツールのエラー コード

| 通信の種類 | リターン コード | UI | メモ |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------|
| アクティブなクイック実行のインストールがないときに、アンインストールします | -2147418113、0x8000ffff または 2147549183 | エラー コード:30088-1008 エラー コード: 30125-1011 (404) | Office 展開ツール |
| MSI バージョンがインストールされているときに、インストールします | 1603 | - | Office 展開ツール |
| インストールが、ユーザーまたは別のインストールによって取り消されました | 17002 | - | クイック実行 |
| 32 ビットがインストールされているデバイス上に 64 ビットをインストールしようとします。 | 1603 | - | Office 展開ツールのリターン コード |
| 不明な SKU をインストールしようとします (有効な SKU でのみ渡す必要があるため、Office CSP の正当なユース ケースではない) | 17004 | - | クイック実行 |
| 領域不足 | 17002 | - | クイック実行 |
| クイック実行のクライアントが開始に失敗しました (原因不明) | 17000 | - | クイック実行 |
| クイック実行のクライアントがシナリオをキューに登録するのに失敗しました (原因不明) | 17001 | - | クイック実行 |

## <a name="next-steps"></a>次の手順

- 選択したグループにアプリを割り当てるには、[グループへのアプリの割り当て](/intune-azure/manage-apps/deploy-apps)に関するページをご覧ください。
