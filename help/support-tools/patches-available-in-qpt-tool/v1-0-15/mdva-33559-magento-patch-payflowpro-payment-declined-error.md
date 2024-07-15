---
title: 'MDVA-33559 패치: PayflowPro 결제 거부 오류'
description: MDVA-33559 패치는 PayPal PayflowPro 결제가 거절되는 문제를 해결합니다.
exl-id: aec57ffa-07c7-404e-985d-8ec4fdb019b1
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# MDVA-33559 패치: PayflowPro 결제 거부 오류

MDVA-33559 패치는 PayPal PayflowPro 결제가 거절되는 문제를 해결합니다.

이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전용 패치가 만들어졌습니다.** 클라우드 인프라 2.3.5-p2의 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

이름에 앰퍼샌드 기호(&amp;)와 등호(=) 특수 문자가 사용되는 것과 관련이 있습니다.

<u>재현 단계</u>:

1. 간단한 제품을 장바구니에 추가합니다.
1. 체크아웃으로 이동합니다.
1. 배송 주소를 설정합니다. (배달 주소 예: **이름** = ** *존* ** **성** = ** *사과 및 오렌지, Inc* ** **거리 주소** = *1234 이름 없는 St* **국가** = *US* **시/도** = *Anystate* **시** = *Anytown* **Zip** = *12345* **8}전화** = *1234567890*)
1. 결제를 **PayPal PayflowPro**(으)로 설정하고 체크아웃을 완료해 보십시오.

<u>예상 결과</u>:

트랜잭션으로 인해 예상대로 결제가 성공하거나 올바른 오류 메시지가 표시됩니다.

<u>실제 결과</u>:

거래가 거부되고 &quot;거래가 거부되었습니다.&quot;라는 이메일이 고객에게 전송됩니다.

## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 다음 링크를 사용하십시오.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
