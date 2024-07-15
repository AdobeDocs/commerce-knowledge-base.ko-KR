---
title: 'MDVA-41399: 고객이 위시리스트에 제품을 추가하는 경우 장바구니 관리에 액세스할 수 없음'
description: MDVA-41399 패치는 고객이 위시리스트에 제품을 추가할 경우 관리 사용자가 장바구니 관리 페이지에 액세스할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-41399입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 227653c6-2d20-4475-b973-b9fa58db815b
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-41399: 고객이 위시리스트에 제품을 추가하는 경우 장바구니 관리에 액세스할 수 없음

MDVA-41399 패치는 고객이 위시리스트에 제품을 추가할 경우 관리 사용자가 장바구니 관리 페이지에 액세스할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-41399입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객이 위시리스트에 제품을 추가하는 경우 관리자 사용자는 장바구니 관리 페이지에 액세스할 수 없습니다.

<u>필수 구성 요소</u>:

1. 두 개 이상의 제품을 만듭니다.
1. 고객을 만듭니다.
1. 개발자 모드를 활성화합니다.

<u>재현 단계</u>:

1. Storefront로 이동하여 전제 조건에서 고객으로 로그인합니다.
1. 위시리스트에 제품 추가.
1. 관리 패널로 이동하여 만든 고객 편집 페이지로 이동하고 **장바구니 관리** 단추를 클릭합니다.

<u>예상 결과</u>:

관리자 사용자는 장바구니를 관리할 수 있습니다.

<u>실제 결과</u>:

관리자가 오류 메시지를 받습니다. *오류가 발생했습니다. 자세한 내용은 오류 로그를 참조하십시오.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
