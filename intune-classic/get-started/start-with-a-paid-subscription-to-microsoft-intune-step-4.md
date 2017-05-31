---
title: "Intune のライセンスを割り当てる | Microsoft Docs"
description: "Intune サブスクリプションのユーザーにライセンスを割り当てます"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 03/28/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 793df9f3734b84c74ecac9b8192d0b06306607e8
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="assign-intune-licenses-to-your-user-accounts"></a>ユーザー アカウントに Intune のライセンスを割り当てる

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

ユーザーを手動で追加する場合も、オンプレミスの Active Directory から同期する場合も、まず各ユーザーに Intune のライセンスを割り当ててから、Intune にデバイスを登録する必要があります。

## <a name="assign-an-intune-license-in-the-office-365-admin-center"></a>Office 365 管理センターで、Intune のライセンスを割り当てる

[Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)を使用して、手動でクラウドベースのユーザーを追加し、クラウドベースのユーザー アカウントと、オンプレミスの Active Directory から Azure AD に同期されているアカウントの両方にライセンスを割り当てることができます。

1.  テナント管理者の資格情報を使用して [Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)にサインインした後、**[ユーザー]** > **[アクティブ ユーザー]** の順に選択します。

2.  Intune ユーザー ライセンスを割り当てるユーザー アカウントを選択し、**[製品ライセンス]** > **[編集]** の順に選択します。

3.  **Intune** または **Enterprise Mobility + Security** を **[オン]** に切り替えて、**[保存]** を選択します。

4. ユーザー アカウントが、サービスを使用してデバイスを管理に登録するために必要なアクセス許可を持つようになります。

> [!NOTE]
> デバイスを登録すると、管理コンソールにユーザーが表示されます。 また、編集するユーザーのグループを一度に選択して、選択したすべてのユーザーに対してライセンスを追加したり交換することができます。

## <a name="use-school-data-sync-to-assign-licenses-to-users-in-intune-for-education"></a>School Data Sync を使って Intune for Education のユーザーにライセンスを割り当てる
教育組織の場合、School Data Sync (SDS) を使用して Intune for Education のライセンスを同期されたユーザーに割り当てることができます。 SDS プロファイルを設定するときに、Intune for Education のチェック ボックスをオンにするだけです。  

![SDS プロファイル設定の画像](./media/i4e-sds-profile-setup-setting.png)

Intune for Education のライセンスを割り当てるときは、Intune A Direct のライセンスも割り当てられることを確認してください。

![製品ライセンス設定の画像](./media/i4e-set-licenses.png)

SDS について詳しくは、「[School Data Sync と Classroom の概要](https://support.office.com/en-us/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91?ui=en-US&rs=en-US&ad=US)」をご覧ください。

## <a name="use-powershell-to-selectively-manage-ems-user-licenses"></a>PowerShell を使用して、EMS ユーザー ライセンスを選択的に管理する
Microsoft Enterprise Mobility + Security (旧 Enterprise Mobility Suite) を使用している組織には、EMS パッケージの Azure Active Directory Premium または Intune サービスのみを必要とするユーザーがいる可能性があります。 [Azure Active Directory PowerShell コマンドレット](https://msdn.microsoft.com/library/jj151815.aspx)を使用して、いずれかのサービスまたはサービスのサブセットを割り当てることができます。

EMS サービスのユーザー ライセンスを選択的に割り当てるには、[Azure Active Directory Module for Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule) がインストールされているコンピューターで管理者として PowerShell を開きます。 PowerShell は、ローカル コンピューターまたは ADFS サーバーにインストールできます。

目的のサービス プランにのみ適用される新しいライセンス SKU 定義を作成する必要があります。 これを行うには、適用しないプランを無効にします。 たとえば、Intune ライセンスを割り当てないライセンス SKU 定義を作成できます。 利用できるサービスの一覧を確認するには、次のコマンドを入力します。

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

次のコマンドを実行すると、Intune サービス プランを除外できます。 同じメソッドを使用して、セキュリティ グループ全体に展開することや、より詳細なフィルターを使用することができます。

**例 1**<br>
コマンド ラインで、新しいユーザーを作成し、ライセンスに含まれる Intune を有効にせずに EMS ライセンスを割り当てます。

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


次のコマンドで確認します。

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**例 2**<br>
ライセンスが既に割り当てられているユーザーに対して、EMS ライセンスに含まれる Intune を無効にします。

    Connect-MsolService

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -LicenseOptions $CustomEMS

次のコマンドで確認します。

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)

>[!div class="step-by-step"]

>[&larr; **Intune にユーザーを同期する**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**ユーザーとデバイスを整理する**&rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)  
