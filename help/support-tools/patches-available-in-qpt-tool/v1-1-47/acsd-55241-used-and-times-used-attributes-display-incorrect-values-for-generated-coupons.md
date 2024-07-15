---
title: 'ACSD-55241: **Used** 및 **Times Used** 속성에 생성된 쿠폰에 대한 잘못된 값이 표시됨'
description: ACSD-55241 패치를 적용하여 **사용된 시간** 및 **사용된 시간** 속성에 생성된 쿠폰에 대한 잘못된 값이 표시되는 Adobe Commerce 문제를 해결합니다
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: 5d0b4743fe49d22c099102490f93dc4065ab4413
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-55241: **사용됨** 및 **사용됨** 특성에 생성된 쿠폰에 대한 잘못된 값이 표시됨

ACSD-55241 패치는 **Used** 및 **Times Used** 특성이 생성된 쿠폰의 잘못된 값을 표시하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.47이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-55241입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

**Used** 및 **Times Used** 특성에 생성된 쿠폰의 값이 잘못 표시됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]**&#x200B;에서 **[!UICONTROL Cart Price Rules]**&#x200B;을(를) 만들고 주문하는 동안 일치하는 조건을 추가합니다(예: 소계가 *5$*&#x200B;보다 큼).

* 할인을 적용합니다.
* **[!UICONTROL Auto Coupon]**&#x200B;을(를) 선택합니다.
* **쿠폰 코드 관리**&#x200B;에서 몇 가지 쿠폰 코드를 생성합니다.
* 캐시를 다시 인덱싱하고 정리합니다.

1. **[!UICONTROL customer account]**&#x200B;을(를) 만들고 프런트 엔드에 로그인합니다.
1. 장바구니에 수량이 *2*&#x200B;개를 초과하는 제품 1개를 추가하고 쿠폰 1개를 적용합니다.
1. **[!UICONTROL Check Out with Multiple Addresses]**&#x200B;을(를) 클릭합니다.
1. 각 수량에 대해 별도의 주소를 선택하고 주문을 지정한 다음 체크아웃 프로세스를 완료합니다.
1. 관리자의 주문 합계를 확인하고 적용된 할인을 확인합니다.
1. 다른 쿠폰으로 다시 주문하세요.
1. `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` 명령을 실행하여 쿠폰 코드 사용을 업데이트합니다.

<u>예상 결과</u>:

관리자의 **[!UICONTROL cart price rule]**&#x200B;에서 **[!UICONTROL manage coupon]**&#x200B;에 대한 **예** 값이 있는 **사용된 시간** 및 **사용됨** 열에 올바른 개수를 표시해야 합니다.

<u>실제 결과</u>:

쿠폰 그리드의 **사용된 시간** 열에서 사용된 쿠폰 코드 카운트가 업데이트되지 않고, 여러 배송 주소로 주문하는 경우 **사용된 시간** 열에 *없음* 값이 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
