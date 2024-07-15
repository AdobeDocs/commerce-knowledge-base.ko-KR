---
title: 'ACSD-48366: [!UICONTROL Back to Stock] 전자 메일 템플릿에 제품 이미지가 표시되지 않음'
description: ACSD-48366 패치를 적용하여 제품 썸네일 이미지가 제품의 재고 경고 이메일에 표시되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 57b549b0-6e97-4d5f-927e-9585f3257872
feature: Admin Workspace, Communications, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48366: [!UICONTROL Back to Stock] 전자 메일 템플릿에 제품 이미지가 표시되지 않음

ACSD-48366 패치는 제품 썸네일 이미지가 제품의 재고 경고 이메일에 표시되지 않는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48366입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 이미지가 [!UICONTROL Back to Stock] 전자 메일 템플릿에 표시되지 않습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]*(으)로 이동하여 *[!UICONTROL Back in Stock]*&#x200B;에 대해 *[!UICONTROL Product Alert]*&#x200B;을(를) 사용하도록 설정하십시오.
1. **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]*(으)로 이동하여 *[!UICONTROL Display Out of Stock Products]*&#x200B;을(를) 사용하도록 설정합니다.
1. 수량 = 0인 간단한 제품을 만듭니다.
1. 상점 첫 화면에서 고객을 만들고 위의 제품을 구독하면 재고가 있을 때 제품 알림을 받을 수 있습니다.
1. 제품을 재고로 만드세요.
1. 제품 경고 cron 을 실행합니다.

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. 고객에 대한 제품 경고를 시작합니다.

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. 이메일을 확인합니다. 이제 메일 캐쳐에서 스톡 경고 이메일을 사용할 수 있습니다.

<u>예상 결과</u>:

스톡 경고 이메일에 제품 이미지가 표시됩니다.

<u>실제 결과</u>:

스톡 경고 이메일에는 제품 이미지를 사용할 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
