---
title: "ACSD-55231: 빠른 주문 기능을 사용하는 동안 SKU를 찾을 수 없음 오류"
description: 빠른 주문 기능을 사용하여 장바구니에 제품을 추가하려고 할 때 *'카탈로그에서 SKU를 찾을 수 없음'* 오류가 발생하는 Adobe Commerce 문제를 해결하려면 ACSD-55231 패치를 적용합니다.
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: 463c2c07-39ec-4b03-81f7-ec2f71f5af76
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-55231: 빠른 주문 기능을 사용하는 동안 SKU를 찾을 수 없음 오류

ACSD-55231 패치는 빠른 주문 기능을 사용하여 장바구니에 제품을 추가하려고 할 때 *을(를) 받는 문제를 해결했습니다. 카탈로그에서 SKU를 찾을 수 없습니다* 오류. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-55231입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

빠른 주문 기능을 사용하여 장바구니에 추가할 제품을 검색할 때 카탈로그 &#39;*&#39; 오류에서*&#39;을(를) 가져오는 중 SKU를 찾을 수 없습니다.

<u>재현 단계</u>:

1. B2B 모듈과 함께 Adobe Commerce을 설치합니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]**(으)로 이동하여 다음을 설정합니다.
   * **[!UICONTROL Enable company]**: *예*
   * **[!UICONTROL Enable Shared Catalog]**: *예*
   * **[!UICONTROL Enable Quick Order]**: *예*
1. 위의 구성을 저장합니다.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]**(으)로 이동하여 새 공유 카탈로그를 만드십시오.
1. **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**(으)로 이동하여 새 고객을 만드십시오.
   * 그룹 필드에서 최근에 만든 공유 카탈로그를 선택하고 *[!UICONTROL Allow remote shopping assistance]*&#x200B;을(를) *예*(으)로 설정합니다.
1. SKU *p12*&#x200B;을(를) 사용하여 간단한 제품을 생성하고 범주 *c1*&#x200B;과 연결한 다음 [!UICONTROL Product in Shared Catalog] 섹션에서 새로 만든 공유 카탈로그를 선택하십시오.
1. 실행:

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. 관리 페이지를 새로 고칩니다.
1. **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**(으)로 이동하여 이전에 만든 고객을 편집합니다.
1. **[!UICONTROL Login as customer]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Quick order]**(으)로 이동합니다.
1. *p12* SKU를 검색하고 **[!UICONTROL Product Suggestion]**&#x200B;을(를) 클릭합니다.
1. 장바구니에 이 제품을 추가하고 주문합니다.
1. **[!UICONTROL Quick Order]**(으)로 돌아가서 SKU *p12*&#x200B;를 다시 검색하고 **[!UICONTROL Product Suggestion]**&#x200B;을(를) 클릭합니다.

<u>예상 결과</u>:

빠른 주문 기능을 사용하여 제품을 장바구니에 추가할 수 있습니다.

<u>실제 결과</u>:

빠른 주문 기능을 사용하여 제품을 장바구니에 추가할 수 없으며 *을(를) 가져올 수 없습니다. 제품 SKU를 검색할 때 카탈로그의* 오류를 찾을 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
