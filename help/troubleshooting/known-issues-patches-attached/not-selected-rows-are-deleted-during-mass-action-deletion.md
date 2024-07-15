---
title: 관리자에서 대량 삭제하는 동안 시작된 것보다 더 많은 제품이 삭제되었습니다.
description: 이 문서에서는 Commerce 관리자의 그리드에서 대량 삭제가 수행될 때 삭제되는 레코드를 선택하지 않는 것과 관련된 Cloud Infrastructure 2.2.3의 알려진 Adobe с 상거래 문제에 대한 패치를 제공합니다.
exl-id: 0bfdc84e-0292-4702-a20e-bdbe67c111a2
feature: Admin Workspace, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# 관리자에서 대량 삭제하는 동안 시작된 것보다 더 많은 제품이 삭제되었습니다.

이 문서에서는 Commerce 관리자의 그리드에서 대량 삭제가 수행될 때 삭제되는 레코드를 선택하지 않는 것과 관련된 Cloud Infrastructure 2.2.3의 알려진 Adobe с 상거래 문제에 대한 패치를 제공합니다.

## 문제

관리자에서 삭제할 고객 또는 클라이언트 레코드를 선택하고 그리드를 필터링한 다음 **삭제** 작업을 선택하면 모든 레코드가 삭제됩니다.

<u>재현 단계</u>:

1. 관리자의 **카탈로그** > **제품**(으)로 이동합니다.
1. 제품 또는 여러 제품을 선택합니다.
1. 작업 드롭다운 메뉴에서 삭제 를 선택합니다.

<u>예상 결과</u>:

선택한 제품만 삭제됩니다.

<u>실제 결과</u>:

일부 다른 제품도 삭제됩니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-10600\_EE\_2.2.3\_v1.composer.patch 다운로드](assets/MDVA-10600_EE_2.2.3_v1.composer.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* 클라우드 인프라의 Adobe Commerce 2.2.3

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* Adobe Commerce 온-프레미스 2.1.8-2.1.14, 2.2.0-2.2.2 및 2.2.4-2.2.5
* 클라우드 인프라 2.2.4-2.2.5의 Adobe Commerce

## 패치 적용 방법

지침은 [Adobe Commerce에서 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.
