---
title: Security Scan Tool 보고서가 비어 있음
description: 이 문서에서는 보안 검색 도구에 실제 보고서가 아닌 빈 페이지가 표시되는 문제를 해결했습니다. 허용 목록에 추가하다 이 문제를 해결하려면 도구에서 사용하는 IP를 방화벽에 추가해야 할 수 있습니다.
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Security Scan Tool 보고서가 비어 있음

이 문서에서는 보안 검색 도구에 실제 보고서가 아닌 빈 페이지가 표시되는 문제를 해결했습니다. 허용 목록에 추가하다 이 문제를 해결하려면 도구에서 사용하는 IP를 방화벽에 추가해야 할 수 있습니다.

## 영향을 받는 제품 및 버전:

* Adobe Commerce(모든 배포 메서드) 및 Magento Open Source, 모든 버전

## 문제

<u>재현 단계</u>:

1. 사용 안내서의 [보안 검색](https://docs.magento.com/m2/ee/user_guide/magento/security-scan.html)에 설명된 대로 웹 사이트를 확인하도록 보안 검색 도구를 구성합니다.
1. 작업 열에서 **검사 실행**&#x200B;을 선택합니다.

<u>예상 결과</u>:

보고서 완료 알림 및 보고서 열기 기능을 봅니다.

<u>실제 결과</u>:

알림과 사용 가능한 보고서가 없습니다.

## 원인

보안 검색 도구가 웹 사이트에 연결할 수 없기 때문에 이 문제가 발생할 수 있습니다. 즉, 웹 사이트가 다운되어 전혀 연결할 수 없거나 보안 검색 도구가 차단되고 있습니다.

## 솔루션

웹 사이트를 열어 보십시오.

* 허용 목록에 추가하다 페이지가 성공적으로 로드되면 보안 검색 도구에서 사용하는 IP를 방화벽에 추가해야 할 수 있습니다. 포트 80 및 443에서 52.87.98.44, 34.196.167.176, 3.218.25.102 IP가 사용됩니다.
* 사이트가 로드되지 않고 *을(를) 반환하는 경우 &quot;요청을 처리하는 동안 오류가 발생했습니다&quot;* 메시지를 반환하면 웹 사이트에서 가능한 오류가 있는지 확인하십시오.

## 관련 읽기

* 개발자 설명서에서 [라이브 및 시작](https://devdocs.magento.com/guides/v2.3/cloud/live/live.html?_ga=2.73579601.273749082.1559572284-888339099.1547722854#security-scan)을 하세요.
* 사용 안내서의 [보안 검사](https://docs.magento.com/m2/ee/user_guide/magento/security-scan.html).
