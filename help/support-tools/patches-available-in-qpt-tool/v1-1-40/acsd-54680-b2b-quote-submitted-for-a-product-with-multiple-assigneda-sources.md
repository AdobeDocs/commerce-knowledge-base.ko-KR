---
title: 'ACSD-54680: 여러 개의 할당된 소스가 있는 제품에 대한 B2B 견적을 처리할 수 없음'
description: ACSD-54680 패치를 적용하여 여러 개의 할당된 소스가 있는 제품에 대한 B2B 견적을 처리할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: B2B
role: Admin, Developer
exl-id: 4d05714c-d32d-46f3-b857-81704c9e96cd
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-54680: 여러 개의 할당된 소스가 있는 제품에 대한 B2B 견적을 처리할 수 없습니다.

ACSD-54680 패치는 여러 개의 할당된 소스가 있는 제품에 대한 B2B 견적을 처리할 수 없는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.40이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54680입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

여러 개의 할당된 소스가 있는 제품에 대한 B2B 견적을 처리할 수 없습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]**(으)로 이동하여 **Source 1** 및 **Source 2** 두 개의 새 소스를 만듭니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]**(으)로 이동하여 새 Stock: **Stock A**&#x200B;을(를) 만들고, 기본 웹 사이트에 할당하고, **Source 1** 및 **Source 2**&#x200B;을(를) 할당합니다.
1. 간단한 제품을 만들고 **Source 1** 및 **Source 2**&#x200B;을(를) 할당하고 각 소스에 대해 수량 = *2*&#x200B;을(를) 설정합니다. (따라서 제품의 판매 가능 수량은 *4*&#x200B;이어야 합니다.)
1. 회사 계정을 만듭니다.
1. **[!UICONTROL Storefront]**(으)로 이동하여 회사 계정에 로그인합니다.
1. 수량 = *4*&#x200B;인 간단한 제품을 장바구니에 추가합니다.
1. *[!UICONTROL Shopping cart]*&#x200B;을(를) 열고 **[!UICONTROL Request a quote]** 단추를 클릭합니다.
1. 댓글과 따옴표 이름을 추가하고 **[!UICONTROL Send a Request]** 단추를 클릭합니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**(으)로 이동합니다.
1. 최근에 제출된 견적을 엽니다.

<u>예상 결과</u>:

견적된 품목에는 주문한 제품이 포함되어 있습니다.

<u>실제 결과</u>:

견적이 지정된 항목 페이지 섹션이 비어 있어 견적을 처리할 수 없습니다.
`var/log/system.log` 포함 항목

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
