---
title: 'ACSD-49737: 쿠폰이 카드 결제 실패 후 사용된 것으로 잘못 표시됨'
description: ACSD-49737 패치를 적용하여 카드 결제가 실패한 후 쿠폰이 사용된 것으로 잘못 표시되는 Adobe Commerce 문제를 해결합니다.
exl-id: 77b5ec9c-3c4c-4da3-ba7e-8be3ccea04d0
feature: Orders, Payments
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49737: 카드 결제 실패 후 쿠폰이 *used*(으)로 잘못 표시됨

ACSD-49737 패치는 카드 결제 실패 후 쿠폰이 *used*(으)로 잘못 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-49737입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

카드 결제 실패 후 쿠폰이 *used*(으)로 잘못 표시되었습니다.

<u>필수 구성 요소</u>:

1. **[!UICONTROL Braintree sandbox payment]** 메서드를 구성합니다.
1. [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=ko) 소비자가 설정되어 실행 중인지 확인하십시오.

<u>재현 단계</u>:

1. 자동 생성된 쿠폰 코드로 **[!UICONTROL Cart Price Rule]**&#x200B;을(를) 만듭니다.
1. 고객으로 로그인.
1. 장바구니에 제품을 추가합니다.
1. 자동 생성된 쿠폰 코드를 적용합니다.
1. 결제가 실패한 주문을 시도해 보십시오.
1. **[!UICONTROL Manage Coupon Codes]** 탭 아래의 **[!UICONTROL Cart Price Rule]**&#x200B;에서 쿠폰 사용을 확인하십시오.

<u>예상 결과</u>:

결제가 실패한 경우 쿠폰은 *사용됨*(으)로 플래그가 지정될 수 없습니다.

<u>실제 결과</u>:

* 쿠폰 코드 메시지 - 사용됨: *예*, 사용 시간: *1*
* 쿠폰 코드는 한 번만 사용할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 패치 설치 후 추가 단계 필요

(이 섹션은 선택 사항입니다. 문제를 해결하기 위해 패치를 적용한 후 몇 가지 단계가 필요할 수 있습니다.) 

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
