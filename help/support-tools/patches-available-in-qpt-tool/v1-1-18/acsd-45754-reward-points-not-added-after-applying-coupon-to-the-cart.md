---
title: 'ACSD-45754: 장바구니에 쿠폰 적용 후 보상 포인트가 추가되지 않음'
description: ACSD-45754 패치는 장바구니에 쿠폰을 적용한 후 보상 포인트가 추가되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-45754입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
exl-id: 957713c0-3e2e-4dc9-8924-2ae84c817e47
feature: Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-45754: 장바구니에 쿠폰을 적용한 후 보상 포인트가 추가되지 않음

ACSD-45754 패치는 장바구니에 쿠폰을 적용한 후 보상 포인트가 추가되지 않는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18이 설치되었습니다. 패치 ID는 ACSD-45754입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.1 - 2.4.5

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

장바구니에 쿠폰 적용 후 보상 포인트는 추가되지 않습니다.

<u>전제 조건</u>:

PayPal 결제 방법이 구성되어 있습니다.

<u>재현 단계</u>:

1. 로 이동하여 보상 포인트 환율 생성 **저장** > **기타 설정** > **보상 환율**.
1. 쿠폰 코드가 있는 장바구니 가격 규칙을 만들어 로그인한 고객에 대해 100개의 보상 포인트를 적용합니다.
1. PayPal과 쿠폰 코드를 사용하여 로그인한 고객으로 제품을 확인하십시오.
1. 관리자의 고객 계정에서 보상 포인트 내역을 확인합니다.

<u>예상 결과</u>:

가격 규칙에 따라 고객에게 보상 포인트가 추가됩니다.

<u>실제 결과</u>:

고객에게 보상 포인트가 추가되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
