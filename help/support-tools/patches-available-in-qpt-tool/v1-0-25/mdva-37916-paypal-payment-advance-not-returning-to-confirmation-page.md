---
title: 'MDVA-37916: PayPal 결제 고급이 확인 페이지로 돌아가지 않음'
description: Adobe Commerce용 MDVA 37916 품질 패치는 PayPal 결제 Advanced가 결제 후 확인 페이지로 돌아가지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37916입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 18d7bb1c-d73a-43f6-90a8-650290dfd114
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# MDVA-37916: PayPal 결제 고급이 확인 페이지로 돌아가지 않음

Adobe Commerce용 MDVA 37916 품질 패치는 PayPal 결제 Advanced가 결제 후 확인 페이지로 돌아가지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37916입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
클라우드 인프라의 Adobe Commerce 2.3.6-p1

**Adobe Commerce 버전과 호환:**
Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.6-2.4.2-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

PayPal 결제 고급 방법을 사용할 때는 결제 후 결제 확인 페이지로 이동하지 않습니다.

<u>재현 단계</u>: [Screencast](https://assets.adobe.com/public/025d479b-5796-4772-6f3d-adc86306a799)

1. 장바구니에 제품을 추가하고 체크아웃 페이지의 결제 단계로 이동합니다.
1. **신용 카드(Payflow Advanced)** 결제 옵션을 선택하십시오.
1. **계속**&#x200B;을 클릭하여 결제 양식이 포함된 iframe을 표시합니다.
1. 샌드박스 신용카드 세부 정보로 결제 양식을 작성하십시오.
   * 카드 번호: 4444 333 222 1111 또는 41111 111 111 1111
   * 만료 날짜: 2023년 12월
   * CSC: 123
1. **지금 결제**&#x200B;를 클릭합니다.

<u>예상 결과</u>:

결제가 처리되고 결제가 성공하면 주문 확인 페이지로 리디렉션됩니다.

<u>실제 결과</u>:

* 주문 확인 페이지로 리디렉션되지 않았습니다.
* 하지만 Adobe Commerce에서 주문이 생성되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html)

## 관련 읽기

지원 기술 자료의 품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 지원 기술 자료에서 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
