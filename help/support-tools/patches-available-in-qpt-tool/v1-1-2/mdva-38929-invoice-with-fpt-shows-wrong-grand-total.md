---
title: 'MDVA-38929: FPT가 있는 송장에 잘못된 합계가 표시됨'
description: MDVA-38929 패치는 주문이 스토어 크레딧으로 결제될 때 FPT가 있는 송장에 잘못된 총계가 표시되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38929입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 1ed0e311-f4a5-4dc0-98fc-fc1cc9458516
feature: Invoices, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-38929: FPT가 있는 송장에 잘못된 합계가 표시됨

MDVA-38929 패치는 주문이 스토어 크레딧으로 결제될 때 FPT가 있는 송장에 잘못된 총계가 표시되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-38929입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.3

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

FPT가 포함된 인보이스에는 스토어 크레딧으로 주문을 결제할 때 잘못된 총계가 표시됩니다.

<u>재현 단계</u>:

1. 고객을 만들고 고객이 주문을 처리할 만큼 충분한 스토어 크레딧을 보유하고 있는지 확인합니다.
1. FPT를 활성화하고 FPT를 제품에 추가합니다.
1. 프론트엔드에서 고객이 방금 생성한 (으)로 로그인합니다.
1. FPT가 포함된 제품을 장바구니에 추가합니다.
1. 체크아웃 및 스토어 크레딧으로 결제. 제로페이 주문이어야 합니다.
1. 주문으로 이동하여 수동으로 주문의 송장을 발행합니다.
1. 송장 총계를 확인합니다.

<u>예상 결과</u>:

* 송장 총계는 0입니다.
* 주문 총 결제 금액은 0입니다.

<u>실제 결과</u>:

* 송장 총계에는 여전히 FPT 금액이 표시됩니다.
* 총 지불된 금액은 여전히 FPT 금액을 보여줍니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하십시오.
