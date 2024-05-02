---
title: 'MDVA-41631: 선택적 "telephone" 값 없이 주문 정보를 검색하는 동안 오류 발생'
description: MDVA-41631 패치는 GraphQL을 통해 선택적 "전화" 값 없이 주문 정보를 검색하는 동안 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 94b0b918-c1f9-4f5d-8fcd-8b92a9ca8c59
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-41631: 선택적 &quot;telephone&quot; 값 없이 주문 정보를 검색하는 도중 오류 발생

MDVA-41631 패치는 GraphQL을 통해 선택적 &quot;전화&quot; 값 없이 주문 정보를 검색하는 동안 오류가 발생하는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7이 설치되었습니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 GraphQL을 통해 선택적 &quot;전화&quot; 값 없이 주문 정보를 검색하는 도중 오류가 발생했습니다.

<u>재현 단계</u>:

1. 다음으로 이동 **저장** > **구성** > **고객** > **고객 구성** > **이름 및 주소 옵션** > **전화 번호 표시** 전화 번호를 선택 사항으로 설정합니다.
1. GraphQL API를 로그인 고객으로 사용하여 주문합니다.
   * 청구 및 배송 주소를 설정할 때 전화 번호를 설정하지 마십시오. 에 제공된 지침을 따르십시오. [GraphQL 체크아웃 튜토리얼](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-customer.html) 개발자 설명서에서 확인할 수 있습니다.
1. GraphQL을 사용하여 주문 검색 [customerOrder 쿼리](https://devdocs.magento.com/guides/v2.4/graphql/queries/customer-orders.html).

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>예상 결과</u>:

사용자는 주문 정보를 받습니다.

<u>실제 결과</u>:

사용자에게 다음 오류가 표시됩니다. *&quot;message&quot;: &quot;내부 서버 오류&quot;,*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
