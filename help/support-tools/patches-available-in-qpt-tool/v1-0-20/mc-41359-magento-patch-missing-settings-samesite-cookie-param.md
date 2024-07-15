---
title: 'MC-41359 commerce 패치: 설정 SameSite 쿠키 매개 변수가 없음'
description: MC-41359 commerce 패치는 SameSite 쿠키 매개 변수 설정이 누락된 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우 사용할 수 있습니다. 패치 ID는 MC-41359입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: b48faa3f-0d9a-4d65-9abb-1573c6240635
feature: Observability
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# MC-41359 commerce 패치: 설정 SameSite 쿠키 매개 변수가 없음

MC-41359 commerce 패치는 SameSite 쿠키 매개 변수 설정이 누락된 문제를 수정합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MC-41359입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전용 패치가 만들어졌습니다.** 클라우드 인프라 2.4.2의 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.6-p1, 2.4.2, 2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

SameSite 쿠키 매개 변수의 설정이 누락되었습니다.

<u>재현 단계:</u>

사전 요구 사항:

* Chrome을 열고 chrome://flags/으로 이동합니다.
* **SameSite를 기본 쿠키로 사용** 및 **SameSite가 없는 쿠키를 보호해야 함**.
* Chrome 관리자를 엽니다.

<u>시나리오 1:</u>

1. PayPal을 사용하도록 설정합니다.
1. 앞쪽으로 가보세요
1. 장바구니에 제품을 추가합니다.
1. 체크아웃으로 이동합니다.

<u>시나리오 2:</u>

New Relic [사용](https://docs.magento.com/user-guide/reports/new-relic-reporting.html)이 있으면 모든 프론트엔드 페이지에 경고가 표시됩니다.

<u>실제 결과:</u>

브라우저 콘솔에 경고 메시지가 있습니다. *사이트 간 리소스와 연결된 쿠키가 SameSite 특성 없이 설정되었습니다.*

<u>예상 결과:</u>

&quot;lax&quot;는 쿠키 도메인에 추가하지 않아야 합니다. samesite 속성은 기본값으로 표시되어야 합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT 도구에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
