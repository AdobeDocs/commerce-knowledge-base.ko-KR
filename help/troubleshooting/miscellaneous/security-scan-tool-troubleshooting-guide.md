---
title: Adobe Commerce Security Scan 도구 문제 해결 안내서
description: Adobe Commerce 및 Magento Open Source용 보안 검색 도구와 관련된 다양한 문제를 해결하는 방법을 알아봅니다.
exl-id: 35e18a11-bda9-47eb-924a-1095f4f01017
feature: Compliance, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---

# Adobe Commerce Security Scan 도구 문제 해결 안내서

Adobe Commerce 및 Magento Open Source용 보안 검색 도구와 관련된 다양한 문제를 해결하는 방법을 알아봅니다.

## 문제: 사이트를 제출할 수 없음

보안 검색 도구를 사용하려면 도메인을 보안 검색 도구에 추가하려면 먼저 사이트 소유권을 증명해야 합니다. HTML 댓글 또는 `<meta>` 태그를 사용하여 사이트에 확인 코드를 추가하여 이 작업을 수행할 수 있습니다. HTML 설명은 `<body>` 태그 내부(예: 바닥글 섹션)에 배치해야 합니다. `<meta>` 태그는 페이지의 `<head>` 섹션 내부에 배치해야 합니다.

판매자가 직면하는 일반적인 문제는 보안 검색 도구가 판매자의 사이트 소유권을 확인할 수 없을 때 발생합니다.

오류가 발생하여 검색할 사이트를 제출할 수 없는 경우 지원 기술 자료에서 [보안 검색에 사이트를 추가할 때 오류 메시지](/help/troubleshooting/miscellaneous/error-message-adding-site-into-security-scan.md) 문제 해결 문서를 참조하십시오.

## 문제: 보안 검색 도구에서 생성한 빈 보고서

보안 검색 도구에서 빈 검색 보고서를 가져오거나 *보안 도구가 기본 URL에 연결할 수 없거나*&#x200B;제공된 URL에서 *Magento 설치를 찾을 수 없습니다*&#x200B;와 같은 하나의 오류만 포함된 보고서를 가져옵니다.

### 솔루션

1. 52.87.98.44, 34.196.167.176 및 3.218.25.102 IP가 80 및 443 포트에서 차단되지 않았는지 확인하십시오.
1. 제출된 URL에서 리디렉션(예: `https://mystore.com`에서 `https://www.mystore.com`(으)로 리디렉션 또는 그 반대로 리디렉션 또는 다른 도메인 이름으로 리디렉션)을 확인하십시오.
1. 거부된/이행되지 않은 요청에 대해 WAF/웹 서버 액세스 로그를 조사합니다. HTTP 403 `Forbidden` 및 HTTP 500 `Internal server error`은(는) 빈 보고서를 생성하는 일반적인 서버 응답입니다. 다음은 사용자 에이전트의 요청을 차단하는 확인 코드의 예입니다.

```code block
if(req.http.user-agent ~ "(Chrome|Firefox)/[1-7][0-9]" && client.ip !~ useragent_allowlist)

{   error 403;   }
```

자세한 내용은 지원 기술 자료에서 [보안 검사 도구 보고서가 비어 있습니다](/help/troubleshooting/miscellaneous/the-security-scan-tool-report-is-blank.md) 문서를 참조하십시오.

## 문제: 보안 문제가 해결되었지만 검사에서 여전히 취약한 상태로 표시됨

보안 문제를 해결했으며 보안 검사에서 새로 해결된 문제에 더 이상 취약하지 않음을 보여 줄 것으로 예상됩니다. 대신, 보안 검사에서 생성된 보고서가 여전히 보안 문제에 취약하다고 보고하고 있습니다.

### 원인

클라우드 인스턴스 메타데이터는 `active` 및 `live` 클라우드 프로젝트에 대해서만 수집되며 실시간 프로세스가 아닙니다.

