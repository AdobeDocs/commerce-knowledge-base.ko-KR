---
title: B2B 공유 카탈로그에서 작동하지 않는 범주를 숨기기 위한 GraphQL 쿼리
description: 이 문서에서는 B2B 공유 카탈로그 기능이 범주를 숨기기 위해 GraphQL 범주 쿼리와 작동하지 않는 경우에 대한 솔루션을 제공합니다.
exl-id: bdafa8d9-b637-409e-86b5-d132bccfe0b8
feature: B2B, Catalog Management, Categories, GraphQL, Customer Service
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# B2B 공유 카탈로그에서 작동하지 않는 범주를 숨기기 위한 GraphQL 쿼리


## 영향을 받는 제품 및 버전

* Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.4.3

## 문제

GraphQL 범주 및 `categoryList` 쿼리는 범주 권한을 무시하여 공유 카탈로그에 범주를 숨깁니다. 이 문제는 B2B 공유 카탈로그 기능이 설정된 Adobe Commerce 2.4.3의 모든 가맹점에 발생합니다.

<u>재현 단계</u>:

사전 요구 사항:

이 문제는 B2B 공유 카탈로그 기능이 설정된 Adobe Commerce 백엔드/관리로 GraphQL Adobe Commerce API를 사용하는 PWA 상점 2.4.3의 모든 상인에게 발생합니다.

1. 여러 범주(CAT1,CAT2)를 만듭니다.
1. 비공개 공유 카탈로그를 만듭니다.
1. 회사 사용자를 만들고 위의 공유 카탈로그에 할당합니다.
1. 이러한 각 범주에 몇 가지 제품을 할당하십시오.
1. CAT1을 사용자 지정 카탈로그에 할당하고 CAT2를 사용자 지정 개인 카탈로그에서 할당 해제합니다. 이렇게 하면 공유 카탈로그에서 CAT2의 모든 제품 할당이 취소됩니다.
1. 사용자 지정 카탈로그를 저장합니다.
1. CAT2의 범주 권한을 *Deny* 검색 범주로 설정하고 고객 그룹을 위의 개인 카탈로그로 설정하십시오.
1. 3단계에서 회사 사용자로 `categoryList query` 또는 범주 쿼리를 실행합니다.

<u>예상 결과</u>:

CAT1만 결과에 표시됩니다.

<u>실제 결과</u>:

공유 카탈로그에서 지정/미할당 여부 또는 범주 권한에 관계없이 모든 범주가 표시됩니다.

## 원인

기능이 구현되지 않았습니다.

## 솔루션

이 문제는 버전 2.4.4의 범위에서 수정되며, 2.4.4 릴리스 전에 솔루션이 필요한 경우 가맹점은 [티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 사용자 지정 패치를 받아야 합니다.

## 관련 읽기

* 지원 기술 자료에서 [모범 사례 Adobe Commerce 범주 수 제한](https://support.magento.com/hc/en-us/articles/360048176832).
