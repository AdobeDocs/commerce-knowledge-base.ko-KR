---
title: 'Adobe Commerce 2.4.0: B2B 1.2.0 설치 중 예외 발생'
description: 이 문서에서는 B2B 1.2.0을 설치할 때 'setup:upgrade' 도중 발생한 예외에 대한 Adobe Commerce 알려진 문제 해결 방법을 제공합니다.
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: B2B 1.2.0 설치 중 예외

이 문서에서는 다음 기간 동안 throw된 예외에 대해 알려진 Adobe Commerce 문제에 대한 수정 사항을 제공합니다. `setup:upgrade` B2B 1.2.0 설치 시

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.0
* 클라우드 인프라의 Adobe Commerce 2.4.0
* B2B 1.2.0

## 문제

<u>재현 단계</u>

1. 스토어를 두 개 이상 생성하여 Adobe Commerce을 설치합니다.
1. 추가 스토어를 만듭니다.
1. B2B 1.2.0을 설치합니다.

>[!WARNING]
>
>버전 1.2.0 이하 또는 Commerce 인스턴스 2.4.0 이하에서 저장소가 1개 이상인 B2B 인스턴스의 업그레이드도 영향을 받습니다.

<u>예상 결과</u>

B2B 1.2.0 설치

<u>실제 결과</u>

날짜 `setup:upgrade` 를 실행하여 B2B 1.2.0을 설치합니다. 이 오류는 `PurchaseOrder` 모듈:

```php
Module 'Magento_PurchaseOrder':
  Unable to apply data patch Magento\PurchaseOrder\Setup\Patch\Data\InitPurchaseOrderSalesSequence
  for module Magento_PurchaseOrder. Original exception message: DDL statements
  are not allowed in transactions
```

## 솔루션

이 문서에 제공된 패치를 적용합니다.

## 패치

이 문서에 첨부된 패치는 다음 두 위치에서 다운로드할 수 있습니다. `.composer` 및 `.git` 형식(파일의 압축을 푼 후).

다운로드하려면 문서 끝까지 아래로 스크롤하여 파일 이름을 클릭하거나 다음 링크 중 하나를 클릭합니다.

* [작성기 패치 B2B-716\_composer.patch](assets/B2B-716_composer.patch.zip)
* [Git 패치 B2B-716\_git.patch](assets/B2B-716_git.patch.zip)

## 패치 적용 방법

<u>작성기 패치 </u>

다음을 참조하십시오 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 작성기 패치 지침용

<u>Git 패치 </u>

* 다음을 참조하십시오 [패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 클라우드 인프라의 Adobe Commerce에 대한 git 패치 지침에 대해서는 개발자 설명서에서 참조하십시오.
* 다음을 참조하십시오 [패치 적용: 사용자 정의 패치](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#custom-patches) Adobe Commerce용 git 패치 지침에 대해서는 개발자 설명서 를 참조하십시오.

## 관련 읽기

* [Adobe Commerce 2.4.0 알려진 문제: storefront에 원시 메시지 데이터 표시](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 알려진 문제: 수출 세율이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: Braintree 결제 방법이 여러 주소 체크아웃에 표시되지 않음](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0 알려진 문제: 체크아웃 중에 일부 국가에 대해 표시되는 로컬 결제 방법을 선택하는 동안 오류 메시지](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 알려진 문제: 다중 배송 체크아웃에서 보상 포인트를 제거할 때 404 오류 발생](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0 알려진 문제: 주문 표시 오류](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B 관리자가 구성 가능한 제품을 견적에 추가할 수 없음](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0의 배송 라벨 작성 알려진 문제](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Adobe Commerce 2.4.0 알려진 문제 - 고객 활동 새로 고침이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 알려진 문제: &quot;내 장바구니에 선택 항목 추가&quot; 버튼이 작동하지 않음](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
