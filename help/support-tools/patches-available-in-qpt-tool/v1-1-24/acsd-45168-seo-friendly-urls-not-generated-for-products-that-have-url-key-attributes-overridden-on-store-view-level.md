---
title: 'ACSD-45168: url_key 특성이 재정의된 제품에 대해 SEO 친화적 URL이 생성되지 않음'
description: ACSD-45168 패치를 적용하여 스토어-보기 수준에서 url_key 특성이 재정의된 제품에 대해 SEO 친화적 URL이 생성되지 않는 Adobe Commerce 문제를 수정합니다.
exl-id: cdba42ac-3c96-439b-befa-f0a13587b5d9
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-45168: url_key 특성이 재정의된 제품에 대해 SEO에 친숙한 URL이 생성되지 않음

ACSD-45168 패치는 스토어-보기 수준에서 url_key 특성이 재정의된 제품에 대해 SEO에 친숙한 URL이 생성되지 않는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-45168입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

스토어-뷰 수준에서 url_key 특성이 재정의된 제품에 대해서는 SEO에 친숙한 URL이 생성되지 않습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**(으)로 이동하여 구성을 다음과 같이 설정합니다.
   * [!UICONTROL Use Categories Path for Product URLs] = *예*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *예*
1. 구성 캐시를 정리합니다.
1. [!UICONTROL Category 1]과(와) [!UICONTROL Category 2] 두 개의 범주를 만듭니다.
1. [!UICONTROL Category 1]에 [!UICONTROL Product 1], [!UICONTROL Category 1]에 [!UICONTROL Product 2]의 두 제품을 만듭니다.
1. [!UICONTROL Product 1]의 범위를 [!UICONTROL Default Store View](으)로 변경합니다.
1. [!UICONTROL Search Engine Optimization]에서 선택적 URL [!UICONTROL Key]을(를) 선택 취소합니다.
1. 제품을 저장합니다.
1. [!UICONTROL All Store Views](으)로 다시 전환합니다.
1. [!UICONTROL Category 2]에 [!UICONTROL Product 1]을(를) 추가하고 [!UICONTROL Category 2]에 [!UICONTROL Product 2]을(를) 추가합니다.
1. [!UICONTROL url_rewrite] 테이블 또는 [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites]을(를) 확인합니다.

<u>예상 결과</u>:

[!UICONTROL Product 1]에 대해 [!UICONTROL Category 2]에 대한 SEO에 친숙한 URL이 만들어졌습니다.

<u>실제 결과</u>:

저장소 보기 범위에 대해 URL 키 특성을 덮어썼기 때문에 [!UICONTROL Product 1]에 대해 [!UICONTROL Category 2]에 대한 SEO에 친숙한 URL이 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
