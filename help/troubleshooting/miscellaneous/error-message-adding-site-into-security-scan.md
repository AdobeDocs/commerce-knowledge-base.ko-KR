---
title: 보안 검색에 사이트를 추가할 때 오류 메시지 표시
description: 이 문서에서는 사용자가 [Commerce 보안 검색](https://account.magento.com/scanner/dashboard/)에 사이트를 추가할 수 없는 경우에 발생하는 문제에 대해 가능한 해결 방법을 제공합니다.
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# 보안 검색에 사이트를 추가할 때 오류 메시지 표시

이 문서에서는 사용자가 [Commerce 보안 검사](https://account.magento.com/scanner/dashboard/)에 사이트를 추가할 수 없는 경우 문제에 대해 가능한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 메서드 및 버전)
* Magento Open Source

## 문제

사용자가 [Commerce 보안 검사](https://account.magento.com/scanner/dashboard/)에 사이트를 추가할 수 없습니다. 사이트를 추가하려고 할 때 다음 오류 메시지가 나타납니다. *검사할 사이트를 제출할 수 없습니다.*

## 솔루션

1. 포트 80 및 443에서 다음 IP 주소가 차단되지 않았는지 확인하십시오.
   * 52.87.98.44
   * 34.196.167.176
   * 3.218.25.102

1. 확인 코드는 시간에 민감합니다. **사이트 추가** 링크를 클릭한 후 30분 이상이 지난 경우 코드가 만료된 것 같습니다.
1. 캐시를 지우고 홈 페이지 소스 본문에 유효성 검사 코드가 나타나는지 확인하십시오. 확인 코드는 HTML 마크업 사양에 따라 삽입해야 합니다. HTML 주석은 페이지 본문에 삽입할 수 있습니다(바닥글 섹션에 삽입하는 것이 좋음). META 태그는 헤드 섹션에만 있어야 합니다.
1. **확인 코드 확인**&#x200B;을 클릭하기 전에 브라우저의 개발자 콘솔을 열고 **네트워크** 탭을 클릭한 다음 magento.com에서 응답을 확인하십시오. HTTP 200(OK)이어야 하며 응답 본문에는 JSON 오브젝트가 포함되어야 합니다.
1. 응답 코드가 HTTP 200이고 응답 본문이 JSON 개체이고 `verified` 속성 값이 `false`인 경우 페이지에서 코드를 찾을 수 없습니다. `details` 속성 값에는 설명이 포함되어야 합니다. 예를 들어 스토어에서 자체 서명된 SSL 인증서를 사용하는 경우 연결 오류가 발생할 수 있습니다.

여전히 사이트를 추가할 수 없는 경우 다음 단계를 완료하십시오.

1. 페이지에 다른 HTML 주석을 배치합니다.

   ```HTML
   <!-- MAGEID:Your magento.com ID, EMAIL:your email address -->
   ```

1. 지원 티켓을 제출하고 다음 정보를 제공하십시오.
   * Adobe Commerce 스토어 URL
   * MAGEID + Magento.com 계정 이메일
   * 이름 + 성
   * 회사 이름
   * 쉼표로 구분된 알림 이메일 목록

## 관련 읽기

* 사용 안내서의 [보안 검사](https://experienceleague.adobe.com/ko/docs/commerce-admin/systems/security/security-scan).
