---
title: Microsoft Intune でスコープのタグを使ってポリシーをフィルター処理する - Azure | Microsoft Docs
description: スコープのタグを使用して、構成プロファイルを特定のロールにフィルター処理します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb57ea2ef5c99c58968ee25b3a75b2165ece787a
ms.sourcegitcommit: 0adb41c0640743d5cb726e66ad2427e3ad6faf20
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658551"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>ロールベースのアクセス制御 (RBAC) とスコープのタグを使用して、分散の IT

ロールベースのアクセス制御とスコープのタグを使用すると、適切なアクセスと可視性、適切な Intune オブジェクトを適切な管理者があることを確認します。 ロールは、どのようなアクセスを決定するオブジェクトがある管理者。 スコープのタグは、管理者に表示できるオブジェクトを決めます。

たとえば、シアトル支社の管理者が、ポリシーおよびプロファイル マネージャーの役割を割り当てられているとします。 この管理者を表示し、プロファイルとシアトルのデバイスにのみ適用されるポリシーを管理します。 これを行うにはなります。

1. シアトルのというスコープのタグを作成します。
2. ポリシーおよびプロファイル マネージャーのロールのロールの割り当てを作成します。 
    - メンバー (グループ) というシアトルの IT 管理者セキュリティ グループを = です。 このグループ内のすべての管理者は、ポリシーとプロファイルをスコープ (グループ) 内のユーザー/デバイスの管理を許可する必要があります。
    - スコープ (グループ)、セキュリティを = というシアトルのユーザーのグループ。 このグループ内のすべてのユーザー/デバイスには、自分のプロファイルとメンバー (グループ) の管理者によって管理されているポリシーを持つことができます。 
    - スコープ (タグ) シアトルを = です。 メンバー (グループ) の管理者は、シアトルのスコープのタグが設定されているデバイスを確認できます。
3. ポリシーと管理者のメンバー (グループ) にアクセスできるようにプロファイルには、シアトルのスコープのタグを追加します。
4. メンバー (グループ) の管理者に表示デバイスにシアトルのスコープのタグを追加します。 


## <a name="to-create-a-scope-tag"></a>スコープのタグを作成するには

1. Intune では、次のように選択します。**ロール** > **スコープ (タグ)** > **作成**です。

    ![スクリーン ショットでは、スコープのタグを作成します。](./media/scope-tags/create-scope-tag.png)

2. **名前**と**説明**を入力します。
3. **[作成]** を選択します。

## <a name="to-assign-a-scope-tag-to-a-role"></a>スコープのタグをロールに割り当てるには

1. Intune では、次のように選択します。**ロール** > **すべてのロール**> ロールを選択 >**割り当て** > **割り当てる**します。

    ![スクリーン ショットは、ロールにスコープを割り当てます。](./media/scope-tags/assign-scope-to-role.png)

2. 提供、**割り当て名**と**説明**します。
3. 選択**メンバー (グループ)** > **追加**> この割り当ての一部として使用するグループを選択 >**選択** >  **[Ok]** します。 mUsers このグループには、ポリシーとスコープ (グループ) 内のユーザー/デバイスのプロファイルを管理するアクセス許可があります。

    ![グループのメンバーの選択のスクリーン ショット。](./media/scope-tags/select-member-groups.png)

4. 特定のグループ セット内のユーザー/デバイスを管理する場合は、選択**スコープ (グループ)** > **選択したグループ** > **を含めるグループを選択**> グループの選択 >**選択** > **OK**。 このグループ内のすべてのユーザー/デバイスには、自分のプロファイルとメンバー (グループ) の管理者によって管理されているポリシーを持つことができます。

    ![選択範囲のグループのスクリーン ショット。](./media/scope-tags/select-scope-groups.png)

    選択する代わりに、**すべてのデバイス**、**すべてのユーザー**、または**すべてのユーザーとすべてのデバイス**します。

    ![選択範囲のグループの他のオプションのスクリーン ショット。](./media/scope-tags/scope-group-other-options.png)
    
5. 選択**スコープ (タグ)** > **追加**> このロールに追加するタグを選択 >**選択** > **OK**. メンバー (グループ) 内のユーザーには、ポリシーと同じスコープのタグが設定されているプロファイルへのアクセスがあります。

    ![スコープのタグのスクリーン ショット。](./media/scope-tags/select-scope-tags.png)

6. **[OK]** を選びます。 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>スコープのタグを構成プロファイルに追加するには
1. Intune では、次のように選択します。**デバイス構成** > **プロファイル**> プロファイルを選択します。

    ![プロファイルの選択のスクリーン ショット。](./media/scope-tags/choose-profile.png)

2. 選択**プロパティ** > **スコープ (タグ)** > **追加**します。

    ![スコープのタグの追加のスクリーン ショット。](./media/scope-tags/add-scope-tags.png)

3. **選択タグ**プロファイルに追加するタグを選択します。
4. 選択**選択** > **OK** > **保存**します。

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>アプリ構成ポリシーにスコープのタグを割り当てる
使用したデバイスの**デバイス登録の種類**設定**管理対象デバイス**:
1. 選択**クライアント アプリ** > **アプリ構成ポリシー** > アプリ構成ポリシーを選択します。
2. 選択**プロパティ** > **スコープ (タグ)** > ポリシーに割り当てるタグを選択します。

使用したデバイスの**デバイス登録の種類**設定**管理対象アプリ**:
1. 選択**クライアント アプリ** > **アプリ構成ポリシー** > アプリ構成ポリシーを選択します。
2. 選択**スコープ (タグ)** > ポリシーに割り当てるタグを選択します。


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>IOS アプリ プロビジョニング プロファイルにスコープのタグを割り当てる
1. Intune では、次のように選択します。**クライアント アプリ** > **iOS アプリ プロビジョニング プロファイル**> プロファイルを選択します。
2. 選択**プロパティ** > **スコープ (タグ)** > プロファイルに割り当てるタグを選択します。
3. 選択**選択** > **OK** > **保存**します。

## <a name="scope-tag-details"></a>スコープのタグの詳細
スコープのタグを使用する場合は、これらの詳細に注意してください。

- 現在、スコープのタグを割り当てることができます。
    - ロールの割り当て
    - デバイス コンプライアンス ポリシー
    - デバイスの構成プロファイル
    - Windows 10 更新リング
    - マネージド デバイス
    - アプリ
    - アプリ構成ポリシー] – [管理対象デバイス
    - PowerShell スクリプト
    - DEP トークン
    - iOS アプリ プロビジョニング プロファイル
- 管理者は、Intune にオブジェクトを作成するときにその管理者に割り当てられているすべてのスコープのタグが新しいオブジェクトに自動的に割り当てられます。
- Azure Active Directory ロールには、Intune RBAC は適用されません。 そのため、Intune サービス管理者とグローバル管理者ロールには、スコープ タグに関係なく、Intune への完全な管理者アクセスがあります。
- 管理者はスコープのタグのロールの割り当てでは、スコープ タグのない Intune オブジェクトもを参照してください。
- ロールの割り当て内にあるスコープのタグのみ割り当てることができます。
- ロールの割り当てのスコープ (グループ) に記載されているターゲット グループのみを実行できます。
- をロールに割り当てられているスコープのタグがある場合は、Intune オブジェクトのすべてのスコープのタグを削除できません。 少なくとも 1 つのスコープのタグが必要です。

## <a name="next-steps"></a>次の手順

ご自分の[ロール](role-based-access-control.md)と[プロファイル](device-profile-assign.md)を管理します。
