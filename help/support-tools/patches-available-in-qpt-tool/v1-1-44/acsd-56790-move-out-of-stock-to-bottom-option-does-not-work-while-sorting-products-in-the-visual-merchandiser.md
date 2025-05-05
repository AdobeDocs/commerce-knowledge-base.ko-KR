---
title: 'ACSD-56790: **[!UICONTROL move out of stock to bottom]** 옵션이  [!DNL Visual Merchandiser]에서 제품을 정렬하는 동안 작동하지 않습니다.'
description: ACSD-56790 패치를 적용하여 Visual Merchandiser에서 제품을 정렬하는 동안 재고 부족 상태에서 하단으로 이동 옵션이 작동하지 않는 Adobe Commerce 문제를 해결합니다.
feature: Products, Categories
role: Admin, Developer
exl-id: a0c61696-a12d-4c1a-a061-e2f17f38e1f4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# [!DNL Visual Merchandiser]에서 제품을 정렬하는 동안 ACSD-56790: **[!UICONTROL move out of stock to bottom]** 옵션이 작동하지 않습니다.

ACSD-56790 패치는 [!DNL Visual Merchandiser]에서 제품을 정렬하는 동안 재고 부족 상태에서 하단으로 이동 옵션이 작동하지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-56790입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL Visual Merchandiser]에서 제품을 정렬하는 동안 **[!UICONTROL move out of stock to bottom]** 옵션이 작동하지 않습니다.

<u>재현 단계</u>:

1. Adobe Commerce을 설치합니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**(으)로 이동하여 다음 특성을 만듭니다.
1. 새 웹 사이트를 만듭니다. **기본 웹 사이트가 아님**.
1. 이 새 웹 사이트에 **기본 스토어가 아닌**&#x200B;을(를) 만듭니다.
1. 두 개의 스토어를 만듭니다.

   * **기본 웹 사이트 스토어**&#x200B;의 첫 번째
   * **기본 스토어가 아닌**&#x200B;에서 두 번째 항목입니다.

1. 두 개의 소스를 만듭니다.
   * 편지.
   * 숫자.

1. 두 개의 주식을 만듭니다.
   * 첫 번째 주요 - 판매 채널: 주요 웹 사이트 - 지정된 소스: 편지.
   * 두 번째 비주 - 판매 채널: 비주 - 지정된 출처: 숫자.

1. 두 웹 사이트에서 모두 기본값 카테고리의 세 가지 간단한 제품을 만들고 모두 두 소스에 할당합니다.

   * ProductA - 수량 *10*(문자), 수량 *0*(숫자)
   * Product1 - 수량 *0*(문자), 수량 *10*(숫자).
   * ProductA1 - 수량 *10*(문자), 수량 *10*(숫자).

1. **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**(으)로 이동한 다음 **[!UICONTROL Default category]**&#x200B;을(를) 선택합니다.
1. 범위를 **처음**(으)로 변경합니다.
1. 카테고리 섹션의 제품을 확장합니다.
1. **[!UICONTROL move out of stock to bottom]**(으)로 정렬 순서 선택

<u>예상 결과</u>:

**품절** 제품이 있는 제품 목록이 맨 아래로 이동됩니다.

<u>실제 결과</u>:

제품 로드에 실패했습니다. 다음 오류 메시지가 표시된 페이지가 관리 대시보드로 리디렉션됩니다. `Invalid security or form key. Please refresh the page`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
