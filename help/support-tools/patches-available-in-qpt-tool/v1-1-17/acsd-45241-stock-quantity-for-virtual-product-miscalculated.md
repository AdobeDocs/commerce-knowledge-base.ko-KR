---
title: "ACSD-45241: 가상 제품의 재고 수량이 잘못 계산됨"
description: ACSD-45241 패치는 대변 메모를 작성한 후 가상 제품의 재고 수량이 잘못 계산되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-45241입니다. 이 문제는 Adobe Commerce 2.4.4에서 해결되었습니다.
exl-id: 4be97da9-d399-419a-816e-cf65f15cc3be
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# ACSD-45241: 가상 제품의 재고 수량이 잘못 계산됨

ACSD-45241 패치는 대변 메모를 작성한 후 가상 제품의 재고 수량이 잘못 계산되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17이 설치되었습니다. 패치 ID는 ACSD-45241입니다. 이 문제는 Adobe Commerce 2.4.4에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.5 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

대변 메모를 만든 후 가상 제품에 대한 재고 수량이 잘못 계산되었습니다.

<u>재현 단계</u>:

1. Commerce 관리자에서 가상 제품을 하위 제품으로 사용하여 구성 가능한 제품을 만듭니다.
1. 1단계에서 만든 두 제품이 모두 재고에 있는지 확인합니다.
1. 1단계에서 생성된 가상 제품의 수량을 100으로 표시하고 판매 가능한 수량도 100으로 유지합니다.
1. 장바구니에 제품을 추가합니다.
1. 1단계에서 생성한 가상 제품으로 주문합니다.
1. 주문 상태를 &quot;보류 중&quot;으로 유지합니다. 결제를 진행할 필요가 없습니다.
1. `order_created` 레코드 생성일 `inventory_reservation`. 가상 제품 수량은 100이며 판매 가능 수량은 99입니다.
1. 주문을 열고 다음으로 이동 **인보이스** > **송장 제출**.
1. `invoice_created` 레코드 생성일 `inventory_reservation`. 현재 가상 제품 수량은 99개이며, 판매 가능 수량도 99개입니다.
1. 선택하지 않고 대변 메모 만들기 **재고로 돌아가기**.

<u>예상 결과</u>:

새 레코드가에 만들어지지 않음 `inventory_reservation`및 가상 제품에 대한 재고 수량은 변경되지 않습니다.

<u>실제 결과</u>:

A `creditmemo_created` 레코드가에 생성됨 `inventory_reservation`, 가상 제품 재고 수량은 98로 조정되며 판매 가능 수량은 99입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
