---
title: 'ACSD-46683: 배송 가격 표시 *아직 계산되지 않음*'
description: ACSD-46683 패치를 적용하여 배송비가 *아직 계산되지 않음*으로 표시되는 Adobe Commerce 문제를 해결합니다.
exl-id: 77986612-87b7-4f50-afaf-1cfe9a4feb6f
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-46683: 배송 가격에 *아직 계산되지 않음*&#x200B;이 표시됩니다.

ACSD-46683 패치는 배송 가격에 *아직 계산되지 않음*&#x200B;이 표시되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-46683입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

배송 가격에 *아직 계산되지 않음*&#x200B;이 표시됩니다.

<u>필수 구성 요소</u>:

Adobe Commerce Inventory management(MSI) 모듈이 설치되었습니다.

<u>재현 단계</u>:

1. 간단한 제품을 만들고 가격을 *$34*(으)로 설정합니다.
1. 무료 배송 배송 방법을 구성합니다.
1. 하나 이상의 게재 방법을 구성합니다.
1. **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**(으)로 이동하여 새 규칙을 만듭니다.
   * 이름 = *75more*
   * 쿠폰 = 없음
   * 우선 순위 = 1
   * 조건: 소계가 *$75*&#x200B;보다 크거나 같음
   * 작업:
      * 운송 금액에 적용 = 예
      * 후속 규칙 버리기 = 아니요
      * 무료 출하 = 품목이 일치하는 출하의 경우
1. 다른 장바구니 가격 규칙을 만듭니다.
   * 이름 = *35off*
   * 우선 순위 = 0
   * 쿠폰 = 특정 쿠폰
   * 쿠폰 코드 = 35off
   * 작업:
      * 적용 = 제품 가격 할인의 퍼센트
      * 할인 금액 = 35
      * 운송 금액에 적용 = 아니오
      * 후속 규칙 무시 = 예
      * 무료 배송 = 아니오
1. 가게 앞을 열고 소계가 75달러를 초과하도록 장바구니에 세 가지 제품을 추가합니다.
1. 게스트로 체크아웃을 진행합니다.
1. 배송 단계에서 **$0 - 무료 배송**&#x200B;을 선택하고 결제 단계로 진행합니다.
1. 결제 단계에서 [!UICONTROL Order Summary]을(를) 확인하십시오. *[!UICONTROL $0 - Free Shipping - Free]*&#x200B;을(를) 표시합니다.
1. 쿠폰 코드 *35off*&#x200B;를 적용하면 소계가 업데이트되고 $75 미만이 됩니다.
1. 결제 단계에서 [!UICONTROL Order Summary]을(를) 확인하십시오.

<u>예상 결과</u>:

다음 메시지가 표시됩니다. *선택한 배송 방법을 사용할 수 없습니다. 이 주문의 다른 배송 방법을 선택하십시오.*

<u>실제 결과</u>:

배송 가격이 *아직 계산되지 않음*&#x200B;으로 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
