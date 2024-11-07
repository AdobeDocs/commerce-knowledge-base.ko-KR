---
title: "MDVA-40399: 동일한 주문에 대한 부분 송장을 API를 통해 동시에 생성할 수 없음"
description: MDVA-40399 패치는 동일한 주문에 대한 부분 송장을 Rest API를 통해 동시에 생성할 수 없는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40399입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 2444ba57-b30b-4fdf-9e5d-988cf7fa8dd1
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MDVA-40399: 동일한 주문에 대한 부분 인보이스는 API를 통해 동시에 생성할 수 없습니다.

MDVA-40399 패치는 동일한 주문에 대한 부분 송장을 Rest API를 통해 동시에 생성할 수 없는 문제를 수정합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-40399입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

동일한 주문에 대한 부분 송장은 Rest API를 사용하여 동시에 생성할 수 없습니다.

<u>필수 구성 요소</u>:

두 개 이상의 변형이 있는 구성 가능한 제품.

<u>재현 단계</u>:

1. 구성 가능한 제품의 두 변형을 모두 장바구니에 추가합니다.
1. 주문하십시오.
1. Rest API를 통해 주문에 대한 두 개의 송장을 동시에 생성합니다.

<u>예상 결과</u>:

* 두 개의 송장을 모두 성공적으로 생성해야 합니다.
* `sales_order_item` 테이블의 두 송장에 대해 `qty_invoiced`을(를) 업데이트해야 합니다.
* 두 제품 모두 송장 발행 수량이 있어야 합니다.

<u>실제 결과</u>:

* 두 송장이 모두 정상적으로 생성되었습니다.
* `sales_order_item` 테이블의 인보이스 중 하나에 대해 `qty_invoiced`이(가) 업데이트되지 않았습니다.
* 관리자의 **주문 보기** 페이지에서 송장 수량은 한 제품에 대해서만 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
