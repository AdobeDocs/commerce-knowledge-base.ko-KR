---
title: 가져오기로 번들 옵션 순서가 업데이트되지 않음
description: 이 문서에서는 .csv 파일에서 제품을 가져온 후 번들 제품 옵션이 가져오기 파일에 나열된 순서와 다른 순서로 표시되는 문제에 대한 해결 방법을 제공합니다.
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# 가져오기로 번들 옵션 순서가 업데이트되지 않음

이 문서에서는 .csv 파일에서 제품을 가져온 후 번들 제품 옵션이 가져오기 파일에 나열된 순서와 다른 순서로 표시되는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.2.x, 2.3.x
* Adobe Commerce 온-프레미스 2.2.x, 2.3.x
* Magento Open Source

## 문제

<u>필수 구성 요소</u>:

번들 제품이 포함된 유효한 .csv 파일이 있습니다.

<u>재현 단계</u>:

1. [가져오기 기능](https://docs.magento.com/m2/ee/user_guide/system/data-import.html)을 사용하여 파일을 가져옵니다.
1. 번들 제품 페이지를 엽니다.

<u>예상 결과</u>:

옵션 순서는 .csv 파일과 동일합니다.

<u>실제 결과</u>:

옵션 순서는 .csv 파일의 순서와 다릅니다.

## 원인

옵션 위치가 명시적으로 선언되지 않았습니다.

## 솔루션

1. .csv 파일에서 `bundle_values` 열의 `position` 매개 변수에 있는 각 옵션에 대해 명시적으로 위치를 선언합니다. 자세한 지침은 사용 안내서의 [제품 데이터 편집](https://docs.magento.com/m2/ee/user_guide/system/data-transfer-bundle-products.html#method-2-edit-the-product-data)을 참조하세요.
1. 가져오기 작업을 반복합니다.

가져오기에 대한 일반적인 정보는 사용 안내서에서 [번들 제품 가져오기](https://docs.magento.com/m2/ee/user_guide/system/data-transfer-bundle-products.html)를 참조하십시오.
