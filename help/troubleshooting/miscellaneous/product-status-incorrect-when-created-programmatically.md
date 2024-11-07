---
title: 프로그래밍 방식으로 만들 때 제품 상태가 올바르지 않음
description: 이 문서에서는 프로그래밍 방식으로 생성/업데이트할 때 제품 상태가 비활성화됨이고 스토어 전면에 제품이 표시되지 않거나 잘못된 스토어 보기에 할당된 경우에 대한 수정 사항을 제공합니다.
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# 프로그래밍 방식으로 만들 때 제품 상태가 올바르지 않음

이 문서에서는 프로그래밍 방식으로 생성/업데이트할 때 제품 상태가 비활성화됨이고 스토어 전면에 제품이 표시되지 않거나 잘못된 스토어 보기에 할당된 경우에 대한 수정 사항을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.X.X
* Adobe Commerce 온-프레미스 2.X.X

## 문제

Adobe Commerce 애플리케이션이 부트스트랩된 스크립트에서 카탈로그 제품이 프로그래밍 방식으로 생성되거나 업데이트되면 제품이 비활성화됨 상태이거나 잘못된 스토어 보기에 할당될 수 있습니다.

## 원인

Adobe Commerce 인스턴스 관리자 역할에 설정된 ACL 제한 사항으로 인해 문제가 나타날 수 있습니다. 부트스트랩된 응용 프로그램의 경우 적절한 ACL 설정이 있는 초기화된 관리 세션이 없습니다. 그러면 이러한 작업에 대한 권한 검사를 담당하는 `Magento_AdminGws` 모듈에서 유효성 검사가 실패합니다.

## 잘못된 제품 상태에 대한 솔루션

개발자 설명서의 [ObjectManager>프로그램 제품 업데이트](https://developer.adobe.com/commerce/php/development/components/object-manager/) 항목에 설명된 대로 `Magento\Framework\Authorization\PolicyInterface`에 대한 동적 DI 환경 설정을 지정합니다.

## 관련 읽기

* [Github: productRepository로 만든 제품의 상태를 변경할 수 없음](https://github.com/magento/magento2/issues/5664)
