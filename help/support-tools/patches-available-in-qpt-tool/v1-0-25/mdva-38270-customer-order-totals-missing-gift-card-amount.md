---
title: 'MDVA-38270: 고객 주문 합계에서 기프트 카드 금액이 누락됨'
description: MDVA-38270 패치는 기프트 카드 금액이 고객 주문 총계에 없는 경우 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38270입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: 4ab315c4-d26e-4270-a556-66601d01fb2e
feature: Gift, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# MDVA-38270: 고객 주문 합계에서 기프트 카드 금액이 누락됨

MDVA-38270 패치는 기프트 카드 금액이 고객 주문 총계에 없는 경우 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-38270입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
클라우드 인프라의 Adobe Commerce 2.4.2-p1

**Adobe Commerce 버전과 호환:**
Adobe Commerce(모든 배포 방법) 2.4.1-2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문 총량 응답에서 기프트 카드 금액이 누락되었습니다.

<u>필수 구성 요소</u>:

1. 고객 계정을 만듭니다.
1. 기프트 카드(기프트 카드로 전체 주문 가능)로 주문합니다.

<u>재현 단계</u>:

고객, 주문, 품목, 합계에 대해 고객 쿼리를 만듭니다.

```GraphQL
query {
  customer {
    orders(
      pageSize: 20
    ) {
      items {
        id
        order_date
        total {
          grand_total {
            value
            currency
          }
          total_giftcard {
              applied_balance {
                value
                currency
              }
              code
              current_balance {
                value
                currency
              }
              expiration_date
          }
        }
        status
      }
    }
  }
}
```

<u>예상 결과</u>:

`total_giftcard` 필드를 사용할 수 있습니다.

<u>실제 결과</u>:

기프트 카드 관련 필드를 사용할 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
