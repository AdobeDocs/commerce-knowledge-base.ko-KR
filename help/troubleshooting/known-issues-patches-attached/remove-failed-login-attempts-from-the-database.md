---
title: 데이터베이스에서 실패한 로그인 시도 제거
description: 이 문서에서는 Adobe Commerce 온-프레미스 및 Adobe Commerce 온 클라우드 인프라 데이터베이스에서 실패한 기존 로그인 자격 증명을 제거하는 방법에 대해 설명합니다. 버전 2.2.10+ 및 2.3.3+의 경우 첨부된 스크립트만 실행하면 됩니다. 이전 버전 2.3.0-2.3.2-p2의 경우, 로깅을 중지하는 패치를 적용하고 연결된 스크립트를 실행하여 기존의 실패한 로그인 자격 증명을 제거해야 합니다.
exl-id: 0d7e3674-3563-414f-86a2-297eb8104099
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# 데이터베이스에서 실패한 로그인 시도 제거

>[!NOTE]
>
>이 문서는 2020년 4월 13일에 업데이트되었으며, DB\_CLEANUP\_SCRIPT\_v2이라는 새로운 스크립트가 있습니다. 첨부된 DB\_CLEANUP\_SCRIPT\_v2 스크립트를 사용하여 추가 테이블에서 기존의 실패한 로그인 데이터를 지우십시오. 이전에 DB\_CLEANUP\_SCRIPT\_v2을 실행한 적이 있더라도 추가 테이블을 정리하려면 DB\_CLEANUP\_SCRIPT\_v1을 사용해야 합니다.

이 문서에서는 Adobe Commerce 온-프레미스 및 Adobe Commerce 온 클라우드 인프라 데이터베이스에서 실패한 기존 로그인 자격 증명을 제거하는 방법에 대해 설명합니다. 버전 2.2.10+ 및 2.3.3+의 경우 첨부된 스크립트만 실행하면 됩니다. 이전 버전 2.3.0-2.3.2-p2의 경우, 로깅을 중지하는 패치를 적용하고 연결된 스크립트를 실행하여 기존의 실패한 로그인 자격 증명을 제거해야 합니다.

## **영향을 받는 제품 및 버전**

* 이 문제는 클라우드 인프라 2.2.x, 2.3.x 및 이전 버전의 Magento Open Source, Adobe Commerce 온프레미스 및 Adobe Commerce에 영향을 줍니다.
* Adobe Commerce 1.x 배포는 영향을 받지 않습니다.

## 문제

2019년, Adobe Commerce 2.3.x 및 2.2.x에서 실패한 로그인 시도가 데이터베이스에 로그인할 수 있도록 허용하는 버그가 Adobe Commerce에 보고되었습니다. 이에 Adobe Commerce은 Adobe Commerce 2.3.3 및 2.2.10에서 이 문제에 대한 수정 사항을 포함했습니다(2019년 10월에 릴리스됨). 해당 버그에 대한 수정 사항으로 인해 실패한 로그인 시도에 대한 로깅이 중지되었지만 이러한 최신 버전으로 업데이트하기 전에 수집된 정보는 여전히 존재할 수 있습니다. 이 최신 수정 사항은 이전에 기록된 로그인 시도 정보(있는 경우)를 지웁니다.   CVE-2019-8118은 [일반적인 취약점 및 노출](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-8118)에서 설명 및 추적됩니다.

## 솔루션

첨부된 스크립트와 패치를 사용해야 하는지 아니면 스크립트만 사용해야 하는지 여부는 사용 중인 Adobe Commerce 버전에 따라 다릅니다.

**Adobe Commerce 및 Magento Open Source 버전 2.3.0-2.3.2-p2**

이러한 버전의 경우 패치를 적용하고 연결된 데이터베이스 정리 스크립트를 실행하여 지속적인 로깅을 종료하고 로그를 제거해야 합니다.

1. 작성기 패치를 실행하여 로깅을 중지합니다. 이 패치는 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크 [CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip)를 클릭하십시오. 패치 적용 방법에 대한 지침은 지원 기술 자료에서 [Adobe Commerce에서 제공하는 작성기 패치 적용 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

1. 이제 스크립트를 실행하여 실패한 기존 로그인 시도의 데이터베이스를 정리합니다. 이 스크립트는 기사에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크 [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip)을(를) 클릭하십시오.

지침은 [**스크립트 실행 방법**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) 섹션을 참조하십시오.

**Adobe Commerce 및 Magento Open Source 버전 2.3.3 이상/2.2.10 이상**<br>
이러한 버전의 경우에만 아래 스크립트를 실행하여 이전 로그를 지웁니다(2019년 10월에 릴리스된 수정 사항을 통해 이러한 버전에 대한 로깅이 이전에 종료됨). 이 스크립트는 기사에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크 [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip)을(를) 클릭하십시오.

지침은 지원 기술 자료의 [**스크립트 실행 방법**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) 섹션을 참조하십시오.

**스크립트 실행 방법**

아래 지침에 따라 스크립트를 실행하십시오.

1. `DB_CLEANUP_SCRIPT_v2.php`을(를) Adobe Commerce 또는 Magento Open Source 설치의 루트 디렉터리(`app/bootstrap.php`을(를) 포함하는 앱과 동일한 디렉터리)에 넣습니다.
1. `php DB_CLEANUP_SCRIPT_v2.php` 터미널에서 이 명령을 실행하면 데이터베이스 정리 프로세스가 시작됩니다.

스크립트를 실행하는 동안 문제가 발생하면 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하거나 [security@magento.com](mailto:security@magento.com)로 전자 메일을 보내십시오.

**첨부 파일**

[CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip)

[DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip)
