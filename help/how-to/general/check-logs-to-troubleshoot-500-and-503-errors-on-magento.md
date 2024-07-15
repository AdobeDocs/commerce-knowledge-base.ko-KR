---
title: 로그를 확인하여 Adobe Commerce에서 500 및 503 오류 해결
description: 이 문서에서는 'access.log' 및 관련 로그를 확인하여 트래픽 또는 서버 리소스 부족으로 인해 발생할 수 있는 503 및 500 오류를 해결하는 방법에 대해 설명합니다. 'access.log' 및 관련 로그를 보면 클라우드 인프라에서 Adobe Commerce 관련 문제를 일으킬 수 있는 요소에 대한 정보를 얻을 수 있습니다.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# 로그를 확인하여 Adobe Commerce에서 500 및 503 오류 해결

이 문서에서는 트래픽 또는 서버 리소스 부족으로 인해 발생할 수 있는 503 및 500 오류를 해결하기 위해 `access.log` 및 관련 로그를 확인하는 방법에 대해 설명합니다. `access.log` 및 관련 로그를 보면 클라우드 인프라에서 Adobe Commerce 관련 문제를 일으킬 수 있는 원인에 대한 정보를 얻을 수 있습니다.

<!--
Bob - not in TOC
-->

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 [지원되는 버전](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html).

이러한 서버 오류에 대한 로그를 보려면 웹 서버에서 `access.log`을(를) 확인하십시오. 예: `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

관련 로그를 확인하려면:

1. 현재 CLI에 있는 경우(Adobe Commerce on cloud infrastructure Pro 계획 아키텍처의 경우) CLI에서 다음 명령을 실행합니다. 또는 로그 적용 기간이 제한되어 로그 순환을 사용할 수 없으므로 과거 특정 시점까지(클라우드 인프라 시작 계획 아키텍처의 Adobe Commerce의 경우). `grep -r "\" [50[0-9]" /path/to/access.log` 오류가 과거에 발생한 경우 CLI에서 다음 명령을 실행합니다(Pro 아키텍처만 해당). `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. 그런 다음 동일한 타임스탬프에 대한 `exception.log` 및 `error.log` 또는 이와 동등한 [회전된 로그](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#log-rotation)(특정 파일 크기에 도달할 때 자동으로 회전되고 압축되는 로그)를 확인하여 잠재적 오류를 찾고 오류의 원인이 무엇인지 확인하십시오. 참고: `exception.log` 및 `error.log`을(를) 확인하려면 CLI에서 위의 명령을 실행하되, `access.log`을(를) `exception.log` 또는 `error.log`(으)로 바꾸십시오.

## 관련 읽기

* *Cloud Infrastructure의 Adobe Commerce 안내서*&#x200B;에서 [로그 보기 및 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)를 참조하십시오.
* 지원 기술 자료에서 [503 오류 문제 해결](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md)을 참조하십시오.
* 지원 기술 자료에서 [Magento 사이트 작동 중지 문제 해결사](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md)를 참조하십시오.
