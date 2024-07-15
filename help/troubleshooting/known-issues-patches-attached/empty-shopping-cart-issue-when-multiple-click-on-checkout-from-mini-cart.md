---
title: 미니 장바구니에서 체크아웃을 여러 번 클릭할 때 빈 장바구니 문제
description: 이 문서에서는 고객이 미니 장바구니에서 **체크아웃으로 이동**을 여러 번 클릭한 후 장바구니가 비어 있는 것과 관련된 알려진 Adobe Commerce 2.2.3 문제에 대한 패치를 제공합니다.
exl-id: 06b82c91-8998-4e7b-9fc0-671c9b2a2d3f
feature: Checkout, Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# 미니 장바구니에서 체크아웃을 여러 번 클릭할 때 빈 장바구니 문제

이 문서에서는 고객이 미니 장바구니에서 **체크아웃으로 이동**&#x200B;을 여러 번 클릭한 후 장바구니가 비어 있는 것과 관련된 알려진 Adobe Commerce 2.2.3 문제에 대한 패치를 제공합니다.

## 문제

고객이 장바구니에 제품을 추가하고 **체크아웃으로 이동** 단추를 여러 번 클릭하여 체크아웃을 시도하지만 장바구니로 이동하면 장바구니가 비어 있습니다. 미니 장바구니에 여전히 제품이 표시될 수 있습니다.

<u>재현 단계</u>:

1. 상점 정면에 있는 제품 페이지를 엽니다.
1. 장바구니에 제품을 추가합니다.
1. 미니 장바구니에서 **체크아웃으로 이동**&#x200B;을 여러 번 클릭합니다.

<u>예상 결과</u>:

장바구니에는 추가한 모든 제품이 포함됩니다.

<u>실제 결과</u>:

장바구니에 항목이 없습니다.

## 패치

패치는 이 문서에 첨부되어 있습니다. 패치를 다운로드하려면 문서 끝까지 아래로 스크롤하여 필요한 파일 이름을 클릭하거나 다음 링크 중 하나를 클릭합니다.

[MDVA-10441\_EE\_2.2.3\_v3.composer.patch 다운로드](assets/MDVA-10441_EE_2.2.3_v3.composer.patch.zip)

[MDVA-17078\_EE\_2.2.5\_COMPOSER\_v1.patch 다운로드](assets/MDVA-17078_EE_2.2.5_COMPOSER_v1.patch.zip)

### 호환 가능한 Adobe Commerce 버전

패치는 다음에 대해 생성되었습니다.

* Adobe Commerce 온-프레미스 2.2.3(`MDVA-10441_EE_2.2.3_v3.composer.patch` 파일)
* cloud infrastructure 2.2.5의 Adobe Commerce(`MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` 파일)

`MDVA-10441_EE_2.2.3_v3.composer.patch` 패치는 다음 Adobe Commerce 버전 및 버전과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* Adobe Commerce on cloud infrastructure 버전 2.2.1 - 2.2.5
* Adobe Commerce 온-프레미스 버전 2.2.1에서 2.2.5로

`MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` 패치는 다음 Adobe Commerce 버전 및 버전과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* Adobe Commerce 2.2.5

## 패치 적용 방법

지침은 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
