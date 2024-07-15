---
title: 제품 Recommendations이 페이지 빌더에 표시되지 않음
description: 이 문서에서는 제품 Recommendations 옵션이 페이지 빌더에 표시되지 않는 문제에 대한 해결 방법을 제공합니다.
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# 제품 Recommendations이 페이지 빌더에 표시되지 않음

이 문서에서는 제품 Recommendations 옵션이 페이지 빌더에 표시되지 않는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 메서드)

## 문제

제품 Recommendations 옵션이 페이지 빌더에 표시되지 않습니다.

## 원인

페이지 빌더에는 제품 Recommendations을 추가하는 옵션이 없습니다. Product Recommendations for Page Builder는 선택적 모듈이며 별도로 설치됩니다.

## 솔루션

1. `composer show magento/module-page-builder-product-recommendations` 명령을 실행하여 모듈을 별도로 설치했는지 확인하십시오.
1. 다음 메시지를 반환하는 경우: *Package magento/module-page-builder-product-recommendations를 찾을 수 없습니다*. `composer require magento/module-page-builder-product-recommendations` 명령을 실행하여 설치해야 합니다.

페이지 빌더에서 제품 Recommendations을 활성화하면 페이지 빌더에서 만든 콘텐츠에 [추천 단위를 추가](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)할 수 있습니다.

## 관련 읽기

* 사용 안내서에서 [콘텐츠 추가 - 제품 Recommendations](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html).
* 개발자 설명서에서 [제품 Recommendations 설치 및 구성](https://devdocs.magento.com/recommendations/install-configure.html).
* [Adobe Commerce 사용 안내서](https://docs.magento.com/user-guide/)
