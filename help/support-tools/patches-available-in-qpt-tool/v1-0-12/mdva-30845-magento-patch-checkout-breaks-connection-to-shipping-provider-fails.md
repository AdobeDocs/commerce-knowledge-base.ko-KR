---
title: 'MDVA-30845: 체크아웃이 배송 공급자에 대한 연결을 끊습니다.'
description: MDVA-30845 패치는 이 주문에 대해 *죄송합니다. 현재 견적을 사용할 수 없습니다.* 체크아웃 중에 UPS XML/USPS/DHL에 연결하지 못하면 오류가 표시되고 다른 배송 방법을 사용할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12가 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 수정됩니다.
exl-id: 7be54213-1762-431b-bd3b-080c3d45f492
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-30845: 체크아웃이 배송 공급자에 대한 연결을 끊습니다.

MDVA-30845 패치는 체크아웃 중에 UPS XML/USPS/DHL에 연결하지 못할 때 *죄송합니다. 현재 이 주문에 대해 견적을 사용할 수 없습니다* 오류가 표시되고 다른 배송 방법을 사용할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전:** Adobe Commerce on cloud infrastructure 2.3.5-p2에 대한 패치가 만들어졌습니다.

**Adobe Commerce 버전과 호환:** Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.5-2.3.6.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

체크아웃하는 동안 *죄송합니다. 현재 이 주문에 대해 견적을 사용할 수 없습니다.* 오류가 UPS XML/USPS/DHL에 연결하지 못할 때 표시되며 다른 배송 방법도 사용할 수 없습니다.

<u>재현 단계:</u>

1. 제품을 만듭니다.
1. UPS XML 배송 방법을 활성화하고 구성합니다.
1. 상점 앞의 장바구니에 제품을 추가합니다.
1. UPS 배송 방법과 정액 배송이 가능한지 확인하십시오.
1. USP가 해당 게이트웨이에 연결되는 것을 방지하기 위해 호스트 파일을 편집합니다.
1. 매장 앞에서 요금을 받으시고 다시 계산해 주세요.

<u>실제 결과:</u>

*죄송합니다. 현재 이 주문에 대해 사용 가능한 견적이 없습니다* 오류가 표시되고 정액 배송을 사용할 수 없습니다.

<u>예상 결과:</u>

오류 메시지가 표시되지 않고 정액 배송을 사용할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).


## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
