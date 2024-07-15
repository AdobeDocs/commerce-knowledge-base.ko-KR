---
title: 2.4.4에서 2.4.4-p1로 업그레이드한 후 패키지 다운그레이드됨
description: 이 문서에서는 버전 2.4.4의 판매자가 '작성기 업데이트' 명령을 실행한 다음 아래에 나열된 패키지(모듈)가 버전 2.4.4와 호환되지 않으며 버전 2.4.5 이상에서만 사용해야 하는 이전 버전으로 다운그레이드되는 문제에 대한 핫픽스를 제공합니다.
exl-id: 4ebdbcd7-6905-4647-b071-1e4413455f38
feature: Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# 2.4.4에서 2.4.4-p1로 업그레이드한 후 패키지 다운그레이드됨

이 문서에서는 버전 2.4.4의 판매자가 `composer update` 명령을 실행한 다음 아래에 나열된 패키지(모듈)가 버전 2.4.4와 호환되지 않으며 버전 2.4.5 이상에서만 사용하도록 되어 있는 이전 버전으로 다운그레이드되는 경우 발생하는 문제에 대한 핫픽스를 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.4.4
* Adobe Commerce 온-프레미스 2.4.4
* Magento Open Source 2.4.4

## 문제

이 문제가 발생하는 방법과 재현 방법에는 두 가지 시나리오가 있습니다.

### 시나리오 1

<u>재현 단계</u>:

2.4.4에서 2.4.4-p1로 업그레이드할 때 비슷한 출력으로 다운그레이드되는 패키지(모듈)는 여러 개입니다.

```text
Downgrading magento/module-adobe-ims (2.1.4 => 2.1.3)
Downgrading magento/module-adobe-ims-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-admin-ui (1.3.2 => 1.3.1)
Downgrading magento/module-adobe-stock-client-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-image (1.3.3 => 1.3.2)
Downgrading magento/module-adobe-stock-image-admin-ui (1.3.3 => 1.3.2)
Downgrading magento/module-banner-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-inventory (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-advanced-checkout (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-api (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-bundle-product (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-catalog-api (1.3.3 => 1.3.2)
Downgrading magento/module-inventory-configurable-product-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-configurable-product-frontend-ui (1.0.3 => 1.0.2)
Downgrading magento/module-inventory-import-export (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-in-store-pickup-admin-ui (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-frontend (1.1.3 => 1.1.2)
Downgrading magento/module-inventory-in-store-pickup-graph-ql (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-sales-admin-ui (1.1.3 => 1.1.2-p1)
Downgrading magento/module-inventory-in-store-pickup-shipping (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-low-quantity-notification (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-low-quantity-notification-api (1.2.2 => 1.2.1-p1)
Downgrading magento/module-inventory-requisition-list (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-admin-ui (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-api (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-shipping-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-source-selection-api (1.4.2 => 1.4.1-p1)
Downgrading magento/module-inventory-wishlist (1.0.2 => 1.0.1)
Downgrading magento/module-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-re-captcha-checkout-sales-rule (1.1.1 => 1.1.0)
Downgrading magento/module-re-captcha-customer (1.1.3 => 1.1.2)
Downgrading magento/module-re-captcha-frontend-ui (1.1.3 => 1.1.2)
Downgrading magento/module-staging-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-two-factor-auth (1.1.4 => 1.1.3)
Removing magento/module-admin-adobe-ims (100.4.0)
```

<u>예상 결과</u>:

버전 2.4.4에서 2.4.4-p1로 업그레이드하면 버전 2.4.4-p1에 대한 올바른 패키지(모듈)가 생성됩니다.

<u>실제 결과</u>:

버전 2.4.4에서 2.4.4-p1로 업그레이드하는 동안 이러한 패키지(모듈의) 버전은 다운그레이드되지만 이러한 메시지는 무시할 수 있으며 기능에 영향을 주지 않습니다.

### 시나리오 2

<u>재현 단계</u>:

2.4.4 판매자가 `composer update` 명령을 실행하면 **시나리오 1**&#x200B;에서 위에 나열된 동일한 패키지(모듈)가 버전 2.4.5와만 호환되고 버전 2.4.4와 함께 사용해서는 안 되는 최신 버전으로 업그레이드됩니다.

<u>예상 결과</u>:

버전 2.4.4에서 2.4.4-p1로 업그레이드하면 버전 2.4.4-p1에 대한 올바른 패키지(모듈)가 생성됩니다.

<u>실제 결과</u>:

패키지(모듈)는 버전 2.4.4에서 2.4.4-p1로 업그레이드한 후 다운그레이드됩니다.

## 해결 방법 1: 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다. [다운로드 ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip)

## 호환 가능한 Adobe Commerce 및 Magento Open Source 버전:

다음에 대한 패치를 만들었습니다.

* 클라우드 인프라의 Adobe Commerce 2.4.4
* Adobe Commerce 온-프레미스 2.4.4
* Magento Open Source 2.4.4

>[!NOTE]
>
>이 패치는 다른 Adobe Commerce 및 Magento Open Source 버전 및 버전과 호환되지 않습니다.

## 패치 적용 방법

이 문제에 대한 해결 방법으로 첨부된 Bash 스크립트 [ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip)을(를) 사용하십시오.

**스크립트 사용 방법에 대한 정확한 지침:**

### 클라우드 인프라의 Adobe Commerce:

1. 클라우드 코드베이스의 로컬 체크 아웃에 bash 스크립트 파일 `ACPLTSRV-2017-fix.sh`을(를) 다운로드합니다.
1. 작성기 파일을 로컬로 수정하려면 기본 스크립트 파일 `ACPLTSRV-2017-fix.sh`을(를) 실행하십시오.
1. 수정된 작성기 파일을 git 저장소에 추가하고 커밋합니다.

### Adobe Commerce 또는 Magento Open Source 온-프레미스:

1. Adobe Commerce/Magento Open Source 2.4.4 설치의 `root` 폴더(`composer.json`과(와) 동일한 폴더)에 bash 스크립트 `ACPLTSRV-2017-fix.sh`을(를) 배치합니다.
1. `apply` 인수로 bash 스크립트를 실행하여 영향을 받는 패키지(모듈)를 해당 2.4.4 버전에 잠급니다.

   ```bash
   sh ACPLTSRV-2017-fix.sh apply
   ```

1. Run composer가 잠긴 패키지(모듈)를 설치하도록 업데이트되었습니다.
1. 2.4.5 또는 2.4.4-p1로 업그레이드할 준비가 되면 `rollback` 인수를 사용하여 스크립트를 실행합니다.

   ```bash
   sh ACPLTSRV-2017-fix.sh rollback
   ```

   이 단계를 건너뛰면 패키지(모듈) 요구 사항이 충돌하여 업그레이드 오류가 발생합니다.
1. 위의 단계를 완료한 후 업그레이드를 시작할 수 있습니다.

## 해결 방법 2

이 문제에 대한 두 번째 해결 방법은 인수 없이 `composer update` 명령을 실행하지 않는 것입니다.
