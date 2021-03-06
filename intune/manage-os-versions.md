---
title: Microsoft Intune を使用したオペレーティング システムのバージョン管理
titleSuffix: Microsoft Intune
description: Microsoft Intune を使用したプラットフォーム間でのオペレーティング システムのバージョン管理の方法を説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 361ef17b-1ee0-4879-b7b1-d678b0787f5a
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6afd4b0bb45db580f3be47680675bd268681a11
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61506374"
---
# <a name="manage-operating-system-versions-with-intune"></a>Intune を使用したオペレーティング システムのバージョン管理
最近のモバイル プラットフォームおよびデスクトップ プラットフォームでは、主要な更新プログラム、修正プログラム、および新しいバージョンが速いペースでリリースされます。 Windows 上の更新プログラムおよび修正プログラムについては、完全に管理するためのコントロールがありますが、iOS や Android などの他のプラットフォームでは、エンド ユーザーをプロセスに参加させる必要があります。  Microsoft Intune には、異なるプラットフォーム間のオペレーティング システムのバージョン管理を構築するための機能があります。

Intune は、次のような一般的なシナリオに対処するのに役立ちます。 
- エンド ユーザー デバイスのオペレーティング システムのバージョンを判断する
- 新しいオペレーティング システムのリリースを検証している間、デバイス上の組織のデータへのアクセスを制御する
- 組織で承認されたオペレーティング システムの最新バージョンにアップグレードするようにエンドユーザーに奨励または要求する
- 組織全体のオペレーティング システムの新しいバージョンへのロールアウトを管理する
  
## <a name="operating-system-version-control-using-intune-mobile-device-management-mdm-enrollment-restrictions"></a>Intune モバイル デバイス管理 (MDM) の登録制限を使用したオペレーティング システムのバージョン管理
Intune MDM の登録制限を使用すると、クライアント デバイスの登録を許可する前に、デバイスの要件を定義できます。 この目的は、組織のリソースへのアクセス権を得る前に、エンド ユーザーに準拠しているデバイスのみを登録することを義務付けることです。 デバイスの要件には、サポートされているプラットフォームで許可されるオペレーティング システムの最小バージョンと最大バージョンの両方が含まれます。
 
![プラットフォーム構成の制限ブレード](./media/os-version-platform-configurations.png) 
 
### <a name="in-practice"></a>実際
組織はデバイスの種類の制限を使用して、組織のリソースへのアクセスを制御しています。次の設定を使用します。 
1. オペレーティング システムの最小バージョンを使用して、組織内のエンド ユーザーのプラットフォームを最新かつサポートされた状態に保ちます。 
2. オペレーティング システムの最大バージョンを指定しない (制限なし) ままにするか、組織内で検証済みの最新バージョンに設定して、オペレーティング システムの新しいリリースを内部テストするための時間を確保します。

詳細については、「[デバイスの種類の制限を設定する](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions)」を参照してください。
 
## <a name="operating-system-version-reporting-and-compliance-with-intune-mdm-device-compliance-policies"></a>オペレーティング システム バージョンのレポートと Intune MDM デバイス コンプライアンス ポリシーの順守
Intune MDM デバイス コンプライアンス ポリシーでは、次のツールが提供されています。 
- コンプライアンス規則の指定
- レポートを通じたコンプライアンスの状態の表示
- デバイスの検疫と条件付きアクセスによるコンプライアンス非対応に対するアクション

登録制限と同じく、デバイス コンプライアンス ポリシーには、オペレーティング システムの最小バージョンと最大バージョンの両方が含まれています。 ポリシーには、準拠するための猶予期間をユーザーに与えるためのコンプライアンス タイムラインもあります。 デバイス コンプライアンス ポリシーは、登録済みのエンド ユーザー デバイスを組織のポリシーに準拠するように維持します。

![デバイス コンプライアンス - コンプライアンス非対応に対するアクション](./media/os-version-actions-noncompliance.png) 

### <a name="in-practice"></a>実際
組織は、登録制限と同じシナリオにデバイス コンプライアンス ポリシーを使用しています。 これらのポリシーは、組織内のユーザーのオペレーティング システムのバージョンを最新かつ検証済みの状態に維持します。 エンド ユーザーのデバイスが準拠していない状態になった場合に、エンド ユーザーのオペレーティング システムが組織でサポートされる範囲になるまで、条件付きアクセスを使用して組織のリソースへのアクセスをブロックすることができます。 エンド ユーザーには、非対応になっていることが通知され、アクセスを回復する手順が提供されます。   

