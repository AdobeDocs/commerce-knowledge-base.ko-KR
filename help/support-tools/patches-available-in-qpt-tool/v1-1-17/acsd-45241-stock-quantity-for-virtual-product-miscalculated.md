---
title: "ACSD-45241: 가상 제품의 재고 수량이 잘못 계산됨"
description: ACSD-45241 패치는 대변 메모를 작성한 후 가상 제품의 재고 수량이 잘못 계산되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-45241입니다. 이 문제는 Adobe Commerce 2.4.4에서 해결되었습니다.
exl-id: 4be97da9-d399-419a-816e-cf65f15cc3be
feature: Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# ACSD-45241: 가상 제품의 재고 수량이 잘못 계산됨

ACSD-45241 패치는 대변 메모를 작성한 후 가상 제품의 재고 수량이 잘못 계산되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-45241입니다. 이 문제는 Adobe Commerce 2.4.4에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.5 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

대변 메모를 만든 후 가상 제품에 대한 재고 수량이 잘못 계산되었습니다.

<u>재현 단계</u>:

1. Commerce 관리자에서 가상 제품을 하위 제품으로 사용하여 구성 가능한 제품을 만듭니다.
1. 1단계에서 만든 두 제품이 모두 재고에 있는지 확인합니다.
1. 1단계에서 생성된 가상 제품의 수량을 100으로 표시하고 판매 가능한 수량도 100으로 유지합니다.
1. 장바구니에 제품을 추가합니다.
1. 1단계에서 생성한 가상 제품으로 주문합니다.
1. 주문 상태를 &quot;보류 중&quot;으로 유지합니다. 결제를 진행할 필요가 없습니다.
1. `inventory_reservation`에서 `order_created` 레코드를 만들었습니다. 가상 제품 수량은 100이며 판매 가능 수량은 99입니다.
1. 주문을 열고 **청구서** > **청구서 제출**(으)로 이동합니다.
1. `inventory_reservation`에서 `invoice_created` 레코드를 만들었습니다. 현재 가상 제품 수량은 99개이며, 판매 가능 수량도 99개입니다.
1. **주식으로의 반환**&#x200B;을 선택하지 않고 대변 메모를 만듭니다.

<u>예상 결과</u>:

`inventory_reservation`에 새 레코드가 만들어지지 않으며 가상 제품에 대한 재고 수량이 변경되지 않습니다.

<u>실제 결과</u>:

`inventory_reservation`에 `creditmemo_created` 레코드가 만들어지고 가상 제품 재고 수량은 98로 조정되며 판매 가능 수량은 99입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
