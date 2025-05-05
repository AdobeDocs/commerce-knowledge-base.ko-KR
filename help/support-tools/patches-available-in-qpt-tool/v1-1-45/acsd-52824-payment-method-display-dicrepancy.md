---
title: 'ACSD-52824: 회사 고객에 대해 비활성화된 결제 방법 표시'
description: ACSD-52824 패치를 적용하여 회사 설정에서 비활성화되어 있지만 회사 고객에 대해  [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] 결제 방법이 표시되는 Adobe Commerce 문제를 해결합니다.
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 03496fb1-d492-4f02-9cdc-466cb571a2eb
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52824: 회사 고객에 대해 비활성화된 결제 방법 표시

ACSD-52824 패치는 회사 설정에서 [!DNL PayPal Express], [!DNL Google Pay] 및 [!DNL Apple Pay] 결제 방법이 비활성화되어 있지만 회사 고객에 대해 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-52824입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

회사 고객에 대해 비활성화된 결제 방법이 표시됩니다.

<u>재현 단계</u>:

1. [!DNL PayPal Express Checkout]을(를) 구성하고 사용하도록 설정합니다. **[!UICONTROL Basic Settings]**(으)로 이동하고 **[!DNL PayPal Express Checkout]**&#x200B;을(를) 선택한 다음 **[!UICONTROL Display on Shopping Cart]**&#x200B;에 대한 옵션을 *예*(으)로 설정합니다.
1. [!DNL Braintree]을(를) 구성하고 [!DNL Braintree]까지 [!DNL Apple Pay] 및 [!DNL Google Pay]을(를) 사용하도록 설정합니다.
1. **[!UICONTROL Customers]** > **[!UICONTROL Companies]**(으)로 이동하여 새 회사를 만드십시오.
1. **[!UICONTROL Advanced Settings]**&#x200B;을(를) 클릭하고 **[!UICONTROL Applicable Payment Methods]**&#x200B;을(를) 찾은 다음 **[!UICONTROL Selected Payment Methods]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Selected Payment Methods]**&#x200B;에서 사용 가능하고 *[!DNL PayPal Express Checkout]*, *[!DNL Apple Pay]* 또는 *[!DNL Google Pay]*&#x200B;과(와) 연결되어 있지 않은 결제 방법을 선택하십시오. 예를 들어 **[!UICONTROL Check/Money Order]**&#x200B;을(를) 선택합니다.
1. 적절한 결제 방법을 선택한 후 신규 고객을 생성하고 이전에 생성한 회사와 연결합니다.
1. 회사와 연결된 고객 계정으로 로그인하고 계속 진행하여 장바구니에 항목을 추가합니다.
1. 체크아웃 과정에서 미니 장바구니, 장바구니, 결제 단계에 유의하세요.

<u>예상 결과</u>:

[!DNL PayPal] 및 [!DNL Braintree]의 결제 옵션이 미니 장바구니 및 장바구니에 표시되지 않습니다.

<u>실제 결과</u>:

[!DNL PayPal] 및 [!DNL Braintree]의 결제 옵션이 미니 장바구니 및 장바구니에 계속 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
