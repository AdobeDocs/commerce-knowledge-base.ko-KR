---
title: DHL을 배송 운송업체로 계속 제공하기 위해 패치 적용
description: 이 문서에서는 2022년 7월 말부터 9월까지 DHL 스키마 6.0이 더 이상 사용되지 않은 후 Adobe Commerce 2.4.4 이하 버전을 사용하는 상인이 DHL 배송을 계속 제공할 수 있는 패치를 제공합니다.
exl-id: 4350e83a-495b-41b4-a526-dae5923e9d41
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# DHL을 배송 운송업체로 계속 제공하기 위해 패치 적용


## 영향을 받는 제품 및 버전

* Adobe Commerce 2.4.4 이하 버전에서는 모든 배포 메서드를 사용할 수 있습니다.

## 문제

DHL은 6.2 스키마 버전을 도입하고 2022년 7월 말부터 9월까지 6.0을 더 이상 사용하지 않습니다. Adobe Commerce 2.4.4 및 이전 버전의 DHL 통합은 버전 6.0만 지원합니다.

## 솔루션

2022년 8월 릴리스로 예정된 Adobe Commerce 2.4.5에는 버전 6.2 스키마를 사용하는 DHL과의 업그레이드된 통합이 포함됩니다. 새 버전이 출시될 때까지(또는 업그레이드하지 않기로 선택한 경우) 버전 6.2 DHL 스키마 지원을 구현하는 AC-3022 패치를 적용하여 사용 중단 후에도 스토어에서 DHL 배송을 계속 제공할 것을 권장합니다.

## 패치

패치 ID는 품질 패치 도구 버전 1.1.16에서 사용할 수 있는 AC-3022입니다.
QPT 사용 및 패치 설치 방법에 대한 자세한 내용은 개발자 설명서에서 [품질 패치 도구(QPT) > 사용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) 문서를 참조하십시오.

이 패치는 다음 Adobe Commerce 버전에 적용할 수 있습니다.

* 2.4.0 - 2.4.4-p1
* 2.3.7

## 관련 읽기

* 사용 안내서의 [운송업체 > DHL](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl)
* 사용 안내서의 [배달 방법](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/delivery-methods)
