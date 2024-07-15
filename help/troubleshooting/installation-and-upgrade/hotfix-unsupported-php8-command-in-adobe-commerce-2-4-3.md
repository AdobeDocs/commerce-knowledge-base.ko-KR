---
title: Adobe Commerce 업그레이드 2.4.3, 2.3.7-p1 PHP 치명적인 오류 핫픽스
description: '이 문서에서는 판매자가 Adobe Commerce(모든 배포 방법) 또는 Magento Open Source 2.4.3 또는 2.3.7-p1로 업그레이드하려고 하면 다음 오류가 표시되는 경우에 대한 수정 사항을 제공합니다.'
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Adobe Commerce 업그레이드 2.4.3, 2.3.7-p1 PHP 치명적인 오류 핫픽스

이 문서에서는 판매자가 Adobe Commerce(모든 배포 방법) 또는 Magento Open Source 2.4.3 또는 2.3.7-p1로 업그레이드하려고 하면 다음 오류가 표시되는 경우에 대한 수정 사항을 제공합니다.

*PHP 오류: 알 수 없는 오류: &lt;..>/magento/vendor/magento/framework/Filesystem/Directory/DenyListPathValidator.php:74*&#x200B;에서 정의되지 않은 함수 Magento\Framework\Filesystem\Directory\str_contains()을 호출합니다.

이 문제는 2.4.4, 2.4.3-p1 및 2.3.7-p2 릴리스의 범위에서 수정됩니다.

## 영향을 받는 버전 및 제품

* 2.3.7-p1 또는 2.4.3으로 업그레이드할 때의 Adobe Commerce(모든 배포 방법)
* 2.3.7-p1 또는 2.4.3으로 업그레이드 시 Magento Open Source

## 문제

이 문제는 PHP 8 전용 함수 `str_contains`을(를) 사용하는 새로운 Adobe Commerce 2.4.3 및 2.3.7-p1 버전으로 인해 발생합니다. Adobe Commerce 2.4.3 및 2.3.7-p1은 PHP 7.4와만 호환되므로 이 함수를 사용할 수 없습니다.

<u>재현 단계</u>:

Adobe Commerce 2.4.3 또는 2.3.7-p1로 업그레이드해 보십시오.

<u>예상 결과:</u>

성공적으로 업그레이드했습니다.

<u>실제 결과:</u>

PHP 치명적인 오류.

## 솔루션

해결 방법으로 CLI/터미널에서 Magento 루트 폴더에서 `composer require symfony/polyfill-php80` 명령을 실행하거나 작성기 패치를 설치합니다.

2.4.3에 대한 문제를 해결하려면 Adobe Commerce(모든 배포 방법) 및 Magento Open Source 판매자가 패치를 적용해야 합니다.

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

2.3.7-p1의 문제를 해결하려면 Adobe Commerce(모든 배포 방법) 및 Magento Open Source 판매자가 패치를 적용해야 합니다.

[AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## 패치 적용 방법

지침은 [Magento에서 제공한 작성기 패치 적용 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 관련 읽기

GitHub [Magento 2.4.3 EE #33680](https://github.com/magento/magento2/issues/33680)에서 지원되지 않는 PHP 8 명령
