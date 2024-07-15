---
title: 관리자의 주문 그리드에 표시되지 않는 주문
description: 이 문서에서는 Commerce 관리자의 주문 그리드에 표시되지 않는 주문과 관련된 알려진 Adobe Commerce 2.2.1 문제에 대한 패치를 제공합니다.
exl-id: b8376760-6558-41ed-8c6b-51c5759e831a
feature: Admin Workspace, B2B, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# 관리자의 주문 그리드에 표시되지 않는 주문

이 문서에서는 Commerce 관리자의 주문 그리드에 표시되지 않는 주문과 관련된 알려진 Adobe Commerce 2.2.1 문제에 대한 패치를 제공합니다.

## 문제

B2B 확장이 설치된 Adobe Commerce 2.2.1에서 등록된 고객이 상점 첫 화면에서 만든 주문은 Commerce 관리자의 고객 계정에 있는 주문 목록에 표시되지 않습니다. 디버그 로그(`./var/log/debug.log`)에 다음 오류가 기록됩니다.

`report.CRITICAL: You cannot define a correlation name ‘company_order’ more than once`

<u>필수 구성 요소</u>:

스토어 카탈로그에 Adobe Commerce 샘플 데이터가 아닌 제품이 포함되어 있고 B2B 확장이 설치되어 있습니다.

<u>재현 단계</u>:

1. 매장 프런트로 이동하여 고객 계정을 만듭니다.
1. 장바구니에 제품을 추가하고 체크아웃을 완료하고 주문을 제출합니다.
1. 관리자에 로그인합니다.
1. **고객,**(으)로 이동한 다음 **모든 고객**&#x200B;을 선택합니다.
1. 새로 만든 고객의 경우 **편집**&#x200B;을 클릭하세요.
1. 왼쪽 패널에서 **주문**&#x200B;을 클릭합니다.

<u>예상 결과</u>:

최근에 제출된 순서가 격자에 나열됩니다.

<u>실제 결과</u>:

주문 그리드가 표시되지 않습니다. 대신 빈 페이지가 표시됩니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-7868\_EE\_2.2.1\_v1\_composer.patch 다운로드](assets/MDVA-7868_EE_2.2.1_v1_composer.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* Adobe Commerce 온-프레미스 2.2.1

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* 2.2.0에서 2.2.3으로 클라우드 인프라의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.2.0, 2.2.2 - 2.2.3

## 패치 적용 방법

지침은 지원 기술 자료의 [Adobe Commerce에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
