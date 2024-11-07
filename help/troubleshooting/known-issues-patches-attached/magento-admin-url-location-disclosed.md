---
title: Adobe Commerce 관리 URL 위치 공개됨
description: 이 문서에서는 관리 패널의 URL 위치를 공개할 수 있는 Adobe Commerce 보안 문제에 대한 패치를 제공합니다. URL 위치를 알면 공격을 자동화하는 데 더 쉬워질 수 있습니다.
exl-id: fe147ad5-6019-46c1-b48c-6b957b6e1582
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Adobe Commerce 관리 URL 위치 공개됨

이 문서에서는 관리 패널의 URL 위치를 공개할 수 있는 Adobe Commerce 보안 문제에 대한 패치를 제공합니다. URL 위치를 알면 공격을 자동화하는 데 더 쉬워질 수 있습니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.X.X
* Adobe Commerce 온-프레미스 2.X.X
* Magento Open Source 2.X.X

## 문제

관리 패널의 URL 위치를 공개하는 데 사용할 수 있는 문제가 Magento Open Source 및 Adobe Commerce에서 발견되었습니다. 현재 이 문제가 직접 타협으로 이어질 것이라고 믿을 만한 근거가 없지만 URL 위치를 알면 공격을 자동화하는 것이 더 쉬워질 수 있습니다.

## 솔루션

이 문제를 해결하려면 이 문서에 첨부된 패치를 적용하십시오. 다운로드하려면 다음 링크를 클릭하십시오.

* 버전 2.1.13-2.1.17, Adobe Commerce, Magento Open Source의 경우 [PRODSECBUG-2432\_EE\_2.1.17\_composer.patch](assets/PRODSECBUG-2432_EE_2.1.17_composer.patch.zip) 다운로드
* [PRODSECBUG-2432\_EE\_2.2.8\_composer.patch](assets/PRODSECBUG-2432_EE_2.2.8_composer.patch.zip) 다운로드 - 버전 2.2.0-2.2.8의 경우 모든 버전
* [PRODSECBUG-2432\_EE\_2.3.1\_composer.patch](assets/PRODSECBUG-2432_EE_2.3.1_composer.patch.zip) 다운로드 - 버전 2.3.0-2.3.1, 모든 에디션

제품/버전에 대한 패치가 표시되지 않으면 최신 보안 릴리스로 업그레이드한 다음 패치를 적용하십시오.

Adobe은 발작 증상이 없어도 가능한 한 빨리 패치를 붙일 것을 강력히 권장합니다.

## 패치 적용 방법

지침은 [Adobe Commerce에서 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 기타 보안 권장 사항

또한 Adobe은 판매자가 2단계 인증, VPN, IP 허용 목록에 추가 등을 포함하여 관리 패널을 보호하기 위해 도구를 배포할 것을 강력히 권장합니다. 자세한 내용은 다음 블로그 및 설명서를 참조하십시오.

* Brute Force 공격에 대한 Protect에 대한 [5 즉각적인 조치](https://magento.com/security/best-practices/5-immediate-actions-protect-against-brute-force-attacks)
* [새 업데이트를 예상하는 Magento 설치 암호 Protect](https://magento.com/security/best-practices/protect-your-magento-installation-password-guessing-new-update)
* [보안 모범 사례](https://magento.com/security/best-practices/security-best-practices)
* Adobe Commerce에서 [2.4.x](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication)에 대한 2단계 인증 추가 및 구성
