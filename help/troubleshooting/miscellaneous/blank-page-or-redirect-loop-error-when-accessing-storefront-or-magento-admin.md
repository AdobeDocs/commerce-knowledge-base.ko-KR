---
title: storefront 또는 Commerce 관리자에 액세스할 때 빈 페이지 또는 리디렉션 루프 오류 발생
description: 이 문서에서는 Adobe Commerce storefront 또는 백엔드에 액세스하고 빈 페이지 또는 리디렉션 루프를 얻는 문제에 대한 솔루션을 제공합니다.
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# storefront 또는 Commerce 관리자에 액세스할 때 빈 페이지 또는 리디렉션 루프 오류 발생

이 문서에서는 Adobe Commerce storefront 또는 백엔드에 액세스하고 빈 페이지 또는 리디렉션 루프를 얻는 문제에 대한 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 버전
* Adobe Commerce 온-프레미스, 모든 버전
* Magento Open Source, 모든 버전

## 문제

<u>재현 단계</u>

상점 또는 관리자 페이지를 엽니다.

<u>예상 결과</u>

페이지가 열립니다.

<u>실제 결과</u>

페이지가 비어 있거나 *을(를) 표시합니다.&quot;이 웹 페이지에 리디렉션 루프 &quot;* 오류 메시지가 있습니다.

## 원인

문제의 가장 가능성 있는 원인 중 하나는 Adobe Commerce이 비보안 URL에서 보안 URL로 리디렉션되도록 설정되었지만 비보안 URL이 보안 URL 설정의 값으로 주어진다는 것입니다.

문제를 해결하려면 보안 링크의 값을 수정해야 합니다.

## 솔루션

이것이 문제의 원인인지 확인하려면 다음 단계를 수행하십시오.

1. `'core_config_data'` DB 테이블에서 `web/secure/enable_upgrade_insecure` , `web/secure/use_in_adminhtml`(Admin에 빈/루프 리디렉션 문제가 있는 경우) 또는 `web/secure/use_in_frontend`(Store Front에 빈/루프 리디렉션 문제가 있는 경우) 값을 확인하십시오.
   * `web/secure/enable_upgrade_insecure`이(가) &quot;1&quot;로 설정되어 있으면 Adobe Commerce이 응답 헤더 `Content-Security-Policy: upgrade-insecure-requests`을(를) 추가하도록 설정되어 브라우저에서 HTTPS를 사용하도록 지시하고 HTTP를 통해 들어오는 모든 쿼리를 리디렉션합니다
HTTPS(관리자 및 상점 모두)로
   * `web/secure/use_in_adminhtml`이(가) &quot;1&quot;(으)로 설정된 경우 Adobe Commerce은 관리 페이지에 대한 모든 HTTP 요청에 대해 HTTPS 리디렉션을 반환합니다.
   * `web/secure/use_in_frontend`이(가) &quot;1&quot;(으)로 설정된 경우 Adobe Commerce은 스토어 전면 페이지에 대한 모든 HTTP 요청에 대해 HTTPS 리디렉션을 반환합니다.
1. `'core_config_data'` 테이블에서 `web/secure/base_url` 및 `web/unsecure/base_url` 값을 확인합니다. 둘 다 다음으로 시작하는 경우    `http`을(를) 선택한 다음 &quot;보안&quot; 값을 수정해야 합니다.

문제 해결:

1. `web/secure/base_url.`에 대해 `https`(으)로 시작하는 값 설정
1. 변경 사항을 적용하려면 다음 명령을 실행하여 구성 캐시를 정리합니다.

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## 관련 읽기

Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
