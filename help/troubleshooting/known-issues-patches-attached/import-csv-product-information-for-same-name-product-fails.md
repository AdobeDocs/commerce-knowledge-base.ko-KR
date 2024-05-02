---
title: 동일한 이름 제품에 대한 CSV 제품 정보 가져오기가 실패합니다
description: 이 문서에서는 이름이 같은 제품이 있는 경우 제품 정보가 있는 ".csv" 파일을 가져오려고 할 때 오류를 가져오는 것과 관련된 알려진 Adobe Commerce 2.2.3 문제에 대한 패치를 제공합니다.
exl-id: 420b0283-455a-4bd5-ba51-18f341ddacd5
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# 동일한 이름 제품에 대한 CSV 제품 정보 가져오기가 실패합니다

이 문서에서는 가져오기를 시도할 때 오류를 가져오는 것과 관련된 알려진 Adobe Commerce 2.2.3 문제에 대한 패치를 제공합니다. `.csv` 이름이 같은 제품이 있는 경우 제품 정보가 있는 파일입니다.

## 문제

다음과 같은 경우 `.csv` 제품 정보가 있는 파일을 가져오고 동일한 이름의 제품이 있는 경우 데이터 확인 단계에서 다음 오류가 발생합니다. *&quot;`URL Key XYZ was already generated for an item with the SKU %sku%"`*. 이 문제는 가져오는 중에 제품 URL에 대한 열이 없는 경우에도 제품 URL을 다시 작성함으로써 발생합니다 `.csv` 파일.

<u>재현 단계</u>:

1. Commerce 관리자에서 이름이 동일한 구성 가능한 두 제품을 만듭니다.
1. 만들기 `.csv` 이러한 제품에 대한 데이터를 가져올 파일(예: 다음 열) `sku` | `product_type` | `name` | `product_websites` | `store_view_code`
1. 다음으로 이동 **시스템** > **데이터 전송** > **가져오기** 및 선택 `.csv` 파일.
1. 클릭 **데이터 확인**.

<u>예상 결과</u>:

문제를 찾을 수 없음. 다음을 가져올 수 있습니다. `.csv` 파일을 성공적으로 저장했습니다.

<u>실제 결과</u>:

다음과 같은 오류 메시지가 표시됩니다. *&quot;URL 키 XYZ가 SKU %sku%의 항목에 대해 이미 생성되었습니다.&quot;*, 파일을 가져올 수 없습니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-12899\_EE\_2.2.3\_COMPOSER\_v2.patch 다운로드](assets/MDVA-12899_EE_2.2.3_COMPOSER_v2.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* Adobe Commerce 온-프레미스 2.2.3

이 패치는 다음 Adobe Commerce 버전 및 버전과도 호환됩니다(하지만 문제를 해결하지는 못할 수 있음).

* 2.2.0에서 2.2.7, 2.3.0으로 클라우드 인프라의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.2.0 - 2.2.2, 2.2.4 - 2.2.7, 2.3.0

## 패치 적용 방법

다음을 참조하십시오 [Adobe Commerce에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 지침에 대해서는 지원 기술 자료에서 참조하십시오.

## 유용한 링크

[클라우드 인프라의 Adobe Commerce에 사용자 정의 패치 적용](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html)

## 첨부 파일
