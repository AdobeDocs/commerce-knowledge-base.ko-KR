---
title: 'MDVA-31006: Paypal 중복 주문 10415 오류'
description: MDVA-31006 패치는 PayPal Express 체크아웃 결제를 사용하면 10415 오류가 발생하여 중복 주문이 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6이 설치된 경우 사용할 수 있습니다. Adobe Commerce 2.4.2에서 문제가 해결되었습니다.
exl-id: ff471fd3-f580-4149-83bc-67f6fce8e28d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# MDVA-31006: Paypal 중복 주문 10415 오류

MDVA-31006 패치는 PayPal Express 체크아웃 결제를 사용하면 10415 오류가 발생하여 중복 주문이 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6이 설치된 경우에 사용할 수 있습니다. Adobe Commerce 2.4.2에서 문제가 해결되었습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 방법) 2.3.2 - 2.4.0

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자가 Adobe Commerce 주문 성공 페이지로 전송되지 않으므로 빈 페이지를 새로 고치고 두 번째 주문이 배치되므로 중복 주문이 발생합니다.

<u>필수 구성 요소</u>:

* Adobe Commerce이 설치되었습니다.
* PayPal Express 체크아웃 결제가 구성되었습니다.
* Commerce 관리자에 로그인합니다. **스토어** > **구성** > **판매** > **결제 방법** > 선택 **Paypal Express 체크아웃** > **구성** > **고급 설정** > **주문 검토 단계 건너뛰기** > *아니요*.

<u>재현 단계</u>:

1. 사용자로 로그인
1. 항목을 선택하고 **장바구니에 추가**&#x200B;를 클릭합니다.
1. 장바구니를 클릭하고 **체크아웃으로 진행**&#x200B;을 클릭합니다.
1. PayPal Express 창으로 이동하여 결제하세요.
1. Adobe Commerce 주문 검토 페이지로 리디렉션됩니다.
1. **주문** 단추를 누릅니다.
1. 서버 인프라 문제로 인해 시스템 오류를 에뮬레이션합니다. 사용자에게 빈 페이지가 표시됩니다.
1. 페이지를 새로 고칩니다.

<u>예상 결과</u>:

* 고객이 주문 검토 페이지로 리디렉션되고 오류 메시지 &quot;*성공적인 결제 거래가 이미 완료되었습니다. 주문이 완료되었는지 확인하십시오.*&quot;
* `/var/log/payment.log`에 있는 payment.log에 오류가 10415 주문만 생성되었습니다.

<u>실제 결과</u>:

* 고객이 Adobe Commerce 주문 성공 페이지로 전송되지 않으면 빈 페이지가 새로 고쳐지고 두 번째 주문이 추가되므로 두 개의 중복 주문이 생성됩니다.
* `/var/log/payment.log`에 있는 payment.log에 오류가 10415.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
