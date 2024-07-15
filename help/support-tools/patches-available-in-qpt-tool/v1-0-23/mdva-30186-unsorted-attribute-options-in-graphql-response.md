---
title: 'MDVA-30186: GraphQL 응답에서 정렬되지 않은 특성 옵션'
description: MDVA-30186 패치는 GraphQL 응답에서 속성 옵션이 정렬되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-30186입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.
exl-id: 7b2aef16-5012-4206-9444-e0b765f0c0c9
feature: Attributes, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-30186: GraphQL 응답에서 정렬되지 않은 특성 옵션

MDVA-30186 패치는 GraphQL 응답에서 속성 옵션이 정렬되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-30186입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라 2.3.4 및 2.4.2의 Adobe Commerce

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.4 - 2.3.5-p2, 2.4.0 - 2.4.0-p1 및 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. 기존 색상 속성에 세 가지 옵션을 추가합니다.
1. 옵션이 있는 6개의 간단한 제품을 만드십시오(예: *옵션 1*: 1개 제품, *옵션 2*: 2개 제품, *옵션 3*: 3개 제품).
1. 카테고리를 만들고 위에서 만든 모든 제품을 할당합니다.
1. 이제 범주 ID로 다음 GraphQL 요청을 만듭니다.

   <pre><code class="language-graphql">
    {
      products(
        filter: { category_id: { eq: "3" } }
        pageSize: 200
        currentPage: 1
        sort: { name: ASC }
      ) {
        aggregations {
          attribute_code
          count
          label
          options {
            count
            label
            value
          }
        }
        items {
          name
          sku
          url_key
        }
      }
    }
    </code></pre>

1. 이제 관리자의 속성 편집 페이지에서 속성 옵션의 정렬 순서를 변경합니다.
1. 위의 GraphQL 요청을 다시 만들고 색상 속성 옵션을 확인합니다.

<u>예상 결과</u>:

속성 옵션은 관리자에서 설정한 순서에 따라 정렬됩니다.

<u>실제 결과</u>:

속성 옵션은 항상 연관된 제품 수에 따라 정렬됩니다.


## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
