---
title: 'MDVA-33482 패치: 대변 메모의 세금 계산 착오'
description: MDVA-33482 패치는 대변 메모에서 세금이 잘못 계산되는 문제를 해결합니다.
exl-id: 80740e6f-2b6c-4770-9a1a-58ba68a1b28f
feature: Orders, Returns, Taxes
role: Admin
source-git-commit: 0ffa6d63f7046048f7e8f0e9fab1ee1869c98e93
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-33482 패치: 대변 메모의 세금 계산 착오

MDVA-33482 패치는 조정 수수료 또는 조정 환불이 적용되지 않을 때 대변 메모에서 세금이 잘못 계산되는 문제를 해결합니다.

이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전용 패치가 생성되었습니다.** 클라우드 인프라 2.4.0의 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.5 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. **세금**&#x200B;을(를) 구성합니다.
1. 온라인 결제 방법을 사용하여 백엔드에서 두 제품을 사용하여 주문을 만듭니다(예: [!DNL PayPal Payment Pro]). 모든 제품에 세금이 적용되는지 확인하십시오.
1. 주문에 대한 두 개의 송장을 생성합니다.
1. 송장 중 하나에 대해 대변 메모를 생성합니다. 조정 수수료나 조정 환급을 적용하려는 경우에는 이 솔루션을 적용할 수 없습니다.
1. 대변 메모 합계를 확인합니다.

<u>예상 결과</u>:

예상대로 대변 메모에는 부분적으로 인보이스된 세금만 있습니다.

<u>실제 결과</u>:

전체 세액이 대변 메모에 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 다음 링크를 사용하십시오.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
