---
title: Fastly 503 오류 대신 Adobe Commerce 오류 보고서 번호 표시
description: '기본적으로 Fastly는 **503 Service Unavailable** 오류 뒤의 모든 Adobe Commerce 오류를 숨깁니다. Adobe Commerce 오류 로그 보고서 번호를 표시하려면(로그에서 찾고 오류 세부 정보를 보려면) 다음 단계를 수행하여 Fastly를 생략하고 웹 사이트를 여십시오.'
exl-id: c0a4a9f8-a674-4cef-8088-e844594e6076
feature: Cache, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Fastly 503 오류 대신 Adobe Commerce 오류 보고서 번호 표시

기본적으로 Fastly는 **503 Service Unavailable** 오류 뒤에 있는 모든 Adobe Commerce 오류를 숨깁니다. Adobe Commerce 오류 로그 보고서 번호(로그에서 찾아 오류 세부 정보를 볼 수 있음)를 표시하려면 다음 단계를 사용하여 Fastly를 생략하고 웹 사이트를 엽니다.

1. 로컬 컴퓨터의 호스트 파일에 응용 프로그램의 도메인 및 IP 주소를 추가합니다.
1. 브라우저 캐시와 쿠키를 지웁니다(또는 시크릿 모드로 전환).
1. 스토어의 웹 사이트를 다시 열어 Adobe Commerce 오류를 확인합니다.

정품 Adobe Commerce 오류와 오류 보고서 번호가 표시되면 다음 단계에 따라 오류 보고서 파일에 세부 정보를 가져올 수 있습니다.

1. 영향을 받는 환경에 SSH를 추가합니다. 개발자 설명서에서 [환경에 대한 SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections)을(를) 참조하십시오.
1. `./var/report/{error_number}` 파일을 찾습니다.

## 호스트 파일에 애플리케이션 도메인 및 IP 주소 추가: 자세한 단계

1. 로컬 컴퓨터의 명령줄에서 `nslookup` 명령을 실행하여 저장소의 서버 IP를 확인합니다.
   * Pro 아키텍처 사용자(스테이징 및 프로덕션 환경):

   ```
   nslookup {your_project_id}.ent.magento.cloud
   ```

   * 기초 아키텍처 사용자(모든 환경), Pro 아키텍처 사용자(통합 환경):

   ```
   nslookup gw.{your_region}.magentosite.cloud
   ```

1. 다음 형식을 사용하여 로컬 컴퓨터의 호스트 파일에 스토어 도메인 및 애플리케이션 서버 IP를 추가합니다.

```
{server_IP} {store_domain}
```
