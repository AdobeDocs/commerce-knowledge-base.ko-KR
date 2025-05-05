---
title: '''ACSD-51739: ''CompanyTeam'' GraphQL 요청에서 ''structure_id'' 요청 오류'''
description: ACSD-51739 패치를 적용하여 'CompanyTeam' GraphQL 요청에서 'structure_id'가 요청되면 오류가 반환되는 Adobe Commerce 문제를 수정합니다.
exl-id: 31c085e0-c8be-4709-9620-80ff360dca9a
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739: `CompanyTeam` GraphQL 요청에서 `structure_id`을(를) 요청하는 동안 오류가 발생했습니다.

ACSD-51739 패치는 `CompanyTeam` GraphQL 요청에서 `structure_id`을(를) 요청할 때 오류가 반환되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51739입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`CompanyTeam` GraphQL 요청에서 `structure_id`을(를) 요청하면 오류가 반환됩니다.

<u>재현 단계</u>

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**(으)로 이동한 다음 *[!UICONTROL Enable Company]*&#x200B;을(를) *예*(으)로 설정합니다.
1. 회사 관리자 사용자와 함께 회사를 만듭니다.
1. 새 고객(*customer1*)을 만들고 위에서 만든 회사를 이 고객에게 할당합니다.
1. 프론트엔드에서 회사 관리자로 로그인합니다.
1. 회사 팀을 만들고 끌어다 놓기를 사용하여 *customer1*&#x200B;을(를) 팀에 할당합니다.
1. `structure_id`과(와) 함께 `CompanyTeam`을(를) 포함하는 다음 회사 GraphQl 쿼리를 실행합니다.

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. GraphQL 응답을 확인합니다.

<u>예상 결과</u>:

오류가 반환되지 않고 요청된 모든 데이터가 GraphQL 응답에 있습니다.

<u>실제 결과</u>:

* 응답에 *내부 서버 오류*&#x200B;가 있습니다.
* `var/log/exception.log`에 포함된 항목:

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
