---
title: 최신 Adobe Commerce 프리릴리스에 액세스할 수 없음
description: 이 문서에서는 Adobe Commerce의 최신 프리릴리스 코드를 활용하려고 할 때 발생하는 문제에 대한 솔루션을 제공합니다.
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# 최신 Adobe Commerce 프리릴리스에 액세스할 수 없음

이 문서에서는 Adobe Commerce의 최신 프리릴리스 코드를 활용하려고 할 때 발생하는 문제에 대한 솔루션을 제공합니다.

>[!NOTE]
>
>Beta 액세스에 문제가 있는 경우 [최신 Beta 버전에 액세스할 수 없음](/help/how-to/general/cannot-access-the-latest-beta-version.md) 문서를 참조하십시오.

## 문제

이 문서에서는 프리릴리스 코드 액세스와 관련된 다음 문제를 다룹니다.

* 프리릴리스 코드를 찾을 수 없습니다.
* 작성기를 사용하여 [magento.com](https://account.magento.com/customer/account/login)에서 조기 액세스 Adobe Commerce 버전을 다운로드하지 못했습니다.

## 원인

다음은 문제의 가장 일반적인 원인입니다.

* 잘못된 위치에서 조기 액세스 코드를 찾고 있습니다.
* Composer를 통해 코드에 액세스할 때 잘못된 MageID를 사용하고 있습니다.
* 계정이 프리릴리스 프로그램의 일부가 아닙니다.

## 솔루션

### 조기 액세스 코드 위치

프리릴리스 동안 릴리스 패키지는 다음 두 위치에서 사용할 수 있습니다.

1. [magento.com](https://repo.magento.com/)의 작성기에서 계정에 기본 MageID를 사용합니다. 작성기 사용 방법에 대한 자세한 내용은 개발자 설명서에서 [작성기를 사용하여 Adobe Commerce 설치](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer)를 참조하십시오.
1. [account.magento.com](https://account.magento.com/customer/account/login)의 **내 계정** > **다운로드**.

>[!NOTE]
>
>릴리스 패키지는 GA 날짜까지 GitHub에서 사용할 수 없습니다.

### 사용해야 하는 MageID

Adobe Commerce 또는 파트너 계정과 연결된 기본 MageID를 사용해야 합니다. 프리릴리스 프로그램은 공유 액세스 권한이 있는 연락처와 연결되어 있지 않습니다. 조기 액세스는 Composer 또는 [repo.magento.com](https://repo.magento.com/)을(를) 통해서만 Adobe Commerce 라이선스 또는 Partner 라이선스와 연결된 MageID로 액세스할 수 있습니다.

#### 내 MageID가 기본 ID인지 어떻게 알 수 있습니까?

**판매자용**

MageID가 기본 인지 확인하려면 다음을 시도해 보십시오.

1. [magento.com](https://account.magento.com/customer/account/login)에 로그인하고 **내 제품 및 서비스** 탭으로 이동합니다. Adobe Commerce 라이선스 정보가 여기에 표시되는지 확인하십시오.
   * Adobe Commerce 라이선스 정보가 표시되면 MageID는 기본 입니다.
   * Adobe Commerce 라이선스 정보가 표시되지 않으면 MageID에는 공유 액세스만 있습니다. 기본 ID 보유자를 확인하려면 **나와 공유**(으)로 이동하십시오. SHARENAME이 여기에 지정되어 있습니다. **계정 전환**&#x200B;을 클릭하고 SHARENAME에서 지정한 값을 선택합니다. 시작 페이지에 기본 ID 소유자의 이메일이 표시됩니다.
1. [magento.com](https://account.magento.com/customer/account/login)에서 이 정보를 찾을 수 없는 경우 Adobe 계정 팀에 문의하십시오.
1. 위의 방법 중 어느 것도 작동하지 않는 경우 [지원팀에 문의](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하십시오.

**파트너용**

MageID가 기본 인지 확인하려면 다음을 시도해 보십시오.

1. [magento.com](https://account.magento.com/customer/account/login)에 로그인하고 **내 제품 및 서비스** 탭으로 이동합니다. Partners 하위 섹션에서 활성 Partner 라이센스 정보가 표시되는지 확인합니다.
   * 활성 파트너 라이센스 정보가 표시되면 MageID는 기본 입니다. END DATE 값이 미래의 날짜인 경우 Partner 라이센스가 활성화됩니다.
   * 활성 파트너 라이선스 정보가 표시되지 않으면 MageID에는 공유 액세스만 있습니다. 기본 ID 보유자를 확인하려면 **나와 공유**(으)로 이동하십시오. SHARENAME이 여기에 지정되어 있습니다. **계정 전환**&#x200B;을 클릭하고 SHARENAME에서 지정한 값을 선택합니다. 시작 페이지에 기본 ID 소유자의 이메일이 표시됩니다.
1. [magento.com](https://account.magento.com/customer/account/login)에서 이 정보를 찾을 수 없는 경우 파트너 관리자에게 문의하십시오.
1. 위의 방법 중 어느 것도 작동하지 않는 경우 [с지원팀에 문의](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하십시오.

### 프리릴리스 프로그램의 일부가 아님

프리릴리스 액세스 프로그램에 포함되려면 조직에 올바른 상태의 활성 Adobe Commerce 또는 파트너 계정이 있어야 합니다. 이 기준을 충족하고 시험판 코드에 액세스할 수 없는 경우 MageID를 사용하여 [지원팀에 문의](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하십시오.
