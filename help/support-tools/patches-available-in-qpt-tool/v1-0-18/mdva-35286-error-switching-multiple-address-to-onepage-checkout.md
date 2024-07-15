---
title: 'MDVA-35286: 다중 주소를 Onepage 체크아웃으로 전환하는 동안 오류 발생'
description: MDVA-35286 패치는 고객이 장바구니에 번들 제품을 가지고 있고 다중 주소 체크아웃에서 Onepage 체크아웃으로 전환하는 경우 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-35286입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 40c98735-6054-4b25-9882-e274424b203f
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-35286: 다중 주소를 Onepage 체크아웃으로 전환하는 도중 오류 발생

MDVA-35286 패치는 고객이 장바구니에 번들 제품을 가지고 있고 다중 주소 체크아웃에서 Onepage 체크아웃으로 전환하는 경우 오류가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-35286입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.4.1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.0-2.4.1-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니에 번들 제품이 있고 사용자가 다중 배송 체크아웃을 포기한 후 Onepage 체크아웃을 사용하려고 하면 오류가 표시됩니다.

<u>재현 단계</u>:

1. 고객 계정에 로그인하고 둘 이상의 번들 제품을 장바구니에 추가합니다.
1. 링크를 클릭하여 장바구니를 보고 편집합니다.
1. **여러 주소로 체크 아웃** 링크를 클릭합니다.
1. 장바구니에 추가된 제품에 대해 다른 주소를 선택하십시오.
1. **장바구니로 돌아가기**&#x200B;를 클릭합니다.
1. 장바구니에서 **체크아웃 진행**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

체크아웃 페이지로 리디렉션됩니다.

<u>실제 결과</u>:

오류 메시지가 표시됩니다. *요청을 처리하는 동안 오류가 발생했습니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
