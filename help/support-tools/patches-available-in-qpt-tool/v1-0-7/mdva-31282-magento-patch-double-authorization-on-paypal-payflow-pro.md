---
title: 'MDVA-31282: Paypal PayFlow Pro의 이중 인증'
description: MDVA-31282 패치는 Adobe Commerce의 Paypal PayFlow Pro에서 두 번 권한이 발생할 때 문제를 해결합니다. 이중 허가는 페이플로우 프로의 사기 필터를 우회하고 거래 수수료를 배가하는 효과도 있다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우 사용할 수 있습니다.
exl-id: f239012e-e1bd-474b-aad2-7218ec3a3d1b
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31282: Paypal PayFlow Pro에서 이중 인증

MDVA-31282 패치는 Adobe Commerce의 Paypal PayFlow Pro에서 두 번 권한이 발생할 때 문제를 해결합니다. 이중 허가는 페이플로우 프로의 사기 필터를 우회하고 거래 수수료를 배가하는 효과도 있다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라의 Adobe Commerce 2.3.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.2 - 2.3.3 및 2.3.5 - 2.3.6

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Adobe Commerce의 PayPal PayFlow Pro에서 PayFlow Pro의 사기 필터를 우회하고 거래 수수료를 두 배로 인상하는 효과가 발생하는 이중 허가가 발생합니다.

<u>필수 구성 요소</u>:

PayPal PayFlow Pro 결제 방법을 구성합니다.

<u>재현 단계</u>:

1. 프론트엔드에 손님 손님으로 가시면 됩니다
1. 제품 페이지에서 **장바구니**&#x200B;에 제품을 추가하십시오.
1. **체크아웃**&#x200B;을 진행합니다.
1. **배송 주소**&#x200B;을(를) 국가 \#1(예: 영국 주소)의 주소로 지정하고 배송 방법을 선택하십시오.
1. 결제 방법으로 **PayPal PayFlow Pro**&#x200B;을(를) 선택하십시오. **청구 주소**&#x200B;을(를) 국가 \#2에 있는 주소로 지정하십시오(예: 미국 주소).
1. 신용 카드 데이터를 입력하고 주문합니다.
1. 관리자의 **판매** > **주문**(으)로 이동하여 만들어진 주문을 확인합니다.

<u>예상 결과</u>:

* 결제 정보 블록에 표시되는 항목: *&quot;트리거된 사기 필터: RESPMSG: 사기 서비스에서 검토 중*. *순서가 사기성이 의심되는 상태입니다.&quot;*.
* Paypal PayFlow Pro는 예상대로 단일 인증 트랜잭션을 표시합니다.

<u>실제 결과</u>:

* 결제 정보 블록에 표시되는 항목: *&quot;트리거된 사기 필터: RESPMSG: 사기 서비스에서 검토 중*. *주문의 처리 상태&quot;*.
* Paypal PayFlow Pro는 이중 인증 거래를 보여줍니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
