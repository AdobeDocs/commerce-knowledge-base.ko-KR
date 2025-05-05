---
title: 필드가 회색으로 표시되는 경우 magento.com 계정의 이메일 주소를 변경하는 방법
description: 이 문서에서는 필드가 회색으로 표시될 때 [Magento.com](https://account.magento.com) 계정의 이메일 주소를 변경하는 방법에 대해 설명합니다.
exl-id: cd527203-345c-4318-8ca8-0063109b5f79
feature: Communications
source-git-commit: 123027ee291b44ad4b234e561b9c3f4156af7c90
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# 필드가 회색으로 표시되면 magento.com 계정의 이메일 주소를 변경하는 방법

이 문서에서는 다음과 같은 상황에서 필드가 회색으로 표시되면 [Magento.com](https://account.magento.com) 계정의 전자 메일 주소를 변경하는 방법에 대해 설명합니다.

* 귀하 또는 원래 사용자가 회사를 퇴사했습니다.
* 회사가 새 이메일 도메인으로 마이그레이션되었습니다.
* 메일 그룹 또는 전체 메일 주소로 전환하고 있습니다.

## 영향을 받는 제품 및 버전

* 모든 Adobe Commerce 버전 및 인프라 유형

## 원인

[Magento.com](https://account.magento.com) 계정의 전자 메일 주소가 <https://account.adobe.com>의 Adobe 계정에 연결되어 있으므로 해당 위치에서 업데이트해야 합니다.

## 이메일 주소 변경 단계

### 사례 I:

<https://account.adobe.com>에 자신의 계정이 있는 사용자의 전자 메일 주소 변경

<u>솔루션</u>

1. https://experienceleague.adobe.com/home#support에서 다음을 명시하여 [지원 요청을 제출](https://experienceleague.adobe.com/home#support):

   * 업데이트할 기존 이메일 주소
   * 새 이메일 주소
   * 새 계정의 MAGE ID(사용 가능한 경우)

1. 기존 계정에서 이메일 주소를 업데이트하려면 팀에 두 계정을 병합하도록 요청하십시오.

### 사례 2:

현재 <https://account.adobe.com>에 자신의 계정이 없는 사용자의 전자 메일 주소 변경

<u>솔루션</u>

[현재 소유자 전자 메일]의 사서함에 액세스할 수 있는 경우 Creative Cloud 사용 안내서의 [Adobe 암호 재설정 또는 변경](https://helpx.adobe.com/manage-account/using/change-or-reset-password.html) 안내에 따라 현재 소유자 전자 메일의 암호를 재설정하십시오.

1. 지침과 함께 현재 소유자의 사서함으로 전송된 암호 재설정 링크를 찾습니다.
1. 새 암호를 설정하고 전자 메일을 [새 소유자 전자 메일] (으)로 변경합니다.
1. [IMS 계정](https://account.adobe.com/)(으)로 이동하여 새 전자 메일로 로그인하고 암호를 변경합니다.
1. 전자 메일 주소와 암호를 변경한 후 [Magento.com](https://account.magento.com)(으)로 이동하여 [새 소유자 전자 메일]을 사용하여 로그인합니다.

그러나 [현재 소유자 전자 메일]로 보낸 전자 메일에 액세스할 수 없는 경우 다음 단계를 수행합니다.

1. 회사의 메일 서버 구성을 사용하여 [현재 소유자 전자 메일]에서 새 전자 메일로 전자 메일 전달을 설정합니다.
1. 이제 이전 단계를 계속 진행합니다.

## 관련 읽기

Creative Cloud 사용 안내서에서 [잊어버린 암호를 다시 설정](https://helpx.adobe.com/manage-account/using/change-or-reset-password.html)합니다.
Creative Cloud 사용 안내서에서 [계정 프로필을 업데이트](https://helpx.adobe.com/manage-account/using/edit-adobe-account-personal-profile.html)합니다.
