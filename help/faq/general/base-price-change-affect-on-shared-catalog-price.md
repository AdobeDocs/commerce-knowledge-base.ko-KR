---
title: 기본 가격 변경이 공유된 카탈로그 가격에 영향을 미침
description: '이 문서는 공유 카탈로그의 제품에 사용자 지정 가격이 있고 제품의 기본 가격이 변경되는 경우(예: 예정된 업데이트 후) 공유 카탈로그에 적용되는 가격에 대해 설명합니다.'
exl-id: 916678c1-ada6-4f23-af16-b107cb83ff16
feature: Catalog Management
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# 기본 가격 변경이 공유된 카탈로그 가격에 영향을 미침

이 문서는 공유 카탈로그의 제품에 사용자 지정 가격이 있고 제품의 기본 가격이 변경되는 경우(예: 예정된 업데이트 후) 공유 카탈로그에 적용되는 가격에 대해 설명합니다.

## 사용자 지정 가격이 백분율로 설정되면 공유 카탈로그 가격도 변경됩니다

공유 카탈로그의 제품에 대한 사용자 지정 가격을 백분율로 설정한 경우 기본 가격을 변경하면 제품의 공유 카탈로그 가격이 암시적으로 업데이트됩니다.

즉, 기본 가격이 업데이트되면(일반 또는 예약된 업데이트를 통해) 공유 카탈로그 가격도 퍼센트 할인을 적용한 후 변경됩니다.

## 사용자 지정 가격을 고정으로 설정하면 공유 카탈로그 가격이 변경되지 않습니다

공유 카탈로그의 제품에 대한 사용자 지정 가격이 고정으로 설정된 경우 기본 가격을 업데이트하는 방법(예약된 업데이트, Adobe Commerce 관리, API 또는 가져오기를 통해)에 관계없이 공유 카탈로그의 가격은 변경되지 않습니다.

## Storefront는 항상 가장 낮은 가격을 표시합니다.

제품의 기준 가격이 변경되어 해당 공유된 카탈로그 가격보다 저렴해지면 스토어프론트는 기준 가격을 시스템에서 사용할 수 있는 최저 가격으로 표시합니다.

## 관련 읽기

사용 안내서에서 [공유 카탈로그의 가격 및 구조 설정](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/define/catalog-shared-pricing-structure.html?lang=ko).
