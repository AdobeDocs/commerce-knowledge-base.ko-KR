---
title: "ACSD-55100: [!DNL GraphQL] 검색 결과에 10k 이상의 제품을 반환하지 않음"
description: ACSD-55100 패치를 적용하여 GraphQL이 검색 결과에서 *10k* 이상의 제품을 반환하지 않는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 951e5cd4-9690-43df-9e51-deab73f9eb54
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-55100: [!DNL GraphQL]이(가) 검색 결과에 10k 이상의 제품을 반환하지 않습니다.

ACSD-55100 패치는 [!DNL GraphQL]이(가) 검색 결과에서 *10k* 이상의 제품을 반환하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-55100입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL GraphQL]은(는) 검색 결과에서 *10k* 이상의 제품을 반환하지 않습니다.

<u>필수 구성 요소</u>:

**[!DNL OpenSearch]**&#x200B;의 경우 사용 가능한 최신 버전을 사용 중인지 확인하십시오.

보고된 문제를 해결하기 위해 시점 기능이 도입되었습니다. 시점 기능은 **[!DNL OpenSearch]** 2.5.0 이후에 사용할 수 있으며 `opensearch-project/opensearch-php` 패키지의 버전 2.2가 필요합니다.

그러나 버전 2.0.1 미만이어야 하는 `opensearch-project/opensearch-php` 패키지에 대한 종속성을 지정하는 `magento/magento-cloud-metapackage`과(와) 충돌이 있습니다.


이 종속성을 사용하면 [opensearch-project/opensearch-php] 패키지를 최신 버전 2.2로 업데이트할 수 없습니다.

그 결과 다음 오류가 발생하고 *10,000*&#x200B;을(를) 초과하는 제품에 대해 null 결과를 반환합니다.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

기존 종속성을 사용하면 `composer.json` 파일에 버전을 직접 추가하고 `opensearch-project/opensearch-php` 패키지를 버전 2.2로 업데이트하기가 어렵습니다.

이 문제를 해결하려면 필수 블록의 기본 `composer.json` 파일에 다음 줄을 포함하십시오. 그런 다음 다시 배포하여 문제가 있는 패키지를 최신 버전으로 업데이트합니다.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>재현 단계</u>:

1. *15k* 제품으로 카탈로그를 생성합니다.
1. [!DNL GraphQL] 보내기:

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>예상 결과</u>:

Total_count = *15k*
모든 제품을 표시할 수 있어야 합니다.

<u>실제 결과</u>:

Total_count = *10k*
*10k* 일괄 처리 후에는 표시할 제품을 더 이상 가져올 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
