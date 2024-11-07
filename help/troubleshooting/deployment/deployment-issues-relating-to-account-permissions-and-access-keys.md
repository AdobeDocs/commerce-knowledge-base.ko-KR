---
title: 계정 권한 및 액세스 키와 관련된 배포 문제
description: 이 문서에서는 액세스 키 소유권 충돌로 인해 발생하는 클라우드 인프라에 Adobe Commerce 배포 문제에 대한 해결 방법을 제공합니다.
exl-id: e8d72ebe-453f-4d18-a25e-c76e685aa667
feature: Deploy, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 계정 권한 및 액세스 키와 관련된 배포 문제

이 문서에서는 액세스 키 소유권 충돌로 인해 발생하는 클라우드 인프라에 Adobe Commerce 배포 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 지원되는 모든 버전

## 문제

<u>필수 구성 요소</u>:

Cloud 라이선스는 연락처 A(전자 메일 주소: *<u>first@e.mail</u>*)와 연결되어 있습니다.

<u>재현 단계</u>:

1. 계정에 생성된 Adobe Commerce 액세스 키(키 X)를 A에게 연락하여 클라우드에 설치합니다.
1. 연락처 B(전자 메일 주소: *<u>second@e.mail</u>*)가 계정을 사용하여 확장을 구입하고 확장을 설치하기 위한 액세스 키를 만들었습니다(키 Y).
1. 그 후 A에게 연락하여 회사를 퇴사시키고 그 후 라이선스(소유권)를 B에게 이전하였다.
1. System Integrator는 키 X를 사용하여 클라우드 환경에 확장을 설치하려고 합니다.

<u>예상 결과</u>:

확장이 정상적으로 설치되었습니다.

<u>실제 결과</u>:

배포가 실패하여 확장이 설치되지 않았습니다.

## 원인

두 키 모두 연락처 역할에 할당되어 충돌이 발생합니다.

## 솔루션

계정(원래 계정과 새 계정 모두에 자체 액세스 키가 있음)의 기본 연락처가 변경된 후 배포가 실패하고 원래 계정에서 새 계정으로 키가 전송된 경우 원래 계정에서 키를 비활성화해야 합니다. 위의 예에서 키 X는 비활성화해야 합니다.

### 액세스 키를 비활성화하는 방법

이전 키와 연결된 [Commerce Marketplace](https://marketplace.magento.com/) 계정에 대한 액세스 권한이 없는 경우 [Adobe Commerce 지원 팀에 문의](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 키를 비활성화하십시오.

이전 키와 연결된 Marketplace 계정에 액세스할 수 있는 경우 다음 단계를 수행하여 키를 비활성화하십시오.

1. 이전 계정의 자격 증명을 사용하여 [Commerce Marketplace](https://marketplace.magento.com/)에 로그인합니다.
1. 페이지 오른쪽 상단에서 계정 이름을 클릭하고 **내 프로필**&#x200B;을 선택합니다.
1. 마켓플레이스 탭에서 **액세스 키**&#x200B;를 클릭합니다.

   ![magento_products_access_keys_2.4.1.png](/help/troubleshooting/miscellaneous/assets/magento_products_access_keys_2.4.1.png)

1. 액세스 키 옆에 있는 **사용 안 함**&#x200B;을 클릭합니다.

## 관련 읽기

* 개발자 설명서에서 [인증 키를 가져옵니다](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys).
