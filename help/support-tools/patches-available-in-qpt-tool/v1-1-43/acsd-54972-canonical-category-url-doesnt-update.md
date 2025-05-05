---
title: 'ACSD-54972: 표준 범주 URL이 업데이트되지 않음'
description: ACSD-54972 패치를 적용하여 카테고리 URL을 변경한 후 표준 카테고리 URL이 업데이트되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Catalog Management, Products, Categories
role: Admin, Developer
exl-id: 2d78f5f6-d485-45a4-a40d-9a0ddd124f82
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-54972: 범주 URL을 변경한 후 표준 범주 URL이 업데이트되지 않음

ACSD-54972 패치는 범주 URL을 변경한 후 표준 범주 URL이 업데이트되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54972입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

표준 범주 URL은 범주 URL을 변경한 후에는 업데이트되지 않습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**(으)로 이동합니다.

   * *[!UICONTROL Use Canonical Link Meta Tag for Categories]* 설정: *예*

2. 범주(예: *이름*: *범주 01*, *URL 키*: *범주-01*)를 만듭니다.
3. **[!UICONTROL Create Permanent Redirect for old URL]** 확인란이 선택된 상태로 *URL 키*&#x200B;을(를) 원래 값과 다르게 업데이트합니다.
4. 캐시를 정리합니다.
5. 앞쪽 끝의 *[!UICONTROL Category Page]*(으)로 이동합니다.
6. 페이지 소스를 확인하고 *표준* 태그를 검색합니다.

<u>예상 결과</u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01-new.html" />`

<u>실제 결과</u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01.html" />`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
