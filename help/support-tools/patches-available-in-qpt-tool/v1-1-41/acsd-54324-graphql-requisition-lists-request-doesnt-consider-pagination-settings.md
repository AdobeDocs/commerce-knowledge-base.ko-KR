---
title: 'ACSD-54324: GraphQL requisition_lists 요청은 페이지 매김 설정을 고려하지 않습니다.'
description: ACSD-54324 패치를 적용하여 GraphQL 'requisition_lists' 요청이 페이지 매김 설정을 고려하지 않고 모든 결과를 반환하는 Adobe Commerce 문제를 해결합니다.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 85297eae-bedf-4624-9758-0b68452d131b
source-git-commit: b5894687704594a4e751c230246bdf167b1b6402
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-54324: GraphQL `requisition_lists` 요청에서 페이지 매김 설정을 고려하지 않습니다.

ACSD-54324 패치는 GraphQL `requisition_lists` 요청이 페이지 매김 설정을 고려하지 않고 모든 결과를 반환하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.41이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54324입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL `requisition_lists` 요청은 페이지 매김 설정을 고려하지 않고 모든 결과를 반환합니다.

<u>재현 단계</u>:

1. 관리자에 로그인하고 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**(으)로 이동합니다.

   * *[!UICONTROL Enable Requisition List]*&#x200B;을(를) *예*(으)로 설정합니다.

1. 프론트엔드에 로그인하고 상단 메뉴 또는 **[!UICONTROL My Account]**&#x200B;에서 **[!UICONTROL My Requisition Lists]**(으)로 이동하여 여러 개의 구매요청을 만듭니다(예: 7).
1. 고객 토큰을 생성한 후 고객에 대해 아래 GraphQL `requisition_lists` 쿼리를 실행합니다.

   * 페이지 크기가 사용자가 생성한 총 구매요청 목록 수보다 작은지 확인합니다(예: 4).

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. `total_count` 필드의 값이 4이면 7을 표시해야 합니다.

   *페이지 크기*&#x200B;와(과) 같아야 하는 경우 항목 수에는 7개가 표시됩니다.

<u>예상 결과</u>:

* *페이지 크기*(으)로 나열된 숫자는 총 레코드 수가 아니라 `total_count` 아래에 반환됩니다.
* 항목 수가 *페이지 크기*&#x200B;와(과) 같습니다.

<u>실제 결과</u>:

*페이지 크기*&#x200B;이(가) 언급되더라도 `total_count` 아래에 반환되는 총 레코드 수입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
