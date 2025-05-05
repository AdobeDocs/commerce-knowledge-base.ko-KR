---
title: 'ACSD-56193: [!DNL Fastly] 캐시가 콘텐츠 준비 업데이트 시 지워지지 않음'
description: ACSD-56193 패치를 적용하여 콘텐츠 준비 업데이트를 위해  [!DNL Fastly] 캐시가 지워지지 않는 Adobe Commerce 문제를 해결합니다.
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: d4bbfafa-2d24-44cf-a08b-f7dd9111a65b
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-56193: [!DNL Fastly] 캐시가 콘텐츠 준비 업데이트를 위해 지워지지 않았습니다.

ACSD-56193 패치는 콘텐츠 준비 업데이트를 위해 [!DNL Fastly] 캐시가 지워지지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-56193입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

콘텐츠 준비 업데이트를 위해 [!DNL Fastly/Varnish] 캐시가 지워지지 않았습니다.

<u>재현 단계</u>:

1. [!DNL Varnish] 캐시를 설치하고 구성합니다.
1. 예약된 업데이트로 정적 블록을 만듭니다.
1. 정적 블록을 포함하는 범주를 만듭니다.
1. 아래 GraphQL 쿼리를 사용하여 범주의 콘텐츠를 가져옵니다.

   ```GraphQL
      query GetCategories($id: String!) {
         categoryList(filters: { category_uid: { eq: $id } }) 
       {
           meta_title
           meta_keywords
           meta_description
           description
           path
           cms_block {
             content
             identifier
             title
             __typename
           }
           __typename
       }
     }
     {"id":"Mwo="}
   ```

1. 이 쿼리를 여러 번 실행하고 응답이 [!DNL Varnish]에 캐시되었는지 확인하십시오.
1. cron 을 실행하여 예약된 변경 사항을 적용합니다.
1. 위의 GraphQL 쿼리를 다시 실행합니다.
1. 동일한 정적 블록에 대한 새 일정을 만듭니다.
1. 5-9번 단계를 반복합니다.

<u>예상 결과</u>:

예약된 업데이트가 실행되면 업데이트된 콘텐츠가 반환됩니다.

<u>실제 결과</u>:

예약된 업데이트가 실행되면 오래된 콘텐츠가 반환됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
