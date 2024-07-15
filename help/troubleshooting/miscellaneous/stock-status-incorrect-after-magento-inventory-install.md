---
title: Inventory management 설치 후 재고 상태가 잘못됨
description: 이 문서에서는 Inventory management 설치/업그레이드 후 재고 상태가 잘못된 경우에 대한 수정 사항을 제공합니다.
exl-id: ae32fbe3-deab-4f31-b427-95f8b54a476f
feature: Install, Inventory, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Inventory management 설치 후 재고 상태가 잘못됨

이 문서에서는 Inventory management 설치/업그레이드 후 재고 상태가 잘못된 경우에 대한 수정 사항을 제공합니다.

## 일부 사이트의 재고 상태가 잘못됨

다중 웹 사이트 Adobe Commerce 환경에서 Inventory management을 갖도록 처음 설치하거나 업그레이드한 후 일부 웹 사이트에서는 제품에 대한 올바른 재고 상태가 아닙니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce on cloud infrastructure, 모든 버전, Inventory management 설치
* Adobe Commerce 온-프레미스 2.3.0 이상(Inventory management 설치 시)
* Inventory management이 설치된 2.3.0 이상 Magento Open Source

## 원인

처음 설치/업그레이드할 때 모든 제품은 기본 출처에 지정되며 모든 수량을 해당 출처에 연관시킵니다. 기본 Source은 기본 웹 사이트가 연결된 기본 스톡에 할당됩니다.

## 솔루션

웹 사이트가 두 개 이상 있는 경우 이러한 웹 사이트를 Default Stock 또는 기타 사용자 지정 스톡에 Sales Channel으로 추가해야 합니다.

이 작업을 수행하는 방법에 대한 자세한 내용은 사용 안내서의 [위키/사용 안내서의 재고 섹션](https://docs.magento.com/m2/ce/user_guide/catalog/inventory-stock.html)을 참조하십시오.