詳細については、「[Intune でのデバイス コンプライアンスの概要](https://docs.microsoft.com/intune/device-compliance-get-started)」を参照してください。
 
## <a name="operating-system-version-controls-using-intune-app-protection-policies"></a>Intune アプリの保護ポリシーを使用したオペレーティング システムのバージョン管理    
Intune アプリの保護ポリシーとモバイル アプリケーション管理 (MAM) のアクセス設定では、アプリ層でのオペレーティング システムの最小バージョンを指定できます。 これにより、オペレーティング システムを指定した最小バージョンに更新するようにエンド ユーザーに通知、推奨、または要求することができます。
 
2 つのオプションがあります。 
- **警告**: 警告は、エンド ユーザーがアプリケーションの保護ポリシーまたは MAM のアクセス設定がされたアプリを、指定されたバージョンより古いオペレーティング システムのバージョンで開いた場合に、アップグレードする必要があることをエンド ユーザーに通知します。 アプリと組織のデータへのアクセスが許可されます。
  ![Android の更新の警告ダイアログの画像](./media/os-version-update-warning.png) 

- **ブロック**: ブロックは、エンド ユーザーがアプリケーションの保護ポリシーまたは MAM のアクセス設定がされたアプリを、指定されたバージョンより古いオペレーティング システムのバージョンで開いたときに、アップグレードする必要があることをエンド ユーザーに通知します。 アプリと組織のデータへのアクセスは許可されません。
  ![アプリのアクセスのブロック ダイアログの画像](./media/os-version-access-blocked.png)

### <a name="in-practice"></a>実際
現在、組織は、アプリを開いたときまたは再開したときに、アプリを最新に保つ必要性についてエンド ユーザーを教育する方法として、アプリの保護ポリシー設定を使用しています。 構成例では、エンド ユーザーは最新バージョン -1 で警告され、最新バージョン -2 でブロックされます。
 
詳細については、「[アプリ保護ポリシーを作成して割り当てる方法](https://docs.microsoft.com/intune/app-protection-policies)」を参照してください。

## <a name="managing-a-new-operating-system-version-rollout"></a>新しいオペレーティング システム バージョンのロールアウトの管理
この記事で説明されている Intune 機能を使用すると、定義したタイムライン内で、組織を新しいオペレーティング システム バージョンに移行することができます。 次の手順では、サンプルの展開モデルを提供し、ユーザーをオペレーティング システム v1 からオペレーティング システム v2 に 7 日間で移行します。
- **手順 1**: 登録制限を使用して、デバイスを登録する最小バージョンとしてオペレーティング システム v2 を要求します。 これにより、登録時に新しいエンド ユーザーのデバイスを確実に準拠させます。
- **手順 2a**:Intune アプリの保護ポリシーを使用して、アプリを開いたときまたは再開したときに、オペレーティング システム v2 が必要なことをユーザーに警告します。
- **手順 2b**: デバイス コンプライアンス ポリシーを使用して、デバイスを準拠させるための最小バージョンとしてオペレーティング システム v2 を要求します。 コンプライアンス非対応の**アクション**を使用して、猶予期間として 7 日間を与え、タイムラインと要件と共にエンド ユーザーにメールで通知を送信します。
  -  これらのポリシーは、エンド ユーザーに既存のデバイスを更新する必要があることを通知します。通知は、電子メール、Intune ポータル サイトを通じて、およびアプリの保護ポリシーが有効になっているアプリを開いたときに行われます。
  - コンプライアンス レポートを実行して、非コンプライアンスになっているユーザーを特定することができます。 
- **手順 3a**:Intune アプリの保護ポリシーを使用して、デバイスがオペレーティング システム v2 を実行していない場合、アプリを開いたときまたは再開したときにユーザーをブロックします。
- **手順 3b**:デバイス コンプライアンス ポリシーを使用して、デバイスを準拠させるための最小バージョンとしてオペレーティング システム v2 を要求します。
  - これらのポリシーでは、組織のデータに引き続きアクセスするために、デバイスを更新することが求められます。 デバイスの条件付きアクセスと共に使用すると、保護されたサービスがブロックされます。 アプリの保護ポリシーが有効になっているアプリは、開いたとき、または組織のデータにアクセスするときにブロックされます。

## <a name="next-steps"></a>次の手順
次のリソースを使用して、組織内のオペレーティング システムのバージョンを管理します。 

- [デバイスの種類の制限を設定する](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions)
- [Intune のデバイス コンプライアンス ポリシーの概要](https://docs.microsoft.com/intune/device-compliance-get-started)
- [アプリ保護ポリシーを作成して割り当てる方法](https://docs.microsoft.com/intune/app-protection-policies)
