---
title: 'ACSD-46770: [!UICONTROL Email Order Confirmation]을(를) 선택하지 않은 경우에도 주문 확인 전자 메일이 전송됩니다.'
description: '[!UICONTROL Email Order Confirmation]을(를) 선택하지 않았더라도 주문 확인 전자 메일이 전송되는 Adobe Commerce 문제를 해결하려면 ACSD-46770 패치를 적용하십시오.'
exl-id: 9cbf3a57-1f59-4030-b432-0e6cad410a27
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46770: **[!UICONTROL Email Order Confirmation]**&#x200B;을(를) 선택하지 않은 경우에도 주문 확인 이메일을 보냅니다.

ACSD-46770 패치는 **[!UICONTROL Email Order Confirmation]**&#x200B;을(를) 선택 취소한 경우에도 게스트 사용자로 REST API를 통해 주문을 할 수 있는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-46770입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Email Order Confirmation]**&#x200B;을(를) 선택하지 않은 경우에도 주문 확인 전자 메일이 전송됩니다.

<u>재현 단계</u>:

1. 고객 계정을 만듭니다.
1. **[!UICONTROL Sales]** > **[!UICONTROL Order]**(으)로 이동한 다음 **[!UICONTROL Create New Order]**&#x200B;을(를) 클릭합니다.
1. 고객을 선택하고 주문에 제품을 추가하고 주소를 입력한 다음 배송 및 결제 방법을 선택합니다.
1. 주문을 제출하기 전에 **[!UICONTROL Email Order confirmation]** 확인란 선택을 취소하십시오.
1. 주문을 만들려면 **[!UICONTROL Submit Order]**&#x200B;을(를) 클릭하십시오.

<u>예상 결과</u>:

**[!UICONTROL Email Order Confirmation]**&#x200B;을(를) 선택하지 않은 경우 주문 확인 이메일을 보내지 마십시오.

<u>실제 결과</u>:

선택하지 않은 **[!UICONTROL Email Order Confirmation]** 확인란과 관계없이 주문 확인 전자 메일이 전송됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
