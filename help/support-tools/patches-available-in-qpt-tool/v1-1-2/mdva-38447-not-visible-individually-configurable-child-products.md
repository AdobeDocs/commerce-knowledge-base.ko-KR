---
title: 'MDVA-38447: "개별적으로 표시되지 않음" 구성 가능한 하위 제품이 GraphQL 응답과 느린 MySQL 쿼리에서 반환됩니다.'
description: MDVA-38447 Adobe Commerce 패치를 사용하면 "개별적으로 보이지 않음" 구성 가능한 하위 제품이 GraphQL 응답에서 반환되고 범주 필터를 사용하여 GraphQL 제품 쿼리에 대한 MySQL 쿼리가 느려지는 문제가 해결됩니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38447입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 302e7458-d9ea-466a-a2ac-d86a8ee3eca3
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-38447: &quot;개별적으로 표시되지 않음&quot; 구성 가능한 하위 제품이 GraphQL 응답에서 반환되고 MySQL 쿼리가 느려집니다.

MDVA-38447 Adobe Commerce 패치를 사용하면 &quot;개별적으로 보이지 않음&quot; 구성 가능한 하위 제품이 GraphQL 응답에서 반환되고 범주 필터를 사용하여 GraphQL 제품 쿼리에 대한 MySQL 쿼리가 느려지는 문제가 해결됩니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-38447입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.3

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

&quot;개별적으로 보이지 않음&quot; 구성 가능한 하위 제품이 GraphQL 응답에서 반환되고 범주 필터가 있는 GraphQL 제품에 대한 느린 MySQL 쿼리가 반환됩니다.

<u>필수 구성 요소</u>:

B2B 모듈을 설치해야 합니다.

<u>재현 단계</u>:

1. 간단한 제품이 **개별적으로 표시되지 않음**(으)로 설정된 구성 가능한 제품을 만듭니다.
1. **전체 색인 재지정**&#x200B;을 실행합니다.
1. 다음과 같이 **GraphQL 쿼리**&#x200B;를 실행합니다.

<pre>쿼리 getFilteredProducts(
  $filter: ProductAttributeFilterInput
  $sort: ProductAttributeSortInput!
  $search: 문자열
  $pageSize: 정수!
  $currentPage: Int!
) {
  products(
    필터: $filter
    정렬: $sort
    검색: $search
    pageSize: $pageSize
    currentPage: $currentPage
  ) {
    total_count
    page_info {
      total_pages
      current_page
      page_size
    }
    항목 {
      이름
      sku
    }
  }
}</pre>

변수:

<pre>{"filter":{"user_group":{"eq":"}},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>예상 결과</u>:

가시성이 &quot;개별적으로 보이지 않음&quot;으로 설정된 제품은 응답으로 반환되지 않습니다.

<u>실제 결과</u>:

가시성이 &quot;개별적으로 표시되지 않음&quot;으로 설정된 제품이 응답으로 반환됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 유형에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

Adobe Commerce용 품질 패치에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
