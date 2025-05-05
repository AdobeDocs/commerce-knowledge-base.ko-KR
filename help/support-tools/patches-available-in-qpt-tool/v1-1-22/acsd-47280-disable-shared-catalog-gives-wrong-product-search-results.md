---
title: '[!DNL ACSD-47280]: 공유 카탈로그를 사용하지 않도록 설정하면 잘못된 제품 검색 결과가 나옵니다'
description: 공유 카탈로그 기능을 사용하지 않도록 설정한 경우 올바른 검색 결과를 표시하려면  [!DNL ACSD-47280] 패치를 적용하십시오.
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: 공유 카탈로그를 사용하지 않도록 설정하면 잘못된 제품 검색 결과가 나옵니다

[!DNL shared catalog] 기능을 사용하지 않도록 설정하면 [!DNL ACSD-47280] 패치가 올바른 검색 결과를 표시합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22가 설치되어 있을 때 사용할 수 있습니다. [!DNL patch ID]은(는) [!DNL ACSD-47280]입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). [!DNL patch ID]을(를) 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL shared catalog]을(를) 사용하지 않도록 설정하면 잘못된 제품 검색 결과가 표시됩니다.

<u>필수 구성 요소</u>:

* [!DNL B2B]개 모듈이 설치됨

<u>재현 단계</u>:

1. 두 번째 웹 사이트를 만듭니다.
1. 두 번째 웹 사이트에 제품을 할당합니다.
1. [!DNL GraphQL]을(를) 사용하여 **초 웹 사이트**&#x200B;에서 제품 확인:

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
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
   ```

1. 기본 [!DNL scope]에서 **[!UICONTROL Shared Catalog]**&#x200B;을(를) 사용하도록 설정합니다.
1. [!DNL GraphQL] 요청에 더 이상 두 번째 웹 사이트에 대한 제품이 표시되지 않습니다. 이는 올바른 결과입니다.
1. 두 번째 웹 사이트의 [!DNL scope] (으)로 이동하여 **[!UICONTROL Company]**&#x200B;을(를) 비활성화합니다.

<u>예상 결과</u>:

[!DNL GraphQL] 요청에도 두 번째 웹 사이트에 대한 제품이 표시됩니다.

<u>실제 결과</u>:

[!DNL GraphQL] 요청에 두 번째 웹 사이트에 대한 제품이 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
