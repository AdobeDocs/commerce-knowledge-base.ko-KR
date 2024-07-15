---
title: 'ACSD-50887: *[!UICONTROL Use in Search]* 옵션 없이 *[!UICONTROL Use in Search Results Layered Navigation]*이(가) 예로 설정됨'
description: ACSD-50887 패치를 적용하여 제품 속성 *[!UICONTROL Use in Search Results Layered Navigation]*을(를) *예*로 설정할 수 있고 *[!UICONTROL Use in Search]* 옵션도 *예*로 설정되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: b597709b-7489-41a0-b1ff-d68d0def0b46
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;이(가) *[!UICONTROL Use in Search]* 옵션 없이 *예*(으)로 설정됨

ACSD-50887 패치는 *[!UICONTROL Use in Search]* 옵션도 *예*(으)로 설정되지 않고 제품 특성 속성 *[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;을(를) *예*(으)로 설정할 수 있는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.36이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-50887입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*[!UICONTROL Use in Search]* 옵션도 *예*(으)로 설정하지 않고 제품 특성 속성 *[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;을(를) *예*(으)로 설정할 수 있습니다.

이러한 설정은 함께 사용하도록 설계되었습니다. 패치가 적용된 상태에서 *[!UICONTROL Use in Search]* 옵션이 *No*(으)로 설정되어 있으면 *No*(으)로 설정된 것처럼 *[!UICONTROL Use in Search Results Layered Navigation]* 옵션이 작동하지 않습니다.

<u>재현 단계</u>:

1. 관리자에서 **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]**(으)로 이동하여 다중 선택 유형의 특성을 만들고 다음을 설정합니다.

   * *[!UICONTROL Use in Search]= 아니요*
   * *[!UICONTROL Use in Layered Navigation]= (모든 옵션)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= 예*
   * *이름 = Test_attribute*
   * *옵션*:
      * *스티커*
      * *선택기*

1. 기본 속성 집합에 새 속성을 추가합니다.
1. 다음 두 가지 제품을 만듭니다.

   1. 첫 번째 제품:
      * 이름 = 스티커
      * 가격, 수량, 중량을 1로 설정
      * Test_attribute = 옵션 *스티커* 선택

   1. 두 번째 제품:
      * 이름 = 선택기
      * 가격, 수량, 중량을 1로 설정
      * Test_attribute = 두 옵션 모두 선택

1. `catalogsearch_fulltext` 다시 인덱싱 실행:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. 상점 전면에서 *스티커*&#x200B;라는 단어를 검색합니다.

<u>예상 결과</u>:

*[!UICONTROL Use in Search]*&#x200B;이(가) *아니요*(으)로 설정되어 있으면 [!DNL Elasticsearch]에서 Test_attribute를 인덱싱하지 않으므로 *스티커* 제품만 반환됩니다.

<u>실제 결과</u>:

두 제품 모두 반품됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
