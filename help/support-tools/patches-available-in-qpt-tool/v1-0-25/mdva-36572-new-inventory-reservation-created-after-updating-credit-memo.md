---
title: 'MDVA-36572: 대변 메모를 업데이트한 후 새 재고 예약이 생성됨'
description: MDVA-36572 패치는 대변 메모를 업데이트한 후 새 재고 예약이 생성되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-36572입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 6d98e1aa-0faf-4317-a6ae-386f84266b9c
feature: Inventory, Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# MDVA-36572: 대변 메모를 업데이트한 후 새 재고 예약이 생성됨


## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
클라우드 인프라의 Adobe Commerce 2.4.1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 유형) 2.3.5-2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

대변 메모 예약 갱신 관찰자는 대변 메모가 갱신될 때마다 트리거됩니다. PO와의 합의에 따라 예약 업데이트의 논리를 생성한 대변 메모에만 트리거되도록 변경했습니다. API를 통한 대변 메모 편집 가능성은 별도 티켓의 범위에서 PO에서도 검토할 것입니다.

<u>재현 단계</u>:

1. 고객 계정을 만듭니다.
1. 간단한 제품을 만듭니다.
1. 주문에 대한 신규 주문, 송장 및 대변 메모를 생성합니다.
1. 새 통합을 만듭니다.
1. inventory_reservation 테이블 확인:

   ```SQL
       select * from inventory_reservation;
       +----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
       | reservation_id | stock_id | sku      | quantity | metadata                                                                                                    |
       +----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
       |              1 |        1 | simple_1 |  -1.0000 | {"event_type":"order_placed","object_type":"order","object_id":"","object_increment_id":"000000001"}        |
       |              2 |        1 | simple_1 |   1.0000 | {"event_type":"creditmemo_created","object_type":"order","object_id":"1","object_increment_id":"000000001"} |
       +----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
       2 rows in set (0.00 sec)
   ```

1. `../rest/default/V1/creditmemo/3`(으)로 GET 요청 보내기
1. 응답 복사(예):

   ```JSON
       {
       "adjustment": 0,
       "adjustment_negative": 0,
       "adjustment_positive": 0,
       "base_adjustment": 0,
       "base_adjustment_negative": 0,
       "base_adjustment_positive": 0,
       "base_currency_code": "USD",
       "base_discount_amount": 0,
       "base_grand_total": 105,
       "base_discount_tax_compensation_amount": 0,
       "base_shipping_amount": 5,
       "base_shipping_incl_tax": 5,
       "base_shipping_tax_amount": 0,
       "base_subtotal": 100,
       "base_subtotal_incl_tax": 100,
       "base_tax_amount": 0,
       "base_to_global_rate": 1,
       "base_to_order_rate": 1,
       "billing_address_id": 2,
       "created_at": "2021-04-05 23:43:45",
       "discount_amount": 0,
       "entity_id": 1,
       "global_currency_code": "USD",
       "grand_total": 105,
       "discount_tax_compensation_amount": 0,
       "increment_id": "000000001",
       "order_currency_code": "USD",
       "order_id": 1,
       "shipping_address_id": 1,
       "shipping_amount": 5,
       "shipping_incl_tax": 5,
       "shipping_tax_amount": 0,
       "state": 2,
       "store_currency_code": "USD",
       "store_id": 1,
       "store_to_base_rate": 0,
       "store_to_order_rate": 0,
       "subtotal": 100,
       "subtotal_incl_tax": 100,
       "tax_amount": 0,
       "updated_at": "2021-04-05 23:43:45",
       "items": [
        {
            "base_cost": null,
            "base_discount_tax_compensation_amount": 0,
            "base_price": 100,
            "base_price_incl_tax": 100,
            "base_row_total": 100,
            "base_row_total_incl_tax": 100,
            "base_tax_amount": 0,
            "base_weee_tax_row_disposition": 0,
            "entity_id": 1,
            "discount_tax_compensation_amount": 0,
            "name": "simple_1",
            "order_item_id": 1,
            "parent_id": 1,
            "price": 100,
            "price_incl_tax": 100,
            "product_id": 1,
            "qty": 1,
            "row_total": 100,
            "row_total_incl_tax": 100,
            "sku": "simple_1",
            "tax_amount": 0,
            "weee_tax_applied": "[]",
            "weee_tax_applied_row_amount": 0,
            "weee_tax_row_disposition": 0
        }
       ],
       "comments": []
      }
   ```

1. `../rest/default/V1/creditmemo`(으)로 POST 요청 보내기

   ```JSON
       {
       "entity":
        --paste full response from previous step here--
       }
   ```

   >[!NOTE]
   >
   >이러한 페이로드는 복제 단순화에만 사용됩니다. 고객은 사용자 지정 특성을 업데이트한 후 동일한 문제를 얻습니다.

1. inventory_reservation 테이블 확인:

<u>실제 결과</u>:

```sql
select * from inventory_reservation;
+----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
| reservation_id | stock_id | sku      | quantity | metadata                                                                                                    |
+----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
|              1 |        1 | simple_1 |  -1.0000 | {"event_type":"order_placed","object_type":"order","object_id":"","object_increment_id":"000000001"}        |
|              2 |        1 | simple_1 |   1.0000 | {"event_type":"creditmemo_created","object_type":"order","object_id":"1","object_increment_id":"000000001"} |
|              3 |        1 | simple_1 |   1.0000 | {"event_type":"creditmemo_created","object_type":"order","object_id":"1","object_increment_id":"000000001"} |
+----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
3 rows in set (0.00 sec)
```

<u>예상 결과</u>:

동일한 대변 메모에 대한 두 번째 예약이 생성되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 유형에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
