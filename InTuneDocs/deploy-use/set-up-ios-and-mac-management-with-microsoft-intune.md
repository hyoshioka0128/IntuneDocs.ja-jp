---
title: "iOS および Mac の管理をセットアップする | Microsoft Intune"
description: "Microsoft Intune で、iPad や iPhone だけでなく Mac OS X デバイスを含む iOS デバイスのモバイル デバイス管理 (MDM) を有効にします。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 11/17/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6adfb7375f9747f64e7037164f48918789bd7ee0
ms.openlocfilehash: 641d2db2bfb49ce6c4f88d823188a714e61f683c


---

# <a name="set-up-ios-and-mac-device-management"></a>iOS および Mac のデバイス管理をセットアップする
Intune では、iPad、iPhone、および Mac OS X デバイスのモバイル デバイス管理 (MDM) が有効にされ、会社の電子メールおよびアプリへのアクセス権がユーザーに付与されます。 Intune で iOS および Mac デバイスを管理するには、Apple Push Notification サービス (APNs) 証明書が必要です。 証明書を Intune に追加すると、ユーザーがポータル サイト アプリをインストールして自分のデバイスを登録できます。または管理者が[企業所有の iOS デバイス管理](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)をセットアップできます。

1.  **Intune をセットアップする**<br>
    **Microsoft Intune** を[モバイル デバイス管理機関に設定](prerequisites-for-enrollment.md#step-2-set-mdm-authority)して、MDM の設定を行うことにより、モバイル デバイス管理を準備します (この作業をまだ行っていない場合)。

2.  **証明書署名要求を取得する**<br>
    管理者として [Microsoft Intune 管理コンソール](http://manage.microsoft.com)を開き、**[管理]** &gt; **[モバイル デバイス管理]** &gt;**[iOS および Mac OS X]** &gt; **[APNs 証明書のアップロード]** の順に移動して、**[APNs 証明書要求のダウンロード]** を選択します。 証明書署名要求 (.csr) ファイルをローカルに保存します。 .csr ファイルは、Apple Push Certificates Portal からの信頼関係証明書を要求するために使用します。

    ![[APNs 証明書のアップロード] ダイアログ ボックス](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Apple Push Notification サービス証明書を取得する**<br>
    [Apple Push Certificates Portal](http://go.microsoft.com/fwlink/?LinkId=269844) に移動します。会社の Apple ID でサインインし、.csr ファイルを使用して APNs 証明書を作成します。 Apple Push Certificate Portal で **[Upload]** (アップロード) を選択すると、APNs に使用できない .json ファイルを受け取ります。 ダウンロードが完了したら、Apple Push Certificates Portal に戻り、**[Certificates for Third-Party Servers]** (サード パーティのサーバーの証明書) で、**[Download]** (ダウンロード) を選択します。

    APNs (.pem) 証明書をダウンロードして、ファイルをローカルに保存します。

    > [!NOTE]
    > この APNs 証明書は毎年 (置き換えではなく) 更新する必要があります。 この同じ Apple ID を使用して Apple の Push Certificate Portal にサインインし、証明書を更新して、このトピックの同じ手順を使用して証明書をダウンロードし、Intune にアップロードします。

4.  **APNs 証明書を Intune に追加する**<br>
    [Microsoft Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[iOS および Mac OS X]** &gt; **[APNs 証明書のアップロード]** の順に移動して、**[APNs 証明書のアップロード]** を選択します。 証明書 (.pem) ファイルに移動し、**[開く]** を選択して、**Apple ID** を入力します。 この APNs 証明書を使用して、Intune はモバイル デバイスを登録し、登録したモバイル デバイスにポリシーを適用して iOS デバイスを管理できます。

5.  **デバイスを登録して会社のリソースへのアクセスを取得する方法をユーザーに知らせる**

    エンドユーザー用の登録手順については、「[Intune に iOS デバイスを登録する](../enduser/enroll-your-device-in-intune-ios.md)」および「[Intune に Mac OS X デバイスを登録する](../enduser/enroll-your-device-in-intune-macos.md)」を参照してください。 登録プロセスでは、登録により可能になる操作、および IT 管理者が見ることのできるデバイス上のデータと見られないデータについての説明が行われます。

    その他のエンドユーザー タスクの詳細については、次の記事を参照してください。
    - [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [IOS および Mac デバイス向けのエンド ユーザー ガイダンス](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)

会社または組織でユーザーのために iOS デバイスを購入した場合は、それらのデバイスも[会社所有の iOS デバイス](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)として管理対象に登録できます。

### <a name="see-also"></a>関連項目
[Microsoft Intune で登録するための前提条件](prerequisites-for-enrollment.md)



<!--HONumber=Dec16_HO2-->

