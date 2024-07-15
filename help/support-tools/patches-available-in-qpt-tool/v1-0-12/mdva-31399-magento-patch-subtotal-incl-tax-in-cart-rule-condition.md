---
title: '''MDVA-31399 패치: 소계(포함). 장바구니 규칙 조건의 세금)'
description: MDVA-31399 패치는 *소계(포함)를 추가합니다. 세금)* 소계를 기반으로 장바구니 가격 규칙을 적용할 수 없었던 문제를 수정하여 [장바구니 가격 규칙 조건](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions)에 옵션을 제공합니다(포함). 세금) 번호. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12가 설치된 경우 사용할 수 있습니다.
exl-id: ea0f4060-753a-4b0d-896b-fff54ffd1a82
feature: Marketing Tools, Orders, Shopping Cart, Taxes
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-31399 패치: 소계(포함) 장바구니 규칙 조건의 세금)

MDVA-31399 패치가 *Subtotal(포함)을 추가합니다. 세금)* 옵션을 [장바구니 가격 규칙 조건](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions)에 추가하여 소계(포함)를 기준으로 장바구니 가격 규칙을 적용할 수 없는 문제를 해결했습니다. 세금) 번호. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12가 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.5-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.2 - 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

소계(포함)에 기반한 장바구니 가격 규칙을 적용할 수 없습니다. 세금) 번호.

<u>재현 단계</u>:

1. 세금을 포함하도록 제품 가격을 구성합니다.
1. 20%에 대한 세금 규칙 및 세율을 생성합니다.
1. **가격** = *100*(이 가격에는 세금이 포함됨)인 제품을 만드십시오.
1. 소계가 다음 조건과 일치하는 경우 $10 고정 할인을 적용하려면 쿠폰이 &quot;10off&quot;인 새 장바구니 가격 규칙을 만듭니다.

**조건**: *이 조건이 모두 TRUE인 경우:*        * **소계**&#x200B;가 100보다 크거나 같음.*

<u>예상 결과</u>:

세금을 포함한 소계에 할인을 적용할 수 있는 쿠폰이 있는 소계 장바구니 가격 규칙을 생성할 수 있습니다.

<u>실제 결과</u>:

장바구니 규칙 조건에는 *소계* 및 *소계(제외)의 두 가지 옵션이 있습니다. Tax)* 및 어떤 항목을 선택하든 세금 제외 소계에만 규칙이 적용됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
