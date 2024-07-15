---
title: 'MDVA-30594: 여러 주소 체크아웃 오류'
description: MDVA-30594 패치는 여러 주소가 있는 주문을 수행한 후 고객이 주문 성공 페이지를 보지 못하는 문제를 해결합니다. Commerce 관리자의 주문을 확인하면 올바른 제품 대신 동일한 제품이 있는 두 개의 주문이 표시됩니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우 사용할 수 있습니다. Adobe Commerce 2.4.2에서 문제가 해결되었습니다.
exl-id: 7560cc39-ff0d-4313-979e-5cd588554c1d
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# MDVA-30594: 여러 주소 체크아웃 오류

MDVA-30594 패치는 여러 주소가 있는 주문을 수행한 후 고객이 주문 성공 페이지를 보지 못하는 문제를 해결합니다. Commerce 관리자의 주문을 확인하면 올바른 제품 대신 동일한 제품이 있는 두 개의 주문이 표시됩니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우에 사용할 수 있습니다. Adobe Commerce 2.4.2에서 문제가 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라의 Adobe Commerce 2.3.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

여러 주소 주문이 주문 성공 페이지로 완료되지 않고 동일한 제품이 아닌 두 개의 주문을 표시합니다.

<u>필수 구성 요소</u>:

스토어 및 스토어 조회수를 사용하여 웹 사이트 두 개를 만듭니다.

<u>재현 단계</u>:

1. 웹 사이트 카탈로그(**스토어** > **설정** > **구성** > **카탈로그** > **카탈로그** > **가격** > **범위**)에 대해 **카탈로그 가격 범위**&#x200B;를 설정합니다.
1. **고정 제품 세금(FPT)** 구성(**스토어** > **구성** > **판매** > **세금** > **고정 제품 세금**):

   * **FPT 사용** = *예*
   * **제품 목록에 가격 표시** = *FPT 제외*
   * **제품 보기 페이지의 가격 표시** = *FPT 제외*
   * **판매 모듈의 가격 표시** = *FPT 제외*(**FPT** 설명 및 최종 가격 포함).
   * **전자 메일의 가격 표시** = *FPT 제외*(**FPT** 설명 및 최종 가격 포함).
   * **FPT에 세금 적용** = *예*
   * **소계에 FPT 포함** = *아니요*

1. **FPT 특성**&#x200B;을(를) 만들고 기본 특성 집합에 할당합니다. 사용 안내서에서 [FPT 구성: FPT 특성 만들기](https://docs.magento.com/user-guide/tax/fixed-product-tax-configuration.html#step-2-create-an-fpt-attribute)를 참조하십시오.

1. 4개의 간단한 제품을 만들고 **FPT** **특성 값**&#x200B;을 설정합니다(예: **FPT** 설정).   **특성 값** = *호주*).

1. 다음 구성으로 두 개의 번들 제품을 만듭니다.

   * **FPT**&#x200B;을(를) 정의합니다.
   * **동적 가격** = *아니요*&#x200B;를 설정합니다.
   * **가격** = *100*&#x200B;을 설정합니다.
   * 번들 옵션이 함께 제공되었으며, 모두 **가격 유형** = *고정*(으)로 기본값으로 표시되었습니다.
   * 4단계에서 만든 간단한 제품 중 2개를 추가합니다.

1. 프론트엔드에 사용자 계정을 만듭니다. 주소를 호주 주소(국가를 호주 또는 **FPT** 설정에서 사용된 국가 설정)로 업데이트합니다.

1. 두 개의 번들 제품을 장바구니에 추가합니다.

1. 장바구니 페이지로 이동하여 **FPT**&#x200B;이(가) 올바르게 표시되는지 확인하십시오.

1. **여러 주소가 있는 체크 아웃**&#x200B;을 클릭합니다.

1. 두 번째 주소를 추가합니다.

1. 각 제품을 다른 주소에 할당합니다.

1. 최대 **주문**&#x200B;까지 체크아웃 프로세스를 계속합니다.

1. **주문** 단추를 클릭합니다.

<u>예상 결과</u>:

주소가 여러 개인 주문이 완료되었습니다.

<u>실제 결과</u>:

&quot;*오류가 발생했습니다.*&quot;이(가) 나타납니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
