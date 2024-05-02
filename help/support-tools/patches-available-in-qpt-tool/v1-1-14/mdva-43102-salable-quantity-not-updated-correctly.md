---
title: 'MDVA-43102: 판매 가능 수량이 올바르게 업데이트되지 않음'
description: MDVA-43102 패치는 REST API를 통해 환불을 수행하면 판매 가능 수량이 올바르게 업데이트되지 않는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43102입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: c51bc45b-a7e0-4581-a318-9c4736e6661c
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-43102: 판매 가능 수량이 올바르게 업데이트되지 않음

MDVA-43102 패치는 REST API를 통해 환불을 수행하면 판매 가능 수량이 올바르게 업데이트되지 않는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14가 설치되었습니다. 패치 ID는 MDVA-43102입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.1 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

REST API를 사용하여 환불이 완료되면 판매 가능 수량이 올바르게 업데이트되지 않습니다.

<u>재현 단계</u>:

1. 장바구니에 항목을 추가합니다.
1. 재고 수량 및 판매 가능 수량을 확인합니다.
1. 주문을 만듭니다.
1. 필요한 경우 송장을 생성합니다.
1. 다음 페이로드를 사용하여 송장을 환불하려면 REST 요청을 실행합니다.

   * offline 메서드/order/`<order_id>`/refund
   * 온라인 방법/청구서/`<invoice_id>`/refund

   ```rest
   {
     "items": [
     {
       "order_item_id": <order_item_id>,
       "qty": 1
     }
     ],
     "notify": true,
     "arguments": {
       "shipping_amount": 5,
       "extension_attributes": {
         "return_to_stock_items": [
         <order_item_id>
         ]
       }
     }
   }
   ```

1. 물건을 배송하지 마십시오.
1. 재고 수량과 판매 가능 수량을 비교합니다. 둘 다 동일한 수량으로 업데이트해야 합니다.

<u>예상 결과</u>:

주문 배송 전 환불이 나오고, 제품이 재고로 반품되면 판매 가능 수량이 올바르게 업데이트 된다.

<u>실제 결과</u>:

주문 배송 전 환불이 가능하고, 제품이 재고로 반품되는 경우 판매 가능 수량이 업데이트되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
