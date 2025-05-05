---
title: "ACSD-45143: setShippingAddressesOnCart 돌연변이가 숫자 지역 코드를 '지역'으로 설정하지 않음"
description: ACSD-45143 패치는 setShippingAddressesOnCart 돌연변이로 인해 숫자 영역 코드를 "region"으로 설정할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-45143입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
exl-id: 5867ea97-7d54-486e-b5d0-bfb87f24fb80
feature: Orders, Shipping/Delivery, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-45143: setShippingAddressesOnCart 돌연변이가 숫자 지역 코드를 &#39;지역&#39;으로 설정하지 않음

ACSD-45143 패치는 setShippingAddressesOnCart 돌연변이로 인해 숫자 영역 코드를 &quot;region&quot;으로 설정할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-45143입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

setShippingAddressesOnCart 돌연변이는 숫자 지역 코드를 &quot;지역&quot;으로 설정하는 것을 허용하지 않습니다.

<u>재현 단계</u>:

1. 아래 쿼리를 사용하여 장바구니를 만듭니다.

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      createEmptyCart
    &rbrace;
    </code>
    </pre>

1. 배송 주소를 장바구니에 설정하도록 요청을 보냅니다.

   <pre>
    <code class="language-graphql">
    mutation ($cartId: String!) &lbrace;
      setShippingAddressesOnCart(
        input: &lbrace;
          cart_id: $cartId
          shipping_addresses: &lbrace;
            address: &lbrace;
              firstname: "Tomek"
              lastname: "Nowak"
              company: "Company Name"
              street: ["234 Rue de Rivoli"]
              region: "58"
              city: "Lille"
              postcode: "59800"
              country_code: "FR"
              telephone: "123-456-0000"
              save_in_address_book: false
            &rbrace;
          &rbrace;
        &rbrace;
        ) &lbrace;
          cart &lbrace;
            shipping_addresses &lbrace;
              firstname
              lastname
              company
              street
              city
              region &lbrace;
                code
                label
              &rbrace;
              postcode
              telephone
              country &lbrace;
                code
                label
              &rbrace;
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

   참고: 이 예제에서는 국가 코드를 &quot;FR&quot;로 설정하고 지역 코드를 &quot;58&quot;로 설정합니다. `directory_country_region` Db 테이블에 따르면 지역 코드 58은 &quot;Nièvre&quot;입니다.

1. 반환된 응답을 확인합니다.

<u>예상 결과</u>:

Adobe Commerce을 사용하면 GraphQL 요청에서 숫자 지역 코드를 설정할 수 있습니다.

<u>실제 결과</u>:

지역 번호가 47로 변경되었습니다.

<pre>
<code class="language-graphql">
&lbrace;
  "data": &lbrace;
    "setShippingAddressesOnCart": &lbrace;
      "cart": &lbrace;
        "shipping_addresses": &lbrack;
        &lbrace;
          "firstname": "Tomek",
          "lastname": "Nowak",
          "company": "Company Name",
          "street": &lbrack;
          "234 Rue de Rivoli"
          &rbrack;,
          "city": "Lille",
          "region": &lbrace;
            "code": "47",
            "label": "Lot-et-Garonne"
            &rbrace;,
            "postcode": "59800",
            "telephone": "123-456-0000",
            "country": &lbrace;
              "code": "FR",
              "label": "FR"
            &rbrace;
          &rbrace;
        &rbrack;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하십시오.
