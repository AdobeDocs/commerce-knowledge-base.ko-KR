---
title: 직송 시 잘못된 주소가 선택됨
description: 배송 솔루션은 제품 출처의 주소를 수령하지 않습니다.
exl-id: ce89713f-d506-4e4f-bf49-cdee3e6d29b5
feature: Customer Service, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# 직송 시 잘못된 주소가 선택됨

## 문제

배송 솔루션은 제품 출처의 주소를 수령하지 않습니다.

## 영향을 받는 제품 및 버전

* Magento 인벤토리가 설치된 클라우드 인프라(모든 버전)의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.3.0 이상(Magento 인벤토리 설치)
* Magento Open Source Magento 인벤토리가 설치된 2.3.0 이상 버전

### 원인

Magento 인벤토리는 현재 체크아웃 중 소스 주소를 기반으로 한 직송 요금 계산을 지원하지 않습니다. 대신 구성의 기본 저장소 주소가 모든 경우에 사용됩니다.

## 관련 읽기

* GitHub의 [Magento 인벤토리 FAQ](https://github.com/magento/inventory/wiki/MSI-FAQs).
