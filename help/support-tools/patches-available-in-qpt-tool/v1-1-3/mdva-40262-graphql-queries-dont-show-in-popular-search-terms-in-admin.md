---
title: "MDVA-40262: GraphQL 쿼리가 관리자의 인기 검색어에 표시되지 않음"
description: MDVA-40262 Adobe Commerce 품질 패치는 GraphQL 검색 쿼리가 관리자의 인기 검색어에 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.3이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40262입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 7157e47d-a042-4462-96ed-23203a3213bd
feature: Admin Workspace, GraphQL, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-40262: GraphQL 쿼리가 관리자의 인기 검색어에 표시되지 않음

MDVA-40262 Adobe Commerce 품질 패치는 GraphQL 검색 쿼리가 관리자의 인기 검색어에 표시되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.3이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-40262입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.3

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL 쿼리는 관리자의 인기 검색어에 표시되지 않습니다.

<u>필수 구성 요소</u>:

샘플 데이터를 설치해야 합니다.

<u>재현 단계</u>:

1. **스토어** > **구성** > **카탈로그** > **SEO** > **인기 검색어**(으)로 이동한 다음 사용하도록 설정합니다.
1. 다음 GraphQL 쿼리를 실행합니다.

<pre>
<code class="language-graphql">
{
  products(
    search: "jackets"
    filter: { price: { to: "50" } }
    pageSize: 20
   ) {
    total_count
    items {
      name
      sku
    }
    page_info {
      page_size
      current_page
    }
  }
}
</code>
</pre>

<u>예상 결과</u>:

GraphQL 쿼리를 실행하여 제품을 검색한 후에는 검색 쿼리를 인기 검색어에 추가해야 합니다.

<u>실제 결과</u>:

검색 쿼리가 인기 검색어에 추가되지 않았습니다.

## 패치 적용

개별 패치를 적용하려면 배포 유형에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

Adobe Commerce용 품질 패치에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
