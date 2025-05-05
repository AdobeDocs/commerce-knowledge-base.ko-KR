---
title: 'MDVA-43605: Rest API를 사용할 때 순서 데이터가 행 합계에 대해 음수 값을 반환합니다.'
description: MDVA 43605 패치는 Rest API를 사용할 때 주문 데이터가 행 합계에 대해 음수 값을 반환하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43605입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: 8a679e85-1681-42c3-b072-18797198bdc4
feature: REST, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# MDVA-43605: Rest API를 사용할 때 주문 데이터가 행 합계에 대해 음수 값을 반환합니다.

MDVA 43605 패치는 Rest API를 사용할 때 주문 데이터가 행 합계에 대해 음수 값을 반환하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-43605입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.1 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Rest API를 사용할 때 주문 데이터는 행 합계에 대해 음수 값을 반환합니다.

<u>재현 단계</u>:

1. 무료 배송을 활성화하십시오.
1. **구성** > **카탈로그** > **가격** >(으)로 이동하고 카탈로그 가격 범위 = 웹 사이트를 설정합니다.
1. **구성** > **판매** > **세금**(으)로 이동하여 업데이트하십시오.
   * 운송에 대한 세금 분류 = 과세 물품
   * 계산 설정:
      * 카탈로그 가격 = 세금 포함
      * 출하 가격 = 포함 가격
      * 가격에 할인 적용 = 세금 포함
   * 가격 표시 설정: 세금 포함(모든 필드)
   * 장바구니 표시 설정: 세금 포함(모든 필드)
   * 주문, 송장, 대변 메모:
      * 운송 금액 표시 = 세금 포함
1. 미국(주 = &#39;*&#39;)에 대한 세율을 생성합니다. 세율 퍼센트 = 24.00
1. 위의 세율로 세금 규칙을 생성합니다.
1. 특정 쿠폰이 포함된 장바구니 가격 규칙을 만들고 할인 = 전체 장바구니에 대한 고정 금액의 $50입니다.
1. $8.90, $5.90, $6.90, $5.95의 가격으로 4개의 제품을 만드십시오.
1. 이전 단계에서 만든 쿠폰 코드를 사용하여 이러한 제품 중 4개를 포함하는 관리자 주문을 만듭니다. 무료 배송을 이용하세요.
1. 쿠폰 코드가 장바구니 총액을 포함하므로 결제가 필요하지 않습니다.
1. Rest API 끝점을 통해 방금 만든 주문을 검색합니다.

   ```json
   GET rest/V1/orders/1
   ```

<u>예상 결과</u>:

응답의 `base_row_total` 및 `base_row_total_incl_tax` 값이 0입니다.

<u>실제 결과</u>:

응답의 `base_row_total` 및 `base_row_total_incl_tax` 필드에 음수 값이 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
