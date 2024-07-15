---
title: 'MDVA-34591: 장바구니 가격 규칙이 예상과 다르게 계산됨'
description: MDVA-34591 패치는 **최대 할인 적용 대상**의 장바구니 가격 규칙이 여러 장바구니 가격 규칙이 적용되는 경우 제대로 작동하지 않는 문제를 해결했습니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-34591입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.
exl-id: 1fa196bb-aab1-4364-a1b0-7c31d6d27d6d
feature: Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# MDVA-34591: 장바구니 가격 규칙이 예상과 다르게 계산됨

MDVA-34591 패치는 **최대 할인 대상**&#x200B;이 적용된 장바구니 가격 규칙이 여러 장바구니 가격 규칙이 적용되는 경우 제대로 작동하지 않는 문제를 해결했습니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-34591입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.6

**Adobe Commerce 버전과 호환:**

Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.0-2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. 관리자로 이동하여 다음 두 가지 규칙을 만듭니다.

   * 규칙 1: 장바구니에서 최대 3개 항목 $10 할인. 우선 순위 = *3*.
   * 규칙 2: 장바구니에 있는 모든 제품 50% 할인. 우선 순위 = *1*&#x200B;을(를) 설정합니다.

1. 가게 앞쪽으로 가보세요

1. 가격 = *$51*(으)로 설정된 제품의 8개 수량을 장바구니에 추가합니다.

1. 장바구니에서 할인 금액을 확인합니다.

<u>예상 결과</u>:

예상대로 올바른 계산된 할인율은 $234입니다.

* 계산:

  일치하는 장바구니 가격 규칙: 규칙 2, 규칙 1\
  규칙 2 적용(50% 할인), 따라서 할인 = $204\
  규칙 1 적용(3개 품목 중 10개), 따라서 할인 = $30\
  총 할인 = 분 ( 408/2 + 10x3, 8 &#42; 51) = 분 (204 + 30, 8 &#42; 51) = $234

<u>실제 결과</u>:

장바구니에서 상품의 금액과 상관없이 고정 할인액이 적용되므로 최대 할인액 계산에 사용된 수량이 잘못되어 할인액이 $153로 잘못 계산된다.

* 계산:

  일치하는 장바구니 가격 규칙: 규칙 2, 규칙 1\
  규칙 2 적용(50% 할인), 따라서 할인 = $204\
  규칙 1 적용(3개 품목 중 10개), 따라서 할인 = $30\
  총 할인 = 최소(204 + 30, 3 &#42; 51) = $153

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
