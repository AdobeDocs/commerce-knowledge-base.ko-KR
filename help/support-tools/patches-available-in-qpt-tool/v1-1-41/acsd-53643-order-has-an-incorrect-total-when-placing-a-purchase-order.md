---
title: 'ACSD-53643: 구매 발주 시 주문 합계가 잘못됨'
description: ACSD-53643 패치를 적용하여 사용하지 않거나 재고 부족 제품이 있는 구매 발주를 수행할 때 주문 합계가 잘못된 Adobe Commerce 문제를 해결합니다.
feature: B2B
role: Admin, Developer
exl-id: 9843e07a-8a17-401e-98bc-559df5148d34
source-git-commit: 2356ac10b05ae9f38e5c0ca90d9156b0fc405718
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-53643: 구매 발주 시 주문의 합계가 잘못됨

ACSD-53643 패치는 사용 불능 또는 재고 부족 제품으로 구매 주문을 할 때 주문 합계가 올바르지 않은 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-53643입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용 불능 또는 재고 부족 제품이 있는 구매 발주를 지시할 때 주문 합계가 올바르지 않습니다.

<u>재현 단계</u>:

1. *[!UICONTROL B2B]* 및 *[!UICONTROL Inventory]*&#x200B;을(를) 설치합니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]**(으)로 이동하여 **[!UICONTROL Company]** = *예* 및 **[!UICONTROL Purchase Order]** = *예*&#x200B;를 설정합니다.
1. 구성 캐시를 지웁니다.
1. 새 회사를 만들어 활성화한 다음 회사에 대해 *[!UICONTROL Purchase order]*&#x200B;을(를) 사용하도록 설정합니다.
1. 회사에 대한 새 사용자를 만듭니다.
1. 회사 관리자가 *1USD*&#x200B;을(를) 초과하는 모든 주문을 승인하려면 *승인 규칙*&#x200B;을(를) 만드십시오.
1. 추가 소스를 만듭니다.
1. 새 회사 사용자로 로그인
1. 장바구니에 제품 2개를 추가하고 구매합니다.
1. 두 번째 제품을 비활성화합니다.
1. 회사 관리자로 로그인합니다.
1. 구매 발주를 열고 구매 발주에 두 제품이 모두 포함되어 있고 합계가 두 제품 모두에 대해 있는지 확인합니다.
1. 구매 주문을 승인합니다.
1. 주문하십시오.
1. 주문 세부 사항을 엽니다.

<u>예상 결과</u>:

* 주문된 제품 중 하나가 *비활성화됨* 또는 *재고 부족*&#x200B;인 경우에도 주문할 수 없습니다.
* *[!UICONTROL Place Order]* 단추가 숨겨져 있습니다.

<u>실제 결과</u>:

주문에는 첫 번째 활성 제품만 포함되지만 주문 합계는 두 제품 모두에 대해 계산됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
