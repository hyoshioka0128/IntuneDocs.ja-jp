---
title: "Intune モバイル デバイス管理 (MDM) の移行ガイド | Microsoft Docs"
description: "このガイドでは、サードパーティの MDM プロバイダーから Microsoft Intune への移行に関連したさまざまな詳細情報を説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: cce6d997c1aad73819b8cfcf31a1505f0ce75923
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="intune-migration-guide"></a>Intune 移行ガイド

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

![Intune MDM 移行ガイド図](../media/MDM-migration-guide-art.PNG)

Intune への移行を成功させるには、まず現在の MDM 環境、ビジネスの目標、および技術的な要件を考慮した、しっかりした計画を立てる必要があります。 また、移行計画を支援し協力する関係者を確保することも重要です。

このガイドでは、サードパーティの MDM プロバイダーから Intune への移行に関連したさまざまな詳細情報を説明します。

## <a name="whats-included-in-this-guide"></a>このガイドに含まれるもの

このガイドには 2 つのフェーズが含まれます。各フェーズには、Intune MDM への移行プロセス全体を理解するうえで役立つタスク、戦略、および戦術的ガイダンスが含まれます。

-   [フェーズ 1: モバイル デバイス管理 (MDM) に Intune を準備する] (/intune-classic/plan-design/migration-phase1-prepare-intune-for-mobile-device-management)

    -   [MDM 移行要件を評価する](/intune-classic/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements)

    -   [基本的なセットアップ](/intune-classic/plan-design/migration-phase1-basic-setup)

    -   [デバイスおよびアプリ管理のポリシー](/intune-classic/plan-design/migration-phase1-configure-device-and-app-management-policies)

    -   [アプリ保護ポリシーを構成する] (/intune-classic/plan-design/migration-phase1-configure-app-protection-policies)

    -   [特殊な移行に関する考慮事項](/intune-classic/plan-design/migration-phase1-special-migration-considerations)

-   [フェーズ 2: 移行のキャンペーン](/intune-classic/plan-design/migration-phase2-migration-campaign)

    -   [情報伝達計画](/intune-classic/plan-design/migration-phase2-communication-plan)

    -   [条件付きアクセスでエンド ユーザーの導入を推進する](/intune-classic/plan-design/migration-phase2-drive-end-user-adoption-with-conditional-access)
    
    -   [標準的な移行サイクル](/intune-classic/plan-design/migration-phase2-typical-migration-cycle)
        -   [移行の監視](/intune-classic/plan-design/migration-phase2-typical-migration-cycle#monitoring-migration)
        -   [移行後](/intune-classic/plan-design/migration-phase2-typical-migration-cycle#post-migration)

## <a name="assumptions"></a>前提条件

-   概念実証 (PoC) 環境で既に Intune を評価し、組織で MDM ソリューションとして使用することを決定している。

-   Intune とその機能について、既によく理解している。 

> [!NOTE]
> 移行前に Intune についてさらに理解を深めたい場合は、[Intune の評価ガイド](/intune-classic/understand-explore/sign-up-for-30-day-trial-microsoft-intune)を確認してください。

## <a name="before-you-begin"></a>始める前に

新しい Intune 展開は、以前の MDM 展開とは異なる可能性があることを認識することが重要です。 従来の MDM サービスとは異なり、Intune では ID ドリブンのアクセス制御に重点を置いているため、組織のネットワーク境界外で使用されるモバイル デバイスから企業データへのアクセスを制御するネットワーク プロキシ アプライアンスは不要です。 Microsoft は、密接に統合されたクラウド サービス スイートである "Enterprise Mobility + Security" を通じて、クラウド内のデータ サービスを保護するソリューションを提供します。

-   [Intune の一般的な使用方法](/intune-classic/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements)を確認してください。

## <a name="next-steps"></a>次のステップ

[フェーズ 1: モバイル デバイス管理 (MDM) に Intune を準備する] (/intune-classic/plan-design/migration-phase1-prepare-intune-for-mobile-device-management)
