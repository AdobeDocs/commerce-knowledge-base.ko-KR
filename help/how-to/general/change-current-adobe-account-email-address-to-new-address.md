---
title: 현재 Adobe 계정 이메일 주소 변경
description: Adobe 계정에 등록된 현재 이메일 주소를 Adobe 계정 또는 Magento 계정에 현재 등록되지 않은 새 주소로 변경하는 방법을 알아봅니다.
exl-id: ca549d38-0d62-4206-9727-0ed85b733dc3
feature: Communications
source-git-commit: 8d91d4c21dc981accf25537cdb61e1271e17b78c
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 현재 Adobe 계정 이메일 주소 변경

이 문서에서는 [Adobe 계정](https://account.adobe.com/)에 등록된 현재 전자 메일 주소를 [Adobe 계정](https://account.adobe.com/) 또는 [Magento 계정](https://account.magento.com/)에 현재 등록되지 않은 새 주소로 변경하는 방법에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 메서드 및 버전)

## 사전 요구 사항

새 이메일 주소의 소유자는 현재 이메일 주소에 액세스할 수 있어야 합니다.

현재 이메일 주소에 대한 액세스 권한이 없는 경우 회사 메일 서버 구성을 사용하여 현재 소유자의 이메일에서 새 이메일로 이메일 전달을 설정합니다.

## 이메일 주소 변경 단계

이메일 주소를 변경하려면 다음 단계를 따르십시오.

1. 이전 이메일 주소에 사용된 암호를 재설정합니다. Adobe helpx에서 [잊어버린 암호 재설정](https://helpx.adobe.com/kr/manage-account/using/change-or-reset-password.html)의 지침을 따르십시오.
1. 암호 재설정 링크가 지침과 함께 현재 소유자의 사서함으로 전송됩니다.
1. [Adobe 계정 페이지](https://account.adobe.com)&#x200B;(으)로 이동하여 새 전자 메일로 로그인하고 암호를 설정합니다.

## 중요: 클라우드 계정 사용자 이름은 자동으로 업데이트되지 않습니다

클라우드 인프라에서 Adobe Commerce을 사용하는 경우 Adobe 계정이나 MAGE ID에서 전자 메일 주소를 변경해도 [클라우드 계정](https://accounts.magento.cloud)에 표시된 사용자 이름이 자동으로 업데이트되지 않습니다.

이 문서의 단계를 완료하여 Adobe 계정 이메일 주소를 변경하세요.

1. [https://accounts.magento.cloud](https://accounts.magento.cloud)에서 클라우드 계정에 로그인합니다.
1. 지원 기술 자료에서 [클라우드 계정 프로필을 업데이트하는 방법](/help/how-to/general/how-to-update-the-cloud-account-profile.md)의 단계에 따라 클라우드 계정 프로필(사용자 이름)을 수동으로 업데이트하십시오.

이렇게 하면 클라우드 계정 사용자 이름이 업데이트된 Adobe 또는 MAGE ID 이메일과 계속 일치하도록 하고 클라우드 프로젝트에 액세스하거나 시스템 알림을 받을 때 혼동을 방지할 수 있습니다.

## 이메일 변경 후 마켓플레이스 및 지원 액세스 확인

MAGE ID의 이메일 주소를 변경한 후에는 다음 단계도 완료하여 Adobe Commerce Marketplace 및 지원 센터에서 새 이메일을 올바르게 인식하도록 해야 합니다.

### Commerce Marketplace 이메일 확인

1. Commerce Marketplace 계정에 로그인하고 계정 이메일이 새 주소로 업데이트되었는지 확인합니다.
1. 전자 메일이 업데이트되지 않은 경우 Commerce Marketplace 계정 전자 메일을 수정하도록 요청하는 [지원 티켓](https://experienceleague.adobe.com/ko/support#home)을 제출하십시오.

### 지원 팀에 내부 계정 업데이트 완료 요청

1. 필요한 내부 업데이트(예: 이전 및 새 Adobe ID와 MAGE ID 간의 연결 업데이트)를 완료하도록 요청하는 [지원 티켓](https://experienceleague.adobe.com/ko/support#home)을 제출하십시오.
1. 이전 섹션에서 Commerce Marketplace 이메일이 업데이트되지 않아 지원 티켓을 이미 연 경우 동일한 티켓을 사용하여 이러한 추가 내부 업데이트를 요청할 수 있습니다.
