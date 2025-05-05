---
title: 'ACSD-52801: GraphQL 제품 필터 쿼리가 부분 일치 결과를 표시하지 않음'
description: ACSD-52801 패치를 적용하여 GraphQL 제품 필터 쿼리가 부분적으로 일치하는 결과를 표시하지 않는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin, Developer
exl-id: a03a4d09-ebec-4ad0-a875-48e000a29b44
source-git-commit: 40968db03939058884bca4e4aeed2ffef0462e0b
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# ACSD-52801: GraphQL 제품 필터 쿼리가 부분 일치 결과를 표시하지 않음

ACSD-52801 패치는 GraphQL 제품 필터 쿼리가 부분 일치 결과를 표시하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-52801입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2, 2.4.5-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL 제품 필터 쿼리에 부분 일치 결과가 표시되지 않습니다.

<u>재현 단계</u>:

1. 샘플 데이터를 사용하여 클린 인스턴스를 설치합니다.
1. 다음 GraphQL 쿼리를 실행합니다.

```GraphQL
{
  products(
    filter: { name: { match: "Life" } }
    sort: { position: ASC }
    pageSize: 100
    currentPage: 1
  ) {
    total_count
    items {
      url_key
      sku
      name
      meta_title
    }
  }
}
```

<u>예상 결과</u>:

필요한 결과를 제어하기 위해 `match_type`([!UICONTROL PARTIAL], [!UICONTROL FULL]) 특성을 추가하여 storefront 고급 검색에서와 유사한 일치 결과를 허용합니다. [!UICONTROL FULL]은(는) 완전한 단어와 일치하고, [!UICONTROL PARTIAL]은(는) 평생에 포함된 삶과 같은 부분적인 단어와 일치합니다.

<u>실제 결과</u>:

제품 필터 쿼리는 검색 키워드에 대한 부분 일치 결과를 반환하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
