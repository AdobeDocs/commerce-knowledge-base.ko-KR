---
title: 'ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_ PHP 7.4의 알려진 제품에 대한 존재하지 않는 특정 범주 경로에 액세스할 때 오류가 발생합니다.'
description: PHP 7.4에서 알려진 제품에 대해 존재하지 않는 특정 카테고리 경로에 액세스할 때 _[!UICONTROL Trying to access array offset on value of type bool]_ 오류가 있는 Adobe Commerce 문제를 해결하려면 ACSD-47444 패치를 적용합니다.
exl-id: dfe803d0-bcff-40e6-a759-8c2243235ea8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-47444: PHP 7.4에서 알려진 제품에 대해 존재하지 않는 특정 범주 경로에 액세스할 때 _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;오류가 발생합니다.

ACSD-47444 패치는 PHP 7.4에서 알려진 제품에 대해 존재하지 않는 특정 범주 경로에 액세스할 때 _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;오류가 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22가 설치되어 있을 때 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**
* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

PHP 7.4에서 알려진 제품에 대해 존재하지 않는 특정 범주 경로에 액세스할 때 다음 오류가 발생합니다. _[!UICONTROL Trying to access array offset on value of type bool]_.

<u>필수 구성 요소</u>:

PHP 7.4.

<u>재현 단계</u>:

1. 이름이 &quot;test&quot;인 새 제품을 만듭니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > 집합 **[!UICONTROL Generate "category/product" URL Rewrites]** = _아니요_(으)로 이동합니다.
1. 상점 첫 화면으로 이동하여 ../abc/test.html (&quot;abc&quot; - 없어야 함)와 같은 URL을 방문하십시오.

<u>예상 결과</u>:

404페이지요

<u>실제 결과</u>:

500 오류:

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
