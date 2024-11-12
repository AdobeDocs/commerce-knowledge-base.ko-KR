---
title: Adobe Commerce용 고급 보고 문제 해결사
description: Adobe Commerce의 고급 보고 문제는 이 문제 해결사 도구를 사용하여 해결할 수 있습니다. 여기에는 데이터를 표시하지 않는 고급 보고와 404 오류가 포함됩니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 3b402728be7a80b62f21319d2cf91a92f1ad4a0c
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 0%

---

# Adobe Commerce용 고급 보고 문제 해결사

Adobe Commerce의 고급 보고 문제는 이 문제 해결사 도구를 사용하여 해결할 수 있습니다. 여기에는 데이터를 표시하지 않는 고급 보고와 404 오류가 포함됩니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다.

## 1단계 - 사이트가 고급 보고 요구 사항을 충족하는지 확인 {#step-1}

+++**웹 사이트가 고급 보고 요구 사항을 충족합니까?**

고급 보고를 사용할 때 404 오류 페이지가 표시됩니다. 웹 사이트가 [고급 보고 요구 사항](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements)을 충족합니까?

a. 예 - [2단계](#step-2)로 진행합니다.\
b. 아니요 - [고급 보고 요구 사항](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements)의 단계에 따라 사이트에 대한 고급 보고 요구 사항을 완료합니다. 그런 다음 [2단계](#step-2)로 진행합니다.

+++

## 2단계 - 여러 기본 통화로 주문이 있습니까? {#step-2}

+++**여러 기본 통화가 사용됩니까?**

주문 및 구성에서 여러 기본 통화가 사용됩니까? 이 [!DNL SQL] 명령을 실행하여 현재 구성을 가져옵니다. `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a. 예 - 쿼리에서 반환된 행이 여러 개인 경우 한 통화만 지원하므로 고급 보고를 사용할 수 없습니다.\
b. NO - 출력에 하나의 통화만 표시됩니다. 예: `USD` 주문에서 여러 기본 통화가 사용된 적이 있습니까? 이 [!DNL SQL] 명령을 실행하여 이전 주문 데이터를 가져옵니다.\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**참고: 이 명령을 사용하려면 전체 테이블을 검사해야 하므로 레코드 수가 많은 테이블의 경우 쿼리가 실행되는 동안 성능에 영향을 줄 수 있습니다.** 이전 주문 데이터를 가져옵니다.
여러 기본 통화가 사용된 경우 하나의 통화만 지원되므로 고급 보고를 사용할 수 없습니다. 출력에 하나의 통화만 표시되면 [3단계](#step-3)로 진행합니다.

+++

## 3단계 - 분할 데이터베이스가 사용 중인지 확인 {#step-3}

+++**분할 데이터베이스 솔루션을 사용하고 있습니까?**

[분할 데이터베이스 솔루션](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)을 사용하고 있습니까?

a. 예 - 분할 데이터베이스 솔루션 및 캐시 지우기에서 Advanced Reporting 404 오류의 패치 **MDVA-26831**&#x200B;을(를) 사용합니다. 작업이 다시 실행될 때까지 24시간 기다린 후 다시 시도하십시오.\
b. 아니요 - [4단계](#step-4)로 진행합니다.

+++

## 4단계 - 고급 보고 활성화 확인 {#step-4}

+++**고급 보고가 활성화되어 있습니까?**

**관리자** > **스토어** > **설정** > **구성** > **일반** > **고급 보고**&#x200B;를 확인합니다. 자세한 단계는 [고급 보고: 고급 보고 사용](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting)을 검토하십시오.

a. 예 - [5단계](#step-5)로 진행합니다.\
b. 아니요 - [고급 보고를 사용하도록 설정](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting)하고 저장하고 Adobe Commerce 및 고급 보고가 동기화되도록 24시간 동안 기다립니다. 이제 데이터가 로드되는지 확인합니다. 만약 당신이 문제를 해결했다면. [5단계](#step-5)로 진행되지 않는 경우

+++

## 5단계 - 토큰 확인 {#step-5}

+++**토큰이 있습니까?**

다음 쿼리를 실행하여 토큰이 있는지 확인하십시오. `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` 토큰이 있습니까?

a. 예 - [7단계](#step-7)로 진행합니다.\
b. 아니요 - 토큰 값이 NULL이거나 데이터베이스에 레코드가 없으면 [6](#step-6)단계로 진행합니다.

+++

## 6단계 - 행 사용 {#step-6}

+++**쿼리가 행을 반환합니까?**

이 쿼리를 실행하여 플래그 테이블에서 카운터 값을 확인합니다. ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` 쿼리가 행을 반환합니까?

a. 예 - 다음 단계를 수행합니다. 1. 아래 쿼리를 실행합니다.\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\. [고급 보고 모듈을 사용하지 않도록 설정](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) 및 [토큰 재인증](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active)을 사용합니다.\
3\. Adobe Commerce 및 고급 보고가 동기화할 때까지 24시간 대기합니다. 고급 보고에서 여전히 데이터를 볼 수 없는 경우 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하십시오.\
b. 아니오 - 쿼리가 아무 것도 반환하지 않으면 다음 단계를 수행합니다. 1. [고급 보고 모듈을 사용하지 않도록 설정](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) 및 [토큰 재인증](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active)을 사용합니다.\
2\. Adobe Commerce 및 고급 보고가 동기화할 때까지 24시간 대기합니다. 고급 보고에서 여전히 데이터를 볼 수 없는 경우 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하십시오.

+++

## 7단계 - `cron_schedule` 테이블의 레코드 확인 {#step-7}

+++**`cron_schedule` 테이블에 레코드가 있습니까?**

`SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G` 쿼리를 실행하여 `analytics_collect_data` 작업이 실행되었는지 확인하십시오.

a. 예 - 레코드가 있고 **status** 열에 _missed_&#x200B;이(가) 표시되면 이 KB 문서 Update Advanced Reporting의 패치를 사용하여 자체 cron 그룹에서 실행하십시오.\
b. 예 - 레코드가 있고 **상태** 열에 _성공_&#x200B;이 표시되면 [9](#step-9)단계를 진행하십시오.\
c. 예 - 레코드가 있고 **status** 열에 _error_&#x200B;이(가) 표시되면 [8단계](#step-8)로 진행하십시오.\
d. 아니요 - 레코드가 없으면 [8단계](#step-8)로 진행합니다.

+++

## 8단계 - `support_report.log`에서 작업 확인 {#step-8}

+++**작업이 `support_report.log`에 기록되었습니까?**

명령 실행: `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. 예 - 쿼리의 출력이 성공적인 작업을 나타내는 경우, 예를 들어 `Cron Job analytics_collect_data is successfully finished`은(는) [9](#step-9)단계로 진행합니다.\
b. 아니요 - 로그에 레코드가 없으면 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)합니다.\
c. 예 - 레코드가 있지만 오류가 있으면 [10단계](#step-10)로 진행합니다.

+++

## 9단계 - `data.tgz` 파일 확인 {#step-9}

+++**파일 `data.tgz`이(가) 시스템에 있고 액세스 로그에 레코드가 있습니까?**

`data.tgz` 파일이 있는지 확인하려면 이 명령을 실행하십시오. 해시 이름의 디렉터리를 반환해야 합니다.

```
ls -ltr pub/media/analytics/
```

access.logs에 레코드가 있는지 확인하려면 이 명령을 실행합니다.

```
zgrep -i analytics /var/log/platform/[cluster_id|cluster_id_stg]/access.log* | grep MagentoBI
```

a. 예 - `data.tgz` 파일이 있고 액세스 로그에 레코드가 있지만 404 오류가 여전히 있는 경우 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)해야 합니다.\
b. 아니요 - [10단계](#step-10)로 진행합니다.

+++

## 10단계 - 오류 메시지 확인 {#step-10}

+++**cron 작업에서 오류 메시지가 표시됩니까?**

예: `core_config_data` 테이블에 오류 *이(가) 표시됩니다. &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0 파일을 삭제할 수 없습니다*. 경고!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0?lang=en): 해당 파일 또는 디렉터리가 없습니다.*

a. 예 - [에서 ACSD-50165 패치를 사용합니다. 파일을 삭제할 수 없습니다. 경고!연결 해제: Admin](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md)에서 이러한 파일 또는 디렉터리 오류가 없습니다. 작업이 다시 실행될 때까지 24시간 기다린 후 다시 시도하십시오.\
b. 아니요 - [11단계](#step-11)로 진행합니다.

+++

## 11단계 - 페이지 빌더 오류가 있는지 확인 {#step-11}

+++**페이지 빌더로 인해 오류가 발생했습니까?**

예: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. 예 - Adobe Commerce의 일반 고급 보고 cron 작업 오류의 MDVA-19391 패치를 사용하고, 작업이 다시 실행될 때까지 24시간 기다린 후 다시 시도하십시오.\
b. 아니요 - [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[1단계로 돌아가기](#step-1)

## 관련 읽기

Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
