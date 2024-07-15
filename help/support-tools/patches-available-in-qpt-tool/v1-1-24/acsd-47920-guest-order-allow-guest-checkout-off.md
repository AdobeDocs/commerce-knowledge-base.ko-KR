---
title: 'ACSD-47920: 게스트 사용자는 [!UICONTROL Allow Guest Checkout]이(가) 꺼져 있는 경우에도 REST API를 통해 주문할 수 있습니다.'
description: '[!UICONTROL Allow Guest Checkout]이(가) 꺼져 있더라도 REST API를 통해 게스트 사용자로 주문을 할 수 있는 Adobe Commerce 문제를 해결하려면 ACSD-47920 패치를 적용합니다.'
exl-id: 8726eac4-ab19-4232-8e15-270d09bdc0a5
feature: REST, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-47920: 게스트 사용자는 **[!UICONTROL Allow Guest Checkout]**&#x200B;이(가) 꺼져 있는 경우에도 REST API를 통해 주문할 수 있습니다.

ACSD-47920 패치는 **[!UICONTROL Allow Guest Checkout]**&#x200B;이(가) 꺼져 있어도 게스트 사용자로 REST API를 통해 주문을 할 수 있는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-47920입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**[!UICONTROL Allow Guest Checkout]**&#x200B;이(가) 꺼져 있는 경우에도 Rest API를 통해 게스트 사용자로 주문을 할 수 있습니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리자 > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** >(으)로 이동하여 **[!UICONTROL Allow Guest Checkout]**&#x200B;을(를) _아니요_(으)로 설정합니다.
1. REST API를 사용하여 장바구니에 제품을 추가하고 주문합니다.

<u>예상 결과</u>:

**[!UICONTROL Allow Guest Checkout]**&#x200B;이(가) _아니요_(으)로 설정된 경우 게스트 체크아웃 API에서 오류 *[!UICONTROL Sorry, guest checkout is not available]*&#x200B;을(를) 반환합니다.

<u>실제 결과</u>:

게스트 체크아웃 API를 사용하면 **[!UICONTROL Allow Guest Checkout]**&#x200B;이(가) _아니요_(으)로 설정된 경우에도 주문을 할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
