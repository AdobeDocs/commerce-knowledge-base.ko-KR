---
title: 소스를 삭제하거나 해당 코드를 변경할 수 없음
description: 이 문서에서는 소스를 완전히 제거하거나 해당 코드를 변경할 수 없는 경우에 대한 수정 사항을 제공합니다.
exl-id: dbdb4d62-9138-4a3d-a58f-8671f1dc5b42
feature: Console
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# 소스를 삭제하거나 해당 코드를 변경할 수 없음

이 문서에서는 소스를 완전히 제거하거나 해당 코드를 변경할 수 없는 경우에 대한 수정 사항을 제공합니다.

## 문제

제품 할당과 관계없이 소스를 삭제할 수 없습니다.

## 영향을 받는 제품 및 버전

* Magento 인벤토리가 설치된 클라우드 인프라(모든 버전)의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.3.0 이상(Magento 인벤토리 설치)
* Magento Open Source Magento 인벤토리가 설치된 2.3.0 이상 버전

## 원인

설계에 의해, 소스를 완전히 제거 및/또는 그 코드를 변경 할 수 없습니다.

출처가 제품 재고, 주문, 선적 데이터 등의 일부이므로 출처를 완전히 제거하면 주문 데이터 문제가 발생합니다.

코드는 소스를 주문에 연결하는 데 필수적입니다. 소스에 대한 고유 ID이며, 편집할 수 없습니다.

## 솔루션

재고를 이전하거나 특정 위치의 모든 납품에서 제품을 드롭하여 제품에서 출처를 제거할 수 있습니다.

[SSA](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/basics/selection-reservations) 계산 및 Adobe Commerce 인벤토리 주문 처리에서 원본을 제거해야 하는 경우 원본을 사용하지 않도록 설정할 수 있습니다. 비활성화된 소스는 모든 데이터, 지정된 제품 및 재고 수량을 유지하고 언제든지 다시 활성화하여 배송을 시작할 수 있습니다.

원본을 사용하지 않도록 설정하는 방법에 대한 자세한 내용은 [원본 만들기 가이드](https://github.com/magento/inventory/wiki/Create-Sources#disable-sources)를 참조하세요.
