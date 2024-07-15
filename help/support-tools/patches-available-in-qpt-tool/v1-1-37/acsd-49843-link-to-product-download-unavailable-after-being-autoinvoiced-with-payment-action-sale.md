---
title: 'ACSD 49843: [!UICONTROL Payment Action] = [!UICONTROL Intent Sale](으)로 자동 송장 발행 후 제품 다운로드 링크를 사용할 수 없음'
description: '[!UICONTROL Payment Action]이(가) [!UICONTROL Intent Sale](으)로 설정되어 있을 때 온라인 결제 방법으로 주문 항목에 자동 송장을 보낸 후 제품 다운로드 링크를 사용할 수 없는 Adobe Commerce 문제를 해결하려면 ACSD-49843 패치를 적용합니다.'
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843: [!UICONTROL Payment Action] = [!UICONTROL Intent Sale](으)로 자동 송장 발행 후 제품 다운로드 링크를 사용할 수 없음

ACSD-49843 패치는 [!UICONTROL Payment Action]이(가) [!UICONTROL Intent Sale](으)로 설정되어 있을 때 온라인 결제 방법으로 주문 항목에 자동 송장을 보낸 후 제품 다운로드 링크를 사용할 수 없는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.37이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-49843입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!UICONTROL Payment Action]이(가) [!UICONTROL Intent Sale](으)로 설정되어 있을 때 온라인 결제 방법으로 주문 항목에 자동 송장을 발행하면 제품 다운로드 링크를 사용할 수 없습니다.

<u>재현 단계</u>:

1. Adobe Commerce 관리자에 로그인하고 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**(으)로 이동합니다.

   * [!UICONTROL Payment Action] 드롭다운에서 **[!UICONTROL Intent Sale]**&#x200B;을(를) 선택하고 *[!UICONTROL Enable Card Payments]*&#x200B;을(를) *예*(으)로 설정합니다.

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]**(으)로 이동한 다음 *&quot;인보이스 발행&quot;*(으)로 설정되어 있는지 확인하십시오.
1. 상점에서 고객으로 로그인합니다.

   * 다운로드 가능한 제품과 간단한 제품을 장바구니에 추가합니다.
   * 카드 옵션을 사용하여 주문하려면 [!DNL Braintree Pay]을(를) 사용하십시오.

1. **[!UICONTROL My Orders]**(으)로 이동하여 주문에 대한 송장이 자동으로 만들어졌는지, 항목 상태가 모두 *&quot;인보이스 발행&quot;*&#x200B;인지 확인하십시오.
1. **[!UICONTROL My Downloadable Products]**(으)로 이동하여 다운로드 링크를 아직 사용할 수 없습니다.
1. 관리자에서 해당 주문으로 이동하여 해당 배송을 생성합니다.
1. 상점 앞에서 **[!UICONTROL My Downloadable Products]**(으)로 이동하여 다운로드 링크를 사용할 수 있는지 확인하십시오.

<u>예상 결과</u>:

다운로드 가능한 제품 상태가 *&quot;인보이스 발행&quot;*&#x200B;인 경우 다운로드 링크를 사용할 수 있습니다.

<u>실제 결과</u>:

다운로드 가능한 제품 상태에 *&quot;인보이스 발행&quot;*&#x200B;이(가) 표시되어 있어도 다운로드 링크를 사용할 수 없습니다. 실제 제품에 대한 선적이 생성된 후에만 사용할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
