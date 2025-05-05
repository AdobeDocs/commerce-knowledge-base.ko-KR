---
title: 'MDVA-41631: 선택적 "telephone" 값 없이 주문 정보를 검색하는 도중 오류 발생'
description: MDVA-41631 패치는 GraphQL을 통해 선택적 "전화" 값 없이 주문 정보를 검색하는 동안 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 94b0b918-c1f9-4f5d-8fcd-8b92a9ca8c59
feature: Orders
role: Admin
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-41631: 선택적 &quot;telephone&quot; 값 없이 주문 정보를 검색하는 도중 오류 발생

MDVA-41631 패치는 GraphQL을 통해 선택적 &quot;전화&quot; 값 없이 주문 정보를 검색하는 동안 오류가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 GraphQL을 통해 선택적 &quot;전화&quot; 값 없이 주문 정보를 검색하는 도중 오류가 발생했습니다.

<u>재현 단계</u>:

1. **스토어** > **구성** > **고객** > **고객 구성** > **이름 및 주소 옵션** > **전화 번호 표시**(으)로 이동하여 전화 번호를 선택 사항으로 설정합니다.
1. GraphQL API를 로그인 고객으로 사용하여 주문합니다.
   * 청구 및 배송 주소를 설정할 때 전화 번호를 설정하지 마십시오. 개발자 설명서에서 [GraphQL 체크아웃 튜토리얼](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/)에 제공된 지침을 따르십시오.
1. GraphQL [customerOrders 쿼리](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/orders/)를 사용하여 주문을 검색합니다.

<pre>
<code class="language-graphql">
&lbrace;
  customer &lbrace;
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}})&lbrace;
        items&lbrace;
          billing_address &lbrace;
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
&rbrace;
shipping_address &lbrace;
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
&rbrace;
        &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>예상 결과</u>:

사용자는 주문 정보를 받습니다.

<u>실제 결과</u>:

사용자에게 다음 오류가 발생합니다. *&quot;message&quot;: &quot;내부 서버 오류&quot;,*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
