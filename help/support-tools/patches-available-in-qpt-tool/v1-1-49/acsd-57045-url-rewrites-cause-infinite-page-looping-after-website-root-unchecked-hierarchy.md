---
title: 'ACSD-57045: [!UICONTROL Hierarchy]에서 [!UICONTROL Website Root]을(를) 선택 취소한 후 URL 재작성으로 인해 무한 페이지 루프가 발생합니다.'
description: ACSD-57045 패치를 적용하여 [!UICONTROL Hierarchy]에서 [!UICONTROL Website Root]을(를) 선택 취소한 후 URL 재작성으로 인해 무한 페이지 루프가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: CMS
role: Admin, Developer
source-git-commit: a39e5c857aae398a0b0ba44308ea417525a410d3
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---


# ACSD-57045: [!UICONTROL Hierarchy]에서 [!UICONTROL Website Root]을(를) 선택 취소한 후 URL 재작성으로 인해 무한 페이지 루프가 발생합니다.

ACSD-57045 패치는 **[!UICONTROL Hierarchy]**&#x200B;에서 **[!UICONTROL Website Root]**&#x200B;을(를) 선택 취소한 후 URL 다시 쓰기로 인해 무한 페이지 루프가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-57045입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Hierarchy]**&#x200B;에서 **[!UICONTROL Website Root]**&#x200B;을(를) 선택 취소한 후 URL 재작성으로 인해 무한 페이지 루프가 발생합니다.

<u>재현 단계</u>:

1. 이름이 *Test-Parent*&#x200B;인 CMS 페이지를 만듭니다.
1. *Test-Child* 페이지를 만들고 **[!UICONTROL Hierarchy]** 섹션에서 **[!UICONTROL Website Root]** > **[!UICONTROL Parent]**&#x200B;을(를) 선택한 다음 저장합니다.
1. **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**(으)로 이동합니다.
1. 다음 두 가지 새로운 재작성 기능이 있습니다.
   * *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*&#x200B;을(를) 가리키는 *Test-Parent*&#x200B;에 대한 요청 경로
   * *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*&#x200B;을(를) 가리키는 *Test-Child*&#x200B;에 대한 요청 경로
1. 상점 앞으로 이동하여 URL에 *test-child*&#x200B;을(를) 추가하십시오. 하위 페이지가 표시됩니다.
1. 동일한 작업을 수행하지만 URL에 *test-parent/test-child/*&#x200B;을(를) 추가하여 동일한 페이지를 봅니다.
1. **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**(으)로 이동한 다음 **[!UICONTROL Add URL Rewrite]**&#x200B;을(를) 선택합니다. 다음 설정을 선택합니다.
   * 유형: *사용자 지정*
   * 요청 경로: *test-parent/test-child*
   * 대상 경로: *test-child*
   * 리디렉션 유형: *영구(301)*
1. *test-parent/test-child* 경로를 방문하면 *test-child*(으)로 리디렉션되어야 합니다.
1. 하위 페이지를 편집합니다(**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** > 하위 항목 선택 후 **[!UICONTROL Edit]**).
1. **[!UICONTROL Hierarchy]** 섹션에서 *Test-Parent*&#x200B;을(를) 선택한 상태로 유지하되 **[!UICONTROL Website Root]**&#x200B;을(를) 선택 취소하고 저장합니다.
1. **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**(으)로 이동하여 *cms/page/view/page_id*&#x200B;에 대한 원래 *test-child*&#x200B;이(가) 누락되었고, 이 시점에서 *test-child*&#x200B;에서 *test-parent/test-child*&#x200B;을(를) 가리키는 경로로 대체됩니다.
1. 상점을 방문하여 *Test-Child* 페이지를 방문하세요.

<u>예상 결과</u>:

*Test-Child* 페이지가 열려 있습니다.

<u>실제 결과</u>:

*Test-Child* 페이지가 열리지 않았습니다. 브라우저가 *test-parent/test-child* 페이지를 무한 루프로 열려고 합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
