---
title: Android デバイスが暗号化されているように見える | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55935b2f69f9573d8df5ea5ca32fb4587c652b26
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57389463"
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>Android デバイスは暗号化されるように見えるが、ポータル サイトではそのように認識されていない

デバイスを暗号化する場合、自分しか知らない秘密キーを使ってデバイス上の情報をエンコードします。 これにより、承認されていないユーザーはデバイスにアクセスできません。 多くの組織では、会社のファイル、メール、またはデータにアクセスするのに、Android デバイスの暗号化を義務づけています。

## <a name="common-issues"></a>一般的な問題

新しいバージョンの Android、特に v7.0 以降では、デバイスが完全に暗号化されているかどうかを確認するスタートアップ パスコードが必要です。 デバイスの製造元によって、スタートアップ パスコードに関する説明と場所は異なります。 ほとんどの場合、この設定は "安全な起動" と呼ばれています。 

## <a name="solutions"></a>ソリューション

### <a name="add-a-startup-pin"></a>スタートアップ PIN の追加

いくつかの Android デバイスでは、デバイスがセキュリティ保護されていることを確認するためにスタートアップ PIN を作成する必要があります。 異なる製造元によるさまざまな Android のバージョンが存在します。 このオプションを有効にする設定アプリで場所を見つけることにより、この問題を解決できます。 たとえば、Samsung Galaxy S7 では、**[設定]** > **[ロック画面とセキュリティ]** > **[安全な起動]** と移動して、安全なスタートアップを有効にします。  

### <a name="encrypt-the-entire-device"></a>デバイス全体を暗号化します

一部のデバイスでは、デバイス全体と使用済み領域のみのどちらを暗号化するかを選ぶことができます。 "使用済み領域のみ" ではなく、デバイス全体の暗号化を選んでください。 既に使用済み領域のみを暗号化している場合は、次のようにします。

1. [ポータル サイトからこのデバイスを削除します](unenroll-your-device-from-intune-android.md)
2. 使用済み領域の暗号化を解除します
3. デバイス全体を暗号化します
4. デバイスを再度登録します

### <a name="downgrade-your-version-of-android"></a>Android のバージョンのダウングレード

デバイスで Android 6.0 以降にダウングレードできる場合は、ダウングレードします。 デバイスのダウングレードには、データ損失のリスクがあります。 そのため、会社のサポートに問い合わせて、この問題を解決することをお勧めします。 会社のサポートの連絡先情報は、[ポータル Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)で入手できます。

## <a name="specific-manufacturer-issues"></a>特定の製造元の問題

バージョン 7.0 以上の一部の Android デバイスでは、特定の Android プラットフォームの標準に準拠していない方法でデータを暗号化します。 これらのデバイスは、まったく新しい場合でも暗号化されているものとして表示されることがあります。 Intune では、これらのデバイスの暗号化方法はデバイスの情報を危険にさらすものとして認識します。 このリスクの原因は主として、デバイスに物理的にアクセスできる悪意のあるユーザーです。

> [!Note]
> Microsoft は製造元と協力して、テスト中に見つけた問題やユーザーから報告された問題に対処しています。 新しい情報が得られたらこの記事の内容を更新します。 

## <a name="known-devices"></a>既知のデバイス

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>更新によってこの問題を解決できる既知のデバイス

Android の最新バージョンに、デバイスを更新していない場合は、デバイスに移動**設定**アプリと選択**Update**します。 更新するまで、これらのデバイスが準拠するいないと表示可能性があります。  

- Huawei Honor 8
- Huawei P9

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>更新によってこの問題を解決できない既知のデバイス
次のデバイスでは、暗号化は常に表示され、会社のリソースにアクセスするのには使用できません。 会社のリソースにアクセスするには、別のデバイスを使用する必要があります。  

- Huawei Mate 8
- OPPO デバイス
- Vivo デバイス
- Xiaomi Mi スマートフォン
