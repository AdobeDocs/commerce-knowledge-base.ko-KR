---
title: 새 주문이 아카이브로 전송됩니다.
description: 이 문서에서는 Commerce 관리자의 주문 그리드 대신 아카이브에 표시되는 새로 생성된 주문과 관련된 알려진 Adobe Commerce 2.2.0 문제에 대한 패치를 제공합니다.
exl-id: 37b70d28-0569-44f2-b677-29b2bde0bc5c
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# 새 주문이 아카이브로 전송됩니다.

이 문서에서는 Commerce 관리자의 주문 그리드 대신 아카이브에 표시되는 새로 생성된 주문과 관련된 알려진 Adobe Commerce 2.2.0 문제에 대한 패치를 제공합니다.

>[!NOTE]
>
>이 문제는 2.2.3 이상에서 해결되었습니다.

## 문제

고객이 주문을 하면 일반 주문 그리드 대신 보관된 주문 그리드에 표시됩니다.

<u>재현 단계</u>:

1. 상점 앞의 장바구니에 제품을 추가하고 체크아웃을 진행한 후 주문합니다.
1. Commerce 관리에서 **판매** > **작업** > **주문**(으)로 이동합니다. 눈금에 순서가 나타납니다.
1. **판매** > **보관** > **주문**(으)로 이동합니다. 표에서 새 순서를 확인합니다.

<u>예상 결과</u>:

순서는 주문 그리드에만 표시됩니다.

<u>실제 결과</u>:

순서는 주문 그리드 및 주문 아카이브 그리드에 표시됩니다.

## 솔루션

패치를 적용하면 예상대로 주문 그리드에 주문이 나타납니다. 하지만 패치가 적용되기 전에 아카이브로 전송된 항목을 Commerce 관리에서 수동으로 복원해야 합니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-8007\_EE\_2.2.0\_v1.composer.patch 다운로드](assets/MDVA-8007_EE_2.2.0_v1.composer.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* Adobe Commerce 2.2.0

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* Adobe Commerce 온-프레미스, Adobe Commerce on cloud infrastructure 2.2.1 - 2.2.3

## 패치 적용 방법

자세한 지침은 지원 기술 자료에서 [Adobe Commerce에서 제공하는 작성기 패치 적용 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 사용 안내서의 유용한 링크

* [보관된 주문 관리](https://docs.magento.com/user-guide/sales/order-archive.html)

## 첨부 파일
