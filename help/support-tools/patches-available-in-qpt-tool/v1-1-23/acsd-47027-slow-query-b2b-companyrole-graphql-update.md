---
title: 'ACSD-47027: 느린 쿼리 B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 업데이트'
description: ACSD-47027 패치를 적용하여 느린 쿼리 B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 업데이트가 있는 Adobe Commerce 문제를 해결합니다.
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027: 느린 쿼리 B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 업데이트

ACSD-47027 패치는 느린 쿼리 B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 업데이트가 예상대로 작동하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-47027입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

느린 쿼리 B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 업데이트가 예상대로 작동하지 않습니다.

<u>필수 구성 요소</u>:

B2B 모듈을 설치합니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리에서 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]**(으)로 이동하여 **[!UICONTROL Enable Company]**&#x200B;을(를) _예_(으)로 설정합니다.
1. 프론트엔드로 이동하여 회사를 만듭니다.
1. 회사 사용자로 로그인한 후 **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]**(으)로 이동하여 새 역할을 추가합니다.
1. `bin/magento dev:que:enab`을(를) 사용하여 [!UICONTROL dev] 쿼리 로그를 사용하도록 설정합니다.
1. 이제 아래 [!DNL GraphQL] 요청을 보냅니다(ID는 [!UICONTROL base64] 인코딩된 역할 ID).

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. 쿼리 로그를 확인합니다.
1. 위의 쿼리가 실행되었음을 알 수 있습니다. 이 쿼리는 `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`에서 실행됩니다.

<u>예상 결과</u>:

**[!UICONTROL company_permissions]** DB 테이블에서 사용 가능한 모든 데이터를 로드하지 않도록 `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`을(를) 최적화해야 합니다.

<u>실제 결과</u>:

Adobe Commerce은 필터 없이 쿼리를 실행합니다. 기록이 많을 때는 Adobe Commerce이 데이터 수집을 준비하는 데 많은 시간이 걸린다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html). 

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