통계 수집 스크립트는 하루에 한 번 실행된 다음 보안 검색 도구는 나중에 새 데이터를 선택해야 합니다.

예상되는 동기화 주기 지연은 최대 1주일이며 최소 24시간이 소요됩니다.

검사에서 다음 상태가 나타날 수 있습니다.

1. **통과**: 보안 검색 도구에서 업데이트된 데이터를 검사하고 변경 내용을 승인했습니다.
1. **알 수 없음**: 보안 검색 도구에 아직 도메인에 대한 데이터가 없습니다. 다음 동기화 주기를 기다립니다.
1. **실패**: 상태가 실패로 표시되면 문제를 해결해야 합니다(2FA 사용, 관리자 URL 변경 등). 다음 동기화 주기를 기다립니다.

인스턴스에 변경 사항이 적용된 후 24시간이 지났고 보안 검색 보고서에 반영되지 않은 경우 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)할 수 있습니다. 티켓을 제출할 때 스토어 URL을 입력합니다.

## BotNet Suspect 오류

&quot;BotNet Suspect&quot; 실패와 관련된 알림을 받습니다.

### 원인

1. 스토어 도메인 이름은 2019년에 &quot;잠재적 BotNet 참가자 목록&quot;에 등록되었으며, 관리 패널, 다운로더 또는 RSS 기능이 공개적으로 노출되었으며 및/또는 CC 스키밍 포럼에서 해당 URL이 언급되었습니다.
1. 경고는 페이지에서 찾을 수 있는 JavaScript과 같은 스토어 손상 및/또는 맬웨어의 기호로 인해 발생할 수 있습니다.
1. 그것은 반드시 진행 중인 문제는 아니다. 스토어가 이전에 손상된 경우 호스트 이름이 여전히 &quot;피해자&quot; 이름으로 다크 웹 주위에 표시될 수 있습니다.
1. 또한 Adobe Commerce이 아니라 시스템 손상(OS 수준)으로 인해 발생할 수 있습니다.

### 솔루션

1. 새로 생성된 SSH 계정, 파일 시스템 변경 사항 등을 확인합니다.
1. 보안 검토를 수행합니다.
1. Adobe Commerce 버전을 확인하고 업그레이드하십시오. 특히 더 이상 지원되지 않는 Magento 1이 계속 실행되고 있는 경우.
1. 문제가 계속되면 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하고 스토어 URL을 제공하십시오.

## 문제: 타협 주입 실패

&quot;타협 주입&quot; 실패와 관련된 오류가 표시됩니다.

### 솔루션

1. Security Scan Tool 보고서에 표시된 스크립트를 검토합니다.
1. 인라인 스크립트 주입에 대한 홈 페이지 소스 본문을 검토합니다.
1. 시스템 구성 변경 내용, 특히 `footer` 섹션 값에서 사용자 지정 `HTML head` 및 `Miscellaneous HTML`을(를) 검토합니다.
1. 삽입된 맬웨어의 익숙하지 않은 변경 사항 및 징후가 있는지 코드 및 데이터베이스 검토를 수행합니다.

위의 방법 중 어느 것도 도움이 되지 않는 경우 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하고 보고서의 스토어 URL 및 오류 메시지를 제공하십시오.

## 자주 묻는 질문

### 보안 검색이 웹 사이트의 성능에 영향을 줍니까?

아니. 보안 검사는 단일 사용자처럼 모든 요청을 하나씩 만듭니다. 이러한 이유로 보안 검사는 웹 사이트 성능에 영향을 주지 않습니다.

### Adobe Commerce은 보안 검색 보고서를 얼마나 오래 보관합니까?

이전 10개의 보고서를 처음부터 생성할 수 있습니다. 이전 보고서가 필요한 경우 Adobe Commerce 지원에 문의하십시오. 최대 1년의 이전 보안 검사 보고서를 얻을 수 있습니다.

### 지원 티켓을 제출할 때 어떤 정보가 필요합니까?

도메인 이름을 입력하십시오.
