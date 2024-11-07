---
title: Adobe Commerce 버전 2.3.4-p1 또는 2.3.5로 업그레이드하는 동안 위시리스트 오류 발생
description: 이 문서에서는 이러한 버전으로 업그레이드하는 동안의 위시리스트 오류와 관련된 Adobe Commerce 버전 2.3.4-p1 및 2.3.5로 업그레이드할 때 발생하는 알려진 문제에 대한 수정 사항을 제공합니다.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Adobe Commerce 버전 2.3.4-p1 또는 2.3.5로 업그레이드하는 동안 위시리스트 오류 발생

이 문서에서는 이러한 버전으로 업그레이드하는 동안의 위시리스트 오류와 관련된 Adobe Commerce 버전 2.3.4-p1 및 2.3.5로 업그레이드할 때 발생하는 알려진 문제에 대한 수정 사항을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라 2.3.4-p1 및 2.3.5의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.3.4-p1 및 2.3.5

## 문제

Adobe Commerce(모든 배포 방법) 및 Magento Open Source을 버전 2.3.5 또는 2.3.4-p1로 업그레이드할 때 모듈에서 위시리스트 오류(아래에 자세히 설명)가 표시될 수 있습니다.

```php
Magento_Wishlist
```

Adobe Commerce(모든 배포 방법)/Magneto Open Source 버전 2.3.4-p1 **에서 버전 2.3.4-p2** 또는 Adobe Commerce(모든 배포 방법)/Magneto Open Source 버전 2.3.5 **에서 버전 2.3.5-p1**(으)로 업그레이드하면 오류가 해결됩니다.

<u>재현 단계</u>:

Adobe Commerce(모든 배포 방법)/Magento Open Source을 버전 2.3.4-p1 또는 2.3.5로 업그레이드하십시오.

<u>예상 결과</u>:

Adobe Commerce(모든 배포 방법)/Magento Open Source 버전 2.3.4-p1 또는 2.3.5로의 업그레이드 프로세스가 정상적으로 완료됩니다.

<u>실제 결과</u>:

업그레이드 중에 다음 오류가 발생합니다.

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## 솔루션

* Adobe Commerce(모든 배포 방법)/Magneto Open Source 버전 2.3.5로 업그레이드하는 경우 **버전 2.3.5-p1로 업그레이드하십시오**. Adobe Commerce(모든 배포 방법)/Magento Open Source 버전 2.3.5-p1은 2.3.5를 대체합니다.
* Adobe Commerce(모든 배포 방법)/Magento Open Source 버전 2.3.4-p1로 업그레이드하는 경우 **버전 2.3.4-p2로 업그레이드**&#x200B;하십시오. Adobe Commerce(모든 배포 방법)/Magneto Open Source 버전 2.3.4-p2는 버전 2.3.4-p1을 대체합니다.

## 관련 읽기

개발자 설명서에서:

* [클라우드 인프라의 Adobe Commerce 안내서](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview)
* [클라우드 인프라의 Adobe Commerce - Adobe Commerce 버전 업그레이드](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)
* [Adobe Commerce 온-프레미스 및 Magento Open Source - Adobe Commerce 응용 프로그램 및 모듈 업그레이드](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/overview)
* [위시리스트 항목 구성 페이지](https://developer.adobe.com/commerce/frontend-core/guide/layouts/product-layouts/#wishlist-item-configure-page)
* [고급 보고를 제공하는 모듈](https://developer.adobe.com/commerce/php/development/advanced-reporting/modules/)
