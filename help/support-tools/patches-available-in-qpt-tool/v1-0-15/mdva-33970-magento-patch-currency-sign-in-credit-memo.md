---
title: 'MDVA-33970 패치: 대변 메모에 통화 로그인'
description: MDVA-33970 패치는 크레딧 메모에서 현지화된 통화 대신 달러($) 기호가 표시되던 문제를 해결했습니다. 이 문제는 **Website** 범위가 **Price** 속성에 사용될 때 발생합니다.
exl-id: 47a03067-86ef-4a55-8c21-921781062b53
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# MDVA-33970 패치: 대변 메모에 통화 로그인

MDVA-33970 패치는 크레딧 메모에서 현지화된 통화 대신 달러($) 기호가 표시되던 문제를 해결했습니다. 이 문제는 **Website** 범위가 **Price** 특성에 사용될 때 발생합니다.

이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.** 클라우드 인프라 2.3.4-p2 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.4 - 2.4.1-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>전제 조건</u>:

이 예에서는 다음 설정이 사용됩니다.

* 웹 사이트가 2개 있습니다. 각각 **스토어** 및 **스토어 보기**&#x200B;가 있습니다.
* **기본 구성**&#x200B;에 **통화**(상점 > 구성 > 일반 > 통화 설정&#x200B;**)로서 싱가포르 달러가 있습니다.**
   * **기본 통화** = *싱가포르 달러*
   * **기본 표시 통화** = *싱가포르 달러*
   * **허용된 통화** = *싱가포르 달러*
* **웹 사이트 1**&#x200B;에 **기본 구성**&#x200B;이 있습니다.
* **웹 사이트 2**&#x200B;에 **통화**(으)로 말레이시아 링깃이 있습니다.
   * **기본 통화** = *말레이시아 링깃*
   * **기본 표시 통화** = *말레이시아 링깃*
   * **허용된 통화** = *말레이시아 링깃*
* **스토어 > 통화 기호**(으)로 이동하여 다음을 설정합니다.
   * **MYR(말레이시아 링기트)** = *RM*
   * **SGD(싱가포르 달러)** = *SGD* (**표준 사용** = *선택됨*)
* 일부 **제품**&#x200B;이(가) 있습니다.

<u>재현 단계</u>:

1. **웹 사이트 2**&#x200B;에서 **주문**&#x200B;을 만듭니다(추가 설정을 방지하기 위해 기본값으로 설정할 수 있음).
1. **관리자**&#x200B;에 로그인합니다.
1. 새로 생성된 주문을 엽니다.
1. **통화 기호** = *RM*&#x200B;이 있는지 확인하십시오.
1. **송장**&#x200B;을(를) 만듭니다.
1. 송장에 **통화 기호** = *RM*&#x200B;이 있는지 확인하십시오.
1. **대변 메모**&#x200B;를 만듭니다.
1. **신용 메모**&#x200B;에서 **통화 기호** ** ** = *RM*&#x200B;을(를) 확인하십시오.
1. **주문**&#x200B;에서 **신용 메모** 탭을 엽니다.
1. 격자에서 **통화 기호**&#x200B;를 확인하세요.
1. **판매 > 대변 메모**&#x200B;를 엽니다.
1. 격자에서 **통화 기호**&#x200B;를 확인하세요.

<u>예상 결과</u>:

예상대로 올바른 현지화된 통화 기호가 사용됩니다.

<u>실제 결과</u>:

달러($) 기호는 관리자 설정에서 설정하지 않았더라도 사용됩니다.

## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 다음 링크를 사용하십시오.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
