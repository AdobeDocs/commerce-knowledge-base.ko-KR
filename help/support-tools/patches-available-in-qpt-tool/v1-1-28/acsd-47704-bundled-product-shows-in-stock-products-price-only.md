---
title: 'ACSD-47704: 번들 제품은 재고 제품의 가격만 표시합니다.'
description: ACSD-47704 패치를 적용하여 번들 제품이 재고 제품의 가격만 표시되는 Adobe Commerce 문제를 해결합니다.
exl-id: 91fbeaf7-4bc2-49b1-a561-c3e63f193eaa
feature: Admin Workspace, Customer Service, Orders, Products
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 0%

---

# ACSD-47704: 번들 제품은 재고 제품의 가격만 표시합니다.

ACSD-47704 패치는 고객 그룹 간에 고객 세그먼트 가격이 잘못 캐시되는 문제를 수정합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28이 설치되었습니다. 패치 ID는 ACSD-47704입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.1-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

재고 품목만 포함되어 있으므로 동적 가격책정이 활성화된 번들 제품의 가격이 올바르지 않습니다.

<u>재현 단계</u>:

1. Commerce 관리 패널로 이동합니다.
1. 다음으로 이동 **[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]**.
1. 설정 **[UICONROL 동적 가격]** 끝 **[!UICONTROL Yes]**.
1. 번들 항목:
   * 설정 **[!UICONTROL Ship bundle items]** 끝 **[!UICONTROL Together]**
   * 선택 **[!UICONTROL Add Option]**
      * **[!UICONTROL Title]** = o1
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * 필수 확인란으로 표시
      * 재고가 있는 간단한 제품을 추가합니다(예: Joust Duffle Bag SKU 24-MB01). 제품을 추가하기 전에 가격을 적어 $34
   * 기본 수량: 1
   * 선택 **[!UICONTROL Add Option]**
      * **[!UICONTROL Option Title]** = o2
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * 필수 확인란으로 표시
      * 이전 단계에서 추가한 제품과 다른 재고에 있는 간단한 제품을 추가합니다. 예를 들어 - Firm Shoulder Pack 24-MB04를 참조하십시오. 제품을 추가하기 전에 가격을 적어 $32
      * 기본 수량: 1
1. 제품을 저장합니다.
1. 상점으로 이동하여 이전 단계에서 생성된 제품을 찾습니다. 가격을 66달러(66 = 32 + 34)로 낮추십시오.
현재 번들 제품의 가격은 옵션 가격의 합과 같습니다.
1. Commerce 관리 패널로 이동합니다. 다음으로 이동 **[!UICONTROL CATALOG]** > **[!UICONTROL Products]**.
1. 이전 번들 제품에 옵션으로 할당된 간단한 제품(SKU 24-MB01, 가격 34달러) 중 하나를 찾으십시오.
1. 수량을 0으로 변경합니다.
1. 제품을 저장합니다.
1. 상점으로 이동하여 이전 단계에서 만든 번들 제품을 찾으십시오. 가격을 32달러로 적어주세요. 이전에는 SKU 24MB01에서 $34, SKU 24MB04에서 $32를 합한 $66로 가격이 책정되었습니다. 24MB01 제품이 품절되었으므로 번들 가격은 $32로 표시됩니다. 인스톡 옵션인 다른 상품의 가격입니다.

<u>예상 결과</u>:

옵션이 재고에 있는지 또는 재고가 없는지에 상관없이 동적 가격책정이 활성화된 번들 제품의 가격은 일관되게 계산됩니다.

<u>실제 결과</u>:

동적 가격책정이 활성화된 번들 제품의 가격이 잘못 계산되었습니다. 재고가 있는 옵션만 고려하기 때문에 옵션 중 하나가 품절됐을 때 실제 옵션보다 표시되는 금액이 적다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
