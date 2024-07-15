---
title: 'ACSD-48694: 잘못된 상태 변경 요청 오류로 인해 고객이 주문을 할 수 없음'
description: ACSD-48694 패치를 적용하여 *잘못된 상태 변경 요청* 오류로 인해 고객이 주문을 할 수 없는 Adobe Commerce 문제를 해결합니다.
exl-id: edf79424-6c4f-4cfd-ab7e-19f95b9bc685
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-48694: *잘못된 상태 변경 요청* 오류로 인해 고객이 주문을 할 수 없습니다.

ACSD-48694 패치는 오류 *잘못된 상태 변경 요청*&#x200B;으로 인해 고객이 주문을 할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48694입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*잘못된 상태 변경이 요청되었습니다* 오류로 인해 고객이 주문을 할 수 없습니다.

<u>재현 단계</u>:

1. 체크아웃 중에 배송 단계에서 결제 단계로 이동할 때 `/shipping-information` 이후에 `/estimate-shipping-methods` 요청이 완료되도록 `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` 함수에 `sleep()`을(를) 포함하여 `/estimate-shipping-methods` 요청 중에 약간의 지연을 추가합니다.
1. *disable_locking: 1* 설정으로 [!DNL Redis]을(를) 사용하도록 세션을 구성하십시오.
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**&#x200B;을(를) 열고 *[!UICONTROL Persistent Shopping Cart]*&#x200B;을(를) 활성화합니다.
1. 고객으로 로그인하여 장바구니에 제품을 추가합니다.
1. 고객 세션이 만료되도록 합니다. 영구적 쿠키 및 장바구니는 계속 유지됩니다.
1. 이제 체크아웃으로 이동하여 배송 주소를 추가하고 결제 섹션으로 이동합니다.
1. 홈 페이지 또는 다른 페이지로 돌아가서 고객 계정으로 로그인합니다.
1. 세션이 다시 만료되도록 합니다.
1. 이제 체크아웃 페이지로 바로 이동하여 결제 단계로 이동합니다.
1. 주문해 보세요.

<u>예상 결과</u>:

* 오류가 없습니다.
* 주문이 완료되었으며 *감사합니다* 페이지가 표시됩니다.

<u>실제 결과</u>:

*잘못된 상태 변경 요청* 오류가 표시되었지만 순서가 변경되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
