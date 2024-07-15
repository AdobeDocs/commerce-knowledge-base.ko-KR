---
title: 'MDVA-35356: 부분적으로 인보이스 발행된 주문을 취소한 후 스토어 크레딧 반환이 잘못됨'
description: MDVA-35356 패치는 부분적으로 인보이스 발행된 주문 취소 후 잘못된 스토어 크레딧 반환 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-35356입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.
exl-id: af37f318-0818-4393-b768-939f08b73847
feature: Invoices, Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-35356: 부분적으로 인보이스 발행된 주문을 취소한 후 스토어 크레딧 반환이 잘못됨

MDVA-35356 패치는 부분적으로 인보이스 발행된 주문 취소 후 잘못된 스토어 크레딧 반환 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-35356입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.4.1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.0-2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. 간단한 제품 3개를 만듭니다.
1. 새 사용자를 만들고 스토어 크레딧을 할당하십시오(예: 스토어 크레딧 = *$10,* 단순 제품 가격 = *$100*, *$200* 및 *$300*).
1. 위 사용자로 로그인하고 세 제품을 장바구니에 추가합니다.
1. 장바구니에서 세 제품을 확인하고 주문의 일부(예: **수표/돈 주문**&#x200B;으로 결제)에 대한 스토어 크레딧을 활용하십시오.
1. API를 통해 주문에 대해 제품 1과 제품 2에 대해 각각 하나씩, 두 개의 송장을 수행합니다.

   ```php
   //endpoint POST {\{baseUrl}}/V1/order/:orderId/invoice    //1st API call:    {    "capture": true,    "items": [    {    "order_item_id": 1,    "qty": 1    }    ],    "notify": true,    "appendComment": false    }    //2nd API call:    {    "capture": true,    "items": [    {    "order_item_id": 2,    "qty": 1    }    ],    "notify": true,    "appendComment": false    }
   ```

1. 스토어 크레딧이 첫 번째 송장에 완전히 적용됩니다.
1. 스토어 크레딧 &#x200B; 잔액은 *0*&#x200B;입니다.
1. 주문을 취소하고 두 품목의 송장이 발행되고 세 번째 품목이 취소되었는지 확인합니다.
1. 스토어 신용 잔액을 확인합니다.

<u>예상 결과</u>:

$10 스토어 크레딧에 대한 송장이 발행되었기 때문에 스토어 크레딧 잔액은 여전히 0입니다.

<u>실제 결과</u>:

전체 스토어 크레딧이 반환됩니다. 잔액은 $10입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
