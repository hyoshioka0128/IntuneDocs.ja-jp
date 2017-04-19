---
title: "Intune 移行中にアプリ保護ポリシーを構成する | Microsoft Docs"
description: "この記事では、Intune 移行中にアプリ保護ポリシーを設定するために必要な手順について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: 35543604ed68393e859517e32f5186247be001df
ms.lasthandoff: 03/27/2017


---

# <a name="phase-1-configure-app-protection-policies-optional"></a>フェーズ 1: アプリ保護ポリシーを構成する (省略可能)

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

アプリ保護ポリシーを使用すると、アプリの暗号化やアプリ アクセス時の PIN の定義、脱獄またはルート化されたデバイスでのアプリ実行の防止など、多くの保護を設定することができます。 携帯電話を紛失したり盗難に遭った場合は、モバイル アプリ保護ポリシーを適用して、個人データは保持したまま会社のデータに対して選択的にリモート ワイプを実行することができます。

アプリ保護ポリシーではアプリ レベルでセキュリティを適用し、デバイスの登録を必要としません。 Intune 登録の有無に関係なく、アプリ保護ポリシーをデバイスで使用できます。 また、サードパーティの MDM プロバイダーに登録されたデバイスでも使用できます。

## <a name="app-protection-policies-with-lob-apps"></a>LOB アプリでのアプリ保護ポリシー

[IOS](https://www.microsoft.com/en-us/download/details.aspx?id=45218&751be11f-ede8-5a0c-058c-2ee190a24fa6=True) および [Android](https://www.microsoft.com/en-us/download/details.aspx?id=47267) プラットフォーム用の [Microsoft Intune App SDK](https://docs.microsoft.com/intune/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management) や Microsoft Intune アプリ ラッピング ツールを利用して、基幹業務 (LOB) アプリに対してモバイル アプリ保護ポリシーを拡張することもできます。

## <a name="how-do-app-protection-policies-help-during-migration"></a>アプリ保護ポリシーは移行中にどのように役立つか

移行では、デバイスを以前の MDM プロバイダーから削除して、Intune に登録する必要があります。 この計画を立てて、エンド ユーザーに以前の MDM プロバイダーの利用をやめて、速やかに Intune に登録するよう働きかけます。 移行中は一部のユーザーの登録プロセスの完了が遅れて、デバイスがどちらの MDM プロバイダーでも管理されないことがあります。

この期間に会社のリソースへのアクセスを引き続き許可すると、デバイスの盗難や会社のデータの損失に対する脆弱性が高まります。また、会社のリソースへのアクセスをブロックすると、ユーザーの生産性が大きく損なわれます。

Intune では移行中の企業データの保護が提供されるため、デバイス レベルの管理が行われない期間も、引き続き会社のデータをセキュリティで保護することができます。

以前の MDM プロバイダーで条件付きアクセスを無効にしても、Intune に登録すればユーザーの生産性を維持することができます。

## <a name="task-list-for-app-protection-policies"></a>アプリ保護ポリシーのタスク一覧

-   タスク 1: [モバイル アプリ保護ポリシーを構成する準備をする](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

-   タスク 2: [モバイル アプリ保護ポリシーを作成して展開する](https://docs.microsoft.com/en-us/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)

## <a name="next-steps"></a>次のステップ 

[フェーズ 1: 移行において特に考慮すべき事項](https://docs.microsoft.com/intune/plan-design/migration-phase1-special-migration-considerations)
