---
title: "MDVA-32449: 판매 주문 내역이 느려지거나 503 오류로 로드되지 않음"
description: MDVA-32449 패치는 판매 주문 내역이 느리게 로드되거나 로드되지 않고 503 오류가 표시되는 Adobe Commerce 문제를 해결합니다. 13000+ 고객이 B2B 회사에 할당될 때 발생하는 문제입니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12가 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.1에서 해결되었습니다.
exl-id: e3fd4db2-b706-4712-ba8e-270eaca7fdb2
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-32449: 판매 주문 내역이 느려지거나 503 오류로 로드되지 않음

MDVA-32449 패치는 판매 주문 내역이 느리게 로드되거나 로드되지 않고 503 오류가 표시되는 Adobe Commerce 문제를 해결합니다. 13000+ 고객이 B2B 회사에 할당될 때 발생하는 문제입니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.1에서 해결되었습니다.

## 영향을 받는 제품 및 버전

13000+ 고객이 B2B 회사에 할당될 때 발생하는 문제입니다.

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.4.1

**Adobe Commerce 버전과 호환:**

Adobe Commerce 온 클라우드 인프라 및 Adobe Commerce 온-프레미스 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문 내역이 매우 느리게 로드되거나 전혀 로드되지 않는 문제를 수정합니다.

<u>필수 구성 요소</u>:

B2B 회사에 할당된 13000+ 고객

<u>재현 단계</u>:

1. 회사 관리자로 상점 첫 화면에 로그인합니다.
1. 판매 주문 내역 페이지로 이동합니다.

<u>예상 결과</u>:

판매 주문 내역 페이지가 정상적으로 로드됩니다.

<u>실제 결과</u>:

페이지가 매우 느리게 로드되거나 페이지가 로드되지 않고 시간 초과 오류가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
