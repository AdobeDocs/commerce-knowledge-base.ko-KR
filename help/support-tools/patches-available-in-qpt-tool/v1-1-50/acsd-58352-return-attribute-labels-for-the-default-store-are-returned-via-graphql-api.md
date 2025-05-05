---
title: 'ACSD-58352: 기본 저장소에 대한 반환 특성 레이블이  [!DNL GraphQL] API를 통해 반환됩니다.'
description: ACSD-58352 패치를 적용하여 요청 헤더에 기본이 아닌 저장소 보기가 지정된 경우 기본 저장소에 대한 반환 특성 레이블이  [!DNL GraphQL] API를 통해 반환되는 Adobe Commerce 문제를 해결합니다.
feature: GraphQL, Returns
role: Admin, Developer
source-git-commit: 6df1ec7e2cccfbadaa88b8233ca99faf40a208c5
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# ACSD-58352: [!DNL GraphQL] API를 통해 기본 저장소에 대한 반환 특성 레이블을 반환합니다.

ACSD-58352 패치는 요청 헤더에 기본이 아닌 저장소 보기가 지정된 경우 [!DNL GraphQL] API를 통해 기본 저장소에 대한 반환 특성 레이블이 반환되는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-58352입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL GraphQL] API를 통해 기본 저장소의 반환 특성 레이블이 반환됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Return Merchandising Authorization]** 사용
1. 기본 웹 사이트 아래에 *[!UICONTROL Additional Store]* 및 *[!UICONTROL Store View]*&#x200B;을(를) 만듭니다.
1. **[!UICONTROL Reason for Return]** 반환 특성을 편집하고 모든 스토어 보기에 대한 레이블을 추가합니다.
1. *[!UICONTROL Order]* 만들기
1. 해당 주문에 대해 *[!UICONTROL Return]*&#x200B;을(를) 만듭니다. *[!UICONTROL Return]*&#x200B;이(가) *[!UICONTROL Pending]* 상태인지 확인하십시오.
1. 헤더에 기본값이 아닌 지정된 [!UICONTROL Store View]을(를) 사용하여 고객 [!DNL GraphQL] 쿼리를 보냅니다.

   ```
   query {
       customer {
           returns {
               items {
                   items {
                       custom_attributes {
                           label
                           value
                       }
                   }
               }
           }
       }
   }
   ```

1. 응답을 확인합니다.

<u>예상 결과</u>

[!DNL GraphQL] 응답의 반환 레이블은 요청 헤더에 설정된 [!UICONTROL Store View]에 대한 것입니다.

<u>실제 결과</u>:

[!DNL GraphQL] 응답의 반환 레이블은 기본 [!UICONTROL Store View]에 대한 것입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
