---
title: Adobe Commerce 2.4.0 B2B 관리자가 구성 가능한 제품을 견적에 추가할 수 없음
description: 이 문서에서는 B2B Quote 를 관리할 때 Commerce 관리자의 알려진 문제에 대해 설명합니다. **SKU**별로 구성 가능한 제품을 Quote에 추가할 수 없습니다. **Quote에 추가** 버튼을 클릭하면 **Quote** 편집 페이지가 로드되지 않고 제품을 구성하고 변경 사항을 저장할 수 없습니다. 이 문제는 관리자가 **SKU**별 제품을 주문에 추가하거나 **Advanced Checkout** (**Admin** &gt; **Customers** &gt; **All Customers** &gt; **Customer Edit** &gt; **Manage Shopping Cart**)에서 **SKU**별 제품을 추가할 때도 발생합니다. 이 문제는 Adobe Commerce 2.4.1용 패치에서 해결됩니다.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B 관리자가 구성 가능한 제품을 견적에 추가할 수 없음

이 문서에서는 B2B 견적을 관리할 때 Commerce 관리자의 알려진 문제에 대해 설명합니다. 견적에 **SKU**&#x200B;별로 구성 가능한 제품을 추가할 수 없습니다. **견적에 추가** 단추를 클릭하면 **견적** 편집 페이지가 로드되지 않고 제품을 구성하고 변경 사항을 저장할 수 없습니다. 이 문제는 **SKU**&#x200B;별 제품을 주문에 추가하거나 **고급 체크아웃**&#x200B;에서 **SKU**&#x200B;별 제품을 추가할 때(**관리자** > **고객** > **모든 고객** > **고객 편집** > **장바구니 관리**) 관리에서도 발생합니다. 이 문제는 Adobe Commerce 2.4.1용 패치에서 해결됩니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.0
* 클라우드 인프라의 Adobe Commerce 2.4.0

## 문제

<u>전제 조건</u>

* Adobe Commerce 2.4.0이 설치되어 있습니다.
* B2B가 설치되었습니다.
* B2B 기능을 **회사 사용 =** *예*, **공유 카탈로그 사용 =** *아니요* 및 **B2B 견적 사용 =** *예*(으)로 설정합니다.
* 고객 계정을 만듭니다.
* 이전에 만든 고객을 회사 관리자로 사용하여 회사 계정을 만듭니다.
* **기본(일반)**&#x200B;에 할당되지 않은 간단한 제품(예: name &amp; **SKU** = TEST SIMPLE 1)을 만드십시오.
* 회사 관리자가 위에서 만든 간단한 제품을 사용하여 견적을 요청하도록 합니다(예: TEST SIMPLE 1).

<u>재현 단계</u>

1. Commerce 관리 패널로 이동합니다.
1. **판매 > 견적**(으)로 이동합니다.
1. **견적**&#x200B;을 엽니다.
1. **SKU별 제품 추가** 단추를 클릭합니다.
1. **SKU 입력 필드**&#x200B;에 다른 제품(예: TEST SIMPLE 2)의 **SKU**&#x200B;을(를) 입력하십시오.
1. **수량** 입력 필드에 올바른 수량을 입력하십시오.
1. **견적에 추가** 단추를 클릭합니다.

<u>예상 결과</u>

* 만든 제품의 이름과 **SKU**&#x200B;이(가) 포함된 **Products가 Quote에 추가되지 않음** 그리드가 예상대로 나타납니다.
* 제품이 구성된 후 관리자는 예상대로 **견적에 제품 추가** 단추를 클릭하여 **견적**&#x200B;에 추가할 수 있습니다.

<u>실제 결과</u>

* 만든 제품의 이름과 **SKU**&#x200B;을(를) 포함하는 **Products가 Quote에 추가되지 않음** 그리드가 나타나지 않습니다.
* **견적** 페이지 로드가 중단되었습니다.

## 추천

현재 B2B 견적 편집 시 이 문제에 대한 해결 방법이 없지만 주문 및 장바구니 관리의 경우 **SKU**&#x200B;별로 제품을 추가하는 대신 **제품 목록**&#x200B;에서 제품을 선택할 수 있습니다. 이 문제를 해결하기 위한 패치는 2020년 4분기 릴리스될 예정인 Adobe Commerce 2.4.1에서 사용할 수 있습니다.

## 관련 읽기

* [Adobe Commerce 2.4.0 알려진 문제: 고객의 활동에 대한 새로 고침이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: Storefront에 원시 메시지 데이터 표시](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 알려진 문제: 수출 세율이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: 주문 표시 오류](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
