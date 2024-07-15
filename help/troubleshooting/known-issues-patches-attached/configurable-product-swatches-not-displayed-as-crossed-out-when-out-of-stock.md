---
title: 구성 가능한 제품 견본은 재고가 없을 때 제외되어 표시되지 않음
description: 이 문서에서는 구성 가능한 제품 견본이 상점 첫 눈에 볼 수 없을 정도로 품절되는 것과 관련된 알려진 Adobe Commerce 2.2.2 문제에 대한 패치를 제공합니다.
exl-id: 79c59a3f-a94b-4726-8af1-5fe754ea95a5
feature: Configuration, Orders, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# 구성 가능한 제품 견본은 재고가 없을 때 제외되어 표시되지 않음

이 문서에서는 구성 가능한 제품 견본이 상점 첫 눈에 볼 수 없을 정도로 품절되는 것과 관련된 알려진 Adobe Commerce 2.2.2 문제에 대한 패치를 제공합니다.

## 문제

구성 가능한 제품이 있고 특정 옵션 조합의 경우 관련 단순 제품의 재고가 소진되었을 때 색상 견본은 여전히 사용할 수 있으며 상점 첫 화면에서 선택할 수 있습니다.

<u>재현 단계</u>:

1. Commerce 관리에서 색상(빨간색, 검정)과 크기(S, M, L)의 두 가지 속성에 대한 옵션을 사용하여 구성 가능한 제품을 만듭니다.
1. 해당하는 각 단순 제품에 대해 수량을 &quot;1&quot;로 설정합니다.
1. 상점에서 빨간색 M 제품을 장바구니에 추가하고 체크아웃합니다.
1. 관리자에서 품목 수량이 &quot;0&quot;으로 업데이트되도록 주문을 처리합니다.
1. 미납주문이 허용되지 않는지 확인하십시오.
1. 상점 첫 화면에서 같은 제품 페이지로 이동하고 같은 옵션을 선택합니다. 빨간색, M.

<u>예상 결과</u>:

빨간색, M 견본에는 빨간색 슬래시가 있어 선택할 수 없습니다.

<u>실제 결과</u>:

빨간색, M 색상 견본을 선택할 수 있습니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-8215\_EE\_2.2.2\_v1.composer.patch 다운로드](assets/MDVA-8215_EE_2.2.2_v1.composer.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* Adobe Commerce(모든 배포 방법) 2.2.2

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.2.0-2.2.3

## 패치 적용 방법

지침은 [Adobe Commerce에서 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
