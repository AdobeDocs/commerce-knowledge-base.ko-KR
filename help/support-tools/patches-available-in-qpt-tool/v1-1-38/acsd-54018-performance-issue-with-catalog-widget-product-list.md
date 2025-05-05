---
title: 'ACSD-54018: 카탈로그 위젯 제품 목록의 성능 문제'
description: ACSD-54018 패치를 적용하여 조건 및 속성 유형 부울이 있는 카탈로그 위젯 제품 목록을 추가할 때 페이지가 느리게 로드되는 Adobe Commerce 문제를 해결합니다.
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 9f20484d-58c7-49d8-87df-1eeb84bee6fe
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-54018: 카탈로그 위젯 제품 목록의 성능 문제

ACSD-54018 패치는 조건 및 속성 유형 부울이 있는 카탈로그 위젯 제품 목록을 추가할 때 페이지가 느리게 로드되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54018입니다. 이 문제는 Adobe Commerce 2.4.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

조건 및 속성 유형 부울이 있는 카탈로그 위젯 제품 목록을 추가할 때 페이지가 느리게 로드됩니다.

<u>재현 단계</u>:

1. 100k 제품을 생성합니다.
1. 범위가 [!UICONTROL Store View] (으)로 설정된 bool 특성을 만듭니다.
1. 모든 속성 집합에 속성을 지정합니다.
   * 모든 제품에 특성 값 *예*&#x200B;를 할당하십시오.
1. 이제 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**(으)로 이동하여 10만개의 제품을 모두 선택하십시오.
   * **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**&#x200B;을(를) 선택합니다.
   * bool 특성을 *예*(으)로 설정하고 저장합니다.
   * 이 단계에서 로그아웃한 경우 *메모*&#x200B;를 확인하십시오.
1. CLI로 이동하여 `php bin/magento queue:con:start product_action_attribute.update`을(를) 실행합니다.
   * 모든 제품의 특성이 업데이트되었는지 확인하십시오.
1. 이제 **[!UICONTROL Content]** > **[!UICONTROL Pages]**(으)로 이동하여 새 페이지를 만드십시오.
1. **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**&#x200B;을(를) 엽니다.
1. *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*&#x200B;을(를) 선택합니다.
1. *[!UICONTROL Created attribute]* 조건을 *[!UICONTROL Yes]*(으)로 설정하고 저장합니다.
1. 프론트엔드로 이동하여 만든 페이지를 엽니다.
1. 전체 페이지 캐시를 비활성화하고 HTML 캐시를 차단합니다.
1. 페이지 로드 속도를 확인합니다.
1. 페이지를 몇 번 다시 로드하고 평균 로드 시간을 계산합니다.

<u>예상 결과</u>:

페이지가 빠르게 로드됩니다.

<u>실제 결과</u>:

페이지를 로드하는 데 5~10초 정도 소요됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
