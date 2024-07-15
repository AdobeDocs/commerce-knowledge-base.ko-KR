---
title: 'ACSD-49849: 고객 이메일이 PayPal 이메일로 대체됨'
description: ACSD-49849 패치를 적용하여 GraphQL을 통해 PayPal Express로 주문할 때 고객 이메일이 PayPal 이메일로 대체되는 Adobe Commerce 문제를 해결합니다.
exl-id: 826ea90a-ac10-43e8-aa88-bd69b152ded8
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-49849: 고객 이메일이 [!DNL PayPal] 이메일로 대체되었습니다.

ACSD-49849 패치는 GraphQL을 통해 [!DNL PayPal Express]을(를) 주문할 때 고객 전자 메일이 [!DNL PayPal's] 전자 메일로 대체되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-49849입니다. 이 문제는 Adobe Commerce 2.4.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL을 통해 [!DNL PayPal Express]을(를) 주문하면 고객의 전자 메일이 [!DNL PayPal's] 전자 메일로 대체됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**(으)로 이동합니다.
1. [!DNL PayPal Express]을(를) 사용 및 구성하고 **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**&#x200B;을(를) 설정합니다.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**(으)로 이동하여 간단한 제품을 만드십시오.
1. GraphQL을 사용하여 게스트 체크아웃을 완료합니다. 자세한 내용은 Adobe Commerce 개발자 설명서에서 [GraphQL 체크아웃 튜토리얼](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/)을 참조하세요.
1. 결제 방법으로 [!DNL PayPal Express]을(를) 사용합니다.
1. Adobe Commerce 개발자 설명서에서 [장바구니에 대한 전자 메일을 설정](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/)하는 단계에서 사용한 전자 메일을 확인합니다.
1. 주문이 처리되면 Adobe Commerce 관리자로 이동하여 작성된 주문에서 이메일을 확인합니다.

<u>예상 결과</u>:

이메일은 체크아웃 중에 설정된 것과 동일합니다.

<u>실제 결과</u>:

체크 아웃 중에 설정된 전자 메일은 [!DNL PayPal] 계정의 전자 메일 집합에 의해 재정의됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
