---
title: Web アプリを Microsoft Intune に追加する
titleSuffix: ''
description: Web アプリ (クライアント/サーバー アプリケーション) を Microsoft Intune に追加する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f1f0c36441b98c334311bdbfa85fa725c26b675
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57393542"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Web アプリを Microsoft Intune に追加する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune では、Web アプリなど、さまざまなアプリの種類がサポートされています。 Web アプリはクライアント/サーバー アプリケーションです。 サーバーから Web アプリが提供されます。これには UI、コンテンツ、および機能が含まれます。 さらに、最新の Web ホスティング プラットフォームでは一般的にセキュリティや負荷分散などの利点が提供されます。 Web アプリは Web 上で個別に維持されます。 Microsoft Intune を使って、このアプリの種類を参照します。 また、このアプリへのアクセスを許可するユーザー グループを割り当てます。 

ユーザー用アプリを管理して割り当てるには、そのアプリを Intune に追加します。 Intune によって、ユーザーのデバイスのホーム画面に Web アプリへのショートカットが作成されます。

> [!Note]
> Web アプリは、Android 仕事用プロファイル デバイスと macOS ではサポートされていません。

## <a name="add-a-web-app-to-intune"></a>Web アプリを Intune に追加する
Web 上のアプリへのショートカットとしてアプリを Intune に追加するには、次の操作を行います。

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。  
    Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[クライアント アプリ]** を選択します。
4. **[クライアント アプリ]** ワークロード ウィンドウで、**[管理]** の **[アプリ]** を選択します。
5. **[アプリ]** ウィンドウで **[追加]** を選択します。
6. **[アプリの追加]** ウィンドウの **[アプリの種類]** ドロップダウン リストで、**[Web リンク]** という種類を選択します。
7. **[構成]** を選択します。
8. **[アプリ情報]** ウィンドウで、以下の情報を追加します。
    - **名前**: アプリの名前を入力します。この名前は会社のポータルに表示されます。 
    
        > [!NOTE]
        > アプリをデプロイしてインストールした後で、Intune Azure Portal からアプリの名前を変更すると、そのアプリを対象としてコマンドを使用できなくなります。
    
    - **説明**:アプリの説明を入力します。 この説明は会社のポータルでユーザーに表示されます。
    - **[発行元]**: このアプリの発行元の名前を入力します。
    - **[アプリ URL]**: 割り当てるアプリをホストする Web サイトの URL を入力します。
    - **[カテゴリ]**: (省略可能) 1 つ以上の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 そうすると、会社のポータルを閲覧するときに、ユーザーがアプリを探しやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]**: ユーザーがアプリを参照するとき、会社のポータルのメイン ページにアプリ スイートが目立つように表示するには、このオプションを選びます。
    - **[このリンクを開くには Managed Browser が必要です]**: Web サイトまたは Web アプリへのリンクをユーザーに割り当てて、ユーザーが Intune Managed Browser で開けるようにするには、このオプションを選びます。 このブラウザーをデバイスにインストールする必要があります。
    - **[ロゴ]**: アプリに関連付けるアイコンをアップロードします。 ユーザーが会社のポータルを参照するとき、アプリにこのアイコンが表示されます。
9. **[OK]** を選択します。
10. **[アプリの追加]** ウィンドウで **[追加]** を選択します。

> [!Note]
> ユーザーは、Android デバイスに割り当てられた Web アプリを表示するには、ホーム画面に Intune ウィジェットを追加する必要があります。
>
> 現在、iOS デバイスへの Intune Web アプリの展開は管理プロファイルに関連付けられ、手動で削除することはできません。 Intune ポータルで展開の種類を**アンインストール**に変更することができ、そうすると Web アプリを自動的に削除することができます。 ただし、アプリ割り当て意図を**アンインストール**に変更する前に展開を削除すると、デバイスが Intune から登録解除されるまで、Web アプリは永続的にデバイス上に残っています。

## <a name="next-steps"></a>次の手順

作成したアプリはアプリの一覧に表示され、選択したグループに割り当てることができるようになります。 詳細については、[アプリをグループに割り当てる方法](apps-deploy.md)に関するページを参照してください。 
