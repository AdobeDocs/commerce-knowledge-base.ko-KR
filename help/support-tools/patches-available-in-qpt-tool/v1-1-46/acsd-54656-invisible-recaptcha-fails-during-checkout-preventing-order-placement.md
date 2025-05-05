---
title: 체크 아웃 중에 보이지 않는  [!DNL reCAPTCHA] 이(가) 실패하여 주문 배치가 되지 않음
description: ACSD-54656 패치를 적용하여 체크아웃 중에 보이지 않는  [!DNL reCAPTCHA] 이(가) 제대로 작동하지 않아 주문 배치가 되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Checkout, Gift
role: Admin, Developer
exl-id: dc26659e-ca34-461e-af91-b230c5afa919
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54656: 체크아웃 중에 보이지 않는 [!DNL reCAPTCHA]이(가) 제대로 작동하지 않아 주문을 배치할 수 없습니다.

ACSD-54656 패치는 체크아웃 중에 보이지 않는 [!DNL reCAPTCHA]이(가) 제대로 작동하지 않아 주문 배치를 방해하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54656입니다. 이 문제는 Adobe Commerce 2.4.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

체크 아웃 중에 보이지 않는 [!DNL reCAPTCHA]이(가) 제대로 작동하지 않아 주문을 배치할 수 없습니다.

<u>재현 단계</u>:

1. [!UICONTROL Checkout] 페이지에서 기프트 카드에 대해 모든 유형의 [!DNL reCAPTCHA]을(를) 사용하도록 설정하십시오.
1. 장바구니에 제품을 추가하고 **[!UICONTROL Checkout]** 페이지로 이동합니다.
1. 기프트 카드 양식을 확장하고 유효한 기프트 카드 쿠폰을 입력합니다.
1. **[!UICONTROL See balance and apply]** 단추를 클릭합니다.

<u>예상 결과</u>:

기프트 카드가 정상적으로 적용되었습니다.

<u>실제 결과</u>:

오류 메시지가 표시됩니다. *[!DNL reCAPTCHA]유효성 검사가 실패했습니다. 다시 시도해 주십시오*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
