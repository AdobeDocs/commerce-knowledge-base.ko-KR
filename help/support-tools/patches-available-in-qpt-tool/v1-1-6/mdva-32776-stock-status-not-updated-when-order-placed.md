---
title: 'MDVA-32776: 재고 상태가 주문 배치로 업데이트되지 않음'
description: MDVA-32776 패치는 주문이 시작되었지만 배송되지 않은 경우 재고 상태가 업데이트되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-32776입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 10e9458f-562a-480b-b813-104a93db4308
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32776: 재고 상태가 주문 배치로 업데이트되지 않음

MDVA-32776 패치는 주문이 시작되었지만 배송되지 않은 경우 재고 상태가 업데이트되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-32776입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 메서드) 2.4.0

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문이 되었으나 출고되지 않은 경우 재고 상태가 업데이트되지 않습니다.

<u>필수 구성 요소</u>:

1. 인벤토리 모듈이 설치되었습니다.
1. 품절 제품 표시가 *예*(으)로 설정되어 있습니다.

   설정하려면 **스토어** > **구성** > **카탈로그** > **인벤토리** > **재고 부족 제품 표시** = *예*(으)로 이동하십시오.

<u>재현 단계</u>:

1. 수량 = 11 및 22인 두 개의 간단한 제품을 생성합니다.
1. 1단계에서 만든 간단한 제품을 사용하여 그룹화된 제품을 만듭니다.
1. 제품 수량 중 하나를 11로 설정하고 다른 간단한 제품의 재고를 소진하여 그룹화된 제품을 장바구니에 추가합니다.
1. 체크아웃을 완료하고 주문을 합니다.

<u>예상 결과</u>:

연결된 단순 제품의 재고가 부족하면 그룹화된 제품에 `out-of-stock` 레이블이 표시됩니다.

<u>실제 결과</u>:

1. 수량 = 11인 간단한 제품은 품절되었습니다.
1. 수량 = 11인 제품에 대해 그룹화된 제품에 *품절* 메시지가 표시되지 않습니다. 그러나 이 제품을 장바구니에 추가하면 *재고 부족* 오류가 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
