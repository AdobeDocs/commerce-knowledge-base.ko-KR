---
title: 'MDVA-31236: 관리자가 2FA를 설정하거나 로그인할 수 없음'
description: MDVA-31236 패치는 사용자 지정 리소스 액세스 권한이 있는 Commerce 관리자가 [2단계 인증(2FA)](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html)을 설정하거나 로그인할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12가 설치된 경우 사용할 수 있습니다.
exl-id: b75d7a19-3c17-4389-b359-7aeeb8797539
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# MDVA-31236: 관리자는 2FA를 설정하거나 로그인할 수 없음

MDVA-31236 패치는 사용자 지정 리소스 액세스 권한이 있는 Commerce 관리자가 [2단계 인증(2FA)](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html)을 설정하거나 로그인할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12가 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전:** Adobe Commerce on cloud infrastructure 2.4.0에 대한 패치가 만들어졌습니다.

**Adobe Commerce 버전과 호환:** Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.4.0-2.4.1.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자 권한이 없는 사용자는 현재 개인 2FA 액세스를 설정할 수 없습니다. Adobe Commerce에 구현된 2FA에는 두 개의 ACL 역할이 포함됩니다. 한 가지 역할은 글로벌 시스템 구성에 영향을 미치며 시스템을 구성할 때만 필요합니다. 두 번째 ACL 역할은 개별 사용자 2FA 계정에 영향을 줍니다. 관리자는 이 두 번째 유형의 2FA ACL을 구성해야 합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
