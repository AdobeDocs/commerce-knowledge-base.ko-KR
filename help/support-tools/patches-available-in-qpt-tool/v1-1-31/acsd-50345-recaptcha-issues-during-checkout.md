---
title: 'ACSD-50345: 체크아웃 중 reCAPTCHA 문제'
description: ACSD-50345 패치를 적용하여 주문 도중 및 체크아웃 중에 reCAPTCHA v2 및 v3 유효성 검사가 실패하는 Adobe Commerce 문제를 해결합니다.
exl-id: ac8c8130-0e4d-4610-9a55-afa779cce7a0
feature: Checkout, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-50345: 체크아웃 중 reCAPTCHA 문제

ACSD-50345 패치는 주문 도중 및 체크아웃 중에 reCAPTCHA v2 및 v3 유효성 검사가 실패하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-50345입니다. 이 문제는 Adobe Commerce 2.4.6에서 부분적으로 수정되었으며 Adobe Commerce 2.4.7에서 완전히 수정될 예정입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**사례 #1**

실패한 결제를 제출한 후 Google reCAPTCHA v2가 다시 로드되지 않습니다.

<u>재현 단계</u>

1. **[!UICONTROL Google reCAPTCHA v2]**&#x200B;을(를) 구성합니다(*로봇이 아닙니다*).
1. 체크아웃을 위해 **[!UICONTROL reCAPTCHA]**&#x200B;을(를) 사용하도록 설정합니다.
1. **[!UICONTROL reCAPTCHA]**&#x200B;을(를) 클릭하지 않고 주문해 보십시오.
1. 사용자가 누락된 reCAPTCHA(*reCAPTCHA 유효성 검사 실패)에 대한 오류 메시지를 수신하면 다시 시도하십시오*). **[!UICONTROL reCAPTCHA]**&#x200B;을(를) 클릭한 다음 주문을 시도하십시오.

<u>예상 결과</u>

주문에는 잘못된 reCAPTCHA가 적용되지 않습니다.

<u>실제 결과</u>

오류가 발생했습니다. *reCAPTCHA 유효성 검사에 실패했습니다. 다시 시도하십시오.* 및 *ID = 4*&#x200B;인 해당 장바구니 없음

**사례 #2**

Google reCAPTCHA v3 Invisible이 체크아웃 상태에서 작동하지 않으므로 주문을 할 수 없습니다. `PlaceOrder` 이벤트가 트리거되지 않았습니다.

<u>재현 단계</u>

1. **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**&#x200B;에서 **[!UICONTROL reCAPTCHA v3 Invisible]**&#x200B;을(를) 구성합니다.
1. **[!UICONTROL Storefront]** 탭에서 체크아웃/주문을 위해 **[!UICONTROL reCAPTCHA v3 Invisible]**&#x200B;을(를) 사용하도록 설정하십시오.
1. [!UICONTROL Check/Money order] 결제 방법을 사용하여 주문해 보십시오.

<u>예상 결과</u>

**[!UICONTROL reCAPTCHA]**&#x200B;이(가) 켜진 상태에서 주문을 수행해야 합니다.

<u>실제 결과</u>

**[!UICONTROL Place Order]** 단추를 클릭하면 사용할 수 없게 되며 더 이상 아무 일도 발생하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
