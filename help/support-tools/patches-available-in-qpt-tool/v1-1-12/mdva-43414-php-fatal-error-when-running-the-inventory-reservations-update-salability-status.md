---
title: 'MDVA-43414: "inventory.reservations.updateSalabilityStatus" 실행 시 PHP 치명적인 오류 발생'
description: MDVA-43414 패치는 숫자 SKU에서 'inventory.reservations.updateSalabilityStatus' 큐 소비자를 실행할 때 발생하는 PHP 치명적 오류를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43414입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 197c5db1-36bc-41a7-a5ca-f026600da786
feature: Inventory, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# MDVA-43414: &quot;inventory.reservations.updateSalabilityStatus&quot;를 실행할 때 PHP 치명적인 오류 발생

MDVA-43414 패치는 숫자 SKU에서 `inventory.reservations.updateSalabilityStatus` 큐 소비자를 실행할 때 발생하는 PHP 치명적인 오류를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-43414입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.6 - 2.3.7-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

숫자 SKU에서 &quot;inventory.reservations.updateSalabilityStatus&quot; 큐 소비자를 실행할 때 PHP 치명적인 오류가 발생합니다.

<u>필수 구성 요소</u>:

인벤토리 모듈이 설치되었습니다.

<u>재현 단계</u>:

1. 사용자 정의 재고 출처를 생성하고 신규 재고 재고에 지정합니다.
1. 사용자 지정 인벤토리 소스로 제품을 만듭니다.
1. 제품 SKU가 정수 값인지 확인합니다.
1. 주문하십시오.
1. `bin/magento queue:consumer:start inventory.reservations.updateSalabilityStatus` 명령을 실행합니다.

<u>예상 결과</u>:

오류 없이 큐가 시작됩니다.

<u>실제 결과</u>:

PHP 치명적인 오류가 발생합니다:

```PHP
PHP Fatal error:  Uncaught TypeError: Argument 1 passed to Magento\InventoryIndexer\Model\Queue\UpdateIndexSalabilityStatus\IndexProcessor::getIndexSalabilityStatus() must be of the type string, int given, called in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php on line 119 and defined in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php:136
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
