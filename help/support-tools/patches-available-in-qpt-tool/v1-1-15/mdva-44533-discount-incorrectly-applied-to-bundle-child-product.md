---
title: 'MDVA-44533: 번들 하위 제품에 할인이 잘못 적용됨'
description: MDVA-44533 패치는 하위 번들 제품에 할인이 잘못 적용되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-44533입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: 84302ed4-d850-45e4-8b5b-44495f9df820
feature: Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-44533: 번들 하위 제품에 할인이 잘못 적용됨

MDVA-44533 패치는 하위 번들 제품에 할인이 잘못 적용되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-44533입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

하위 묶음 상품에 할인이 잘못 적용됩니다.

<u>재현 단계</u>:

1. 가격이 50$인 간단한 제품을 만들 수 있습니다.
1. 번들 제품을 만들고 간단한 제품을 번들 제품에 대한 유일한 옵션으로 할당합니다.
1. 다음을 사용하여 장바구니 가격 규칙 만들기:

   * 조건: 총 금액이 130$보다 큰 경우
   * 작업: 고정 금액 할인 10$이 적용됨

1. 상점 앞으로 가서 수량 = 1인 카트에 번들 제품을 추가합니다.
1. 장바구니로 이동하여 번들 제품의 총 비용이 50$이고 할인이 적용되지 않는지 확인하십시오.
1. 수량을 2로 변경하고 장바구니를 업데이트합니다. 이제 번들 제품의 총 비용은 100$가 되어야 합니다.

<u>예상 결과</u>:

하위 합계가 규칙 조건에서 130\$보다 작은 100\$이므로 할인이 적용되지 않습니다.

<u>실제 결과</u>:

할인이 적용됩니다

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
