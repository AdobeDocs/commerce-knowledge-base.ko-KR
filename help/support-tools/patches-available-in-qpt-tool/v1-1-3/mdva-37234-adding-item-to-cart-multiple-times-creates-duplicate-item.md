---
title: 'MDVA-37234: 장바구니에 항목을 여러 번 추가하면 중복 라인 항목이 만들어집니다.'
description: MDVA-37234 패치는 동일한 SKU에 항목을 장바구니에 여러 번(병렬 요청) 추가하면 동일한 장바구니 ID에 대해 중복 라인 항목이 생성되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.3이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37234입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 8f0dc249-10b2-4f2c-abca-1f5b7aea204d
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-37234: 장바구니에 항목을 여러 번 추가하면 중복 라인 항목이 만들어집니다.

MDVA-37234 패치는 동일한 SKU에 항목을 장바구니에 여러 번(병렬 요청) 추가하면 동일한 장바구니 ID에 대해 중복 라인 항목이 생성되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.3이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37234입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.3.6, 2.4.1 및 2.4.2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.5 - 2.3.7-p1 및 2.4.1 - 2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

동일한 SKU에 항목을 장바구니에 여러 번 추가(병렬 요청)하면 동일한 장바구니 ID에 대해 중복 라인 항목이 만들어집니다.

<u>재현 단계</u>:

1. SKU = simple1인 간단한 제품을 만듭니다.
1. 고객을 만듭니다.
1. GraphQL 요청을 위한 고객 토큰을 생성합니다.

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
        generateCustomerToken(
            email: "customer email"
            password: "customer password"
        )
        &lbrace;
            token
        &rbrace;
    &rbrace;
    </code>
    </pre>

1. 3단계에서 언급된 토큰을 사용하여 고객을 위한 빈 장바구니를 만드십시오.

   <pre>
    <code class="language-graphql">
    mutation&lbrace;
     createEmptyCart
    &rbrace;
    </code>
    </pre>

1. 두 개의 `addSimpleProductsToCart` 요청을 동시에 실행하는 스크립트를 만듭니다. For example:

   <pre>
    <code class="language-#!/bin/bash">
    curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MywiaWF0IjoxNjIzOTUyNjcwLCJleHAiOjE2MjM5NTYyNzB9.-fh7ysqiQTAacdB3MVvaXzFE9AmKyfF8TsVmICLJoWI" -d '{"query" : "mutation { addSimpleProductsToCart( input: { cart_id: \"S8dCF7uan1POMy0qY0Hup7tEv1AhFGdY\" cart_items: [ { data: { quantity: 2 sku: \"simple1\" } } ] } ) { cart { items { id product { name sku } quantity } } } }"}' http://magento2.3.local/graphql &
    curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MywiaWF0IjoxNjIzOTUyNjcwLCJleHAiOjE2MjM5NTYyNzB9.-fh7ysqiQTAacdB3MVvaXzFE9AmKyfF8TsVmICLJoWI" -d '{"query" : "mutation { addSimpleProductsToCart( input: { cart_id: \"S8dCF7uan1POMy0qY0Hup7tEv1AhFGdY\" cart_items: [ { data: { quantity: 1 sku: \"simple1\" } } ] } ) { cart { items { id product { name sku } quantity } } } }"}' http://magento2.3.local/graphql
    </code>
    </pre>

1. 스크립트를 실행합니다.

<u>예상 결과</u>:

장바구니에는 총 수량이 있는 하나의 제품 라인(이 경우 세 개)만 생성됩니다.

<u>실제 결과</u>:

장바구니에서 동일한 제품에 대해 두 개의 별도 라인이 생성됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 유형에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

Adobe Commerce용 품질 패치에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
