---
title: Adobe Commerce의 데이터베이스 스토리지 문제 해결사
description: 이 문서는 데이터베이스에 문제가 있는 Adobe Commerce 고객을 위한 문제 해결사 도구입니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다. 증상 및 구성에 따라 문제 해결사가 데이터베이스의 공간 및 구성 문제를 해결하는 방법에 대해 설명합니다.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# Adobe Commerce의 데이터베이스 스토리지 문제 해결사

이 문서는 데이터베이스에 문제가 있는 Adobe Commerce 고객을 위한 문제 해결사 도구입니다. 각 질문을 클릭하여 문제 해결사의 각 단계에서 답변을 표시합니다. 증상 및 구성에 따라 문제 해결사가 데이터베이스의 공간 및 구성 문제를 해결하는 방법에 대해 설명합니다.

## 1단계 - 공간 문제가 있는 디렉터리 식별 {#step-1}

+++**공간 부족으로 인해 `/tmp`에 문제가 있습니까?**

이는 `/tmp` 마운트가 가득 찼거나, 사이트가 다운되었거나, 노드에 SSH를 사용할 수 없는 등의 다양한 증상으로 표시될 수 있습니다. _장치(28)에 남은 공간이 없음_&#x200B;과 같은 오류가 발생할 수도 있습니다. `/tmp`이(가) 가득 차서 발생하는 오류 목록을 보려면 [/tmp mount full](/help/troubleshooting/miscellaneous/tmp-mount-full.md)을 검토하십시오.

또는 공간 부족으로 인해 `/data/mysql` 문제가 발생했습니까? 이는 사이트 중단, 고객이 장바구니에 제품을 추가할 수 없음, 데이터베이스에 대한 연결 실패 및 _SQLSTATE\[08S01\]: 통신 링크 실패: 1047 WSREP_&#x200B;와 같은 게리아 오류를 비롯한 다양한 증상으로 나타낼 수도 있습니다. 디스크 공간이 부족하여 발생하는 오류 목록을 보려면 [[!DNL MySQL] 클라우드 인프라의 Adobe Commerce에서 디스크 공간이 부족합니다](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md)를 참조하십시오.[!DNL MySQL]

디스크 공간 문제가 있고 New Relic 계정이 있는지 확실하지 않은 경우 [New Relic 인프라 모니터링 호스트 페이지](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/)로 이동하십시오. 여기에서 **저장소** 탭을 클릭하고 **차트 표시** 드롭다운을 5개에서 20개 결과로 변경하고 디스크 사용 비율 차트 또는 표에서 높은 디스크 사용에 대한 표를 확인합니다. 자세한 단계는 [New Relic 인프라 모니터링 > 저장소 탭]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage)을 참조하십시오.

위에 설명된 증상이 있는 경우, 인노드의 상태를 확인하여 파일 번호 문제로 인해 이러한 현상이 발생하지 않는지 확인하십시오. 이렇게 하려면 CLI/Terminal에서 다음 명령을 실행합니다.\
`df -ih`

IUse% > 90%입니까?

a. 예 - 파일이 너무 많기 때문에 발생합니다. Adobe Commerce [클라우드 인프라에서 디스크 공간이 부족할 때 파일을 안전하게 삭제](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26889)하는 단계를 검토하십시오. 이 단계를 완료한 후 [2단계](#step-2)로 진행하십시오. 추가 공간을 요청하려면 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하세요.\
b. 아니요 - 공간을 확인합니다. CLI/터미널에서 `df -h | grep mysql`을(를) 실행한 다음 `df -h | grep tmp`을(를) 실행하여 `/tmp` 및 `/data/mysql` 디렉터리의 디스크 공간 사용량을 확인합니다. [3단계](#step-3)로 진행합니다.

+++

## 2단계 - 디스크 공간 확인 {#step-2}

+++**디스크 공간 사용을 확인하시겠습니까?**

파일 수를 줄이면 CLI/터미널에서 `df -h | grep mysql`을(를) 실행한 다음 `df -h | grep tmp`을(를) 실행하여 `/tmp` 및 `/data/mysql`의 디스크 공간 사용량을 확인하십시오. `/tmp` 또는 `/data/mysql`에 70%보다 많이 사용됩니까?

a. 예 - [3단계](#step-3)로 진행합니다.
b. 아니요 - 쿼리로 인해 사용 가능한 스토리지가 부족할 수 있습니다. 이로 인해 노드가 충돌하여 쿼리가 삭제되고 `tmp` 파일이 제거될 수 있습니다. [!DNL MySQL] CLI에서 `SHOW PROCESSLIST;`의 출력을 검사하여 문제의 원인일 수 있는 쿼리를 확인하십시오. [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 추가 공간을 요청하세요.

+++

## 3단계 - 사용량이 많은 디렉토리 식별 {#step-3}

+++**70%보다 많이 사용된 디렉터리는 무엇입니까?**

70% 이상이 사용된 디렉터리는 무엇입니까? `/tmp` 또는 `/data/mysql`?

>[!NOTE]
>
>기본적으로 데이터베이스 tmpdir은 `/tmp`에 씁니다. 데이터베이스 구성이 여전히 이 기본값으로 설정되어 있는지 확인하려면 [!DNL MySQL] CLI에서 다음 명령을 실행하십시오. `SHOW VARIABLES LIKE "TMPDIR";` 데이터베이스 tmpdir이 여전히 `/tmp`에 기록되고 있으면 값 열에 `/tmp`이(가) 표시됩니다.

a. `/tmp` - [단계 4](#step-4)로 진행합니다. \
b. `/data/mysql` - [5단계](#step-5)로 진행합니다.

+++

## 4단계 - /tmp 마운트 문제 해결 가득 참 {#step-4}

+++**/tmp 마운트 전체 문제 해결**

[Adobe Commerce에 대한 /tmp 마운트 전체 문제 해결](/help/troubleshooting/miscellaneous/tmp-mount-full.md) 문서를 아래로 스크롤하고 솔루션과 모범 사례를 시도하십시오. 그런 다음 CLI/터미널에서 `df -h | grep mysql`을(를) 실행한 다음 `df -h | grep tmp`을(를) 실행하여 `/tmp` 및 `/data/mysql` 디렉터리의 디스크 공간 사용량을 확인합니다\
  70% 미만 사용

>[!NOTE]
>
>[Adobe Commerce에 대한 /tmp 마운트 문제 해결](/help/troubleshooting/miscellaneous/tmp-mount-full.md)의 솔루션은 기본적으로 `/tmp`에 쓰는 데이터베이스 tmpdir에 대한 변수를 변경하지 않은 판매자를 위해 설계되었습니다. tmpdir 값을 변경한 경우 [Adobe Commerce에 대한 /tmp 마운트 전체 문제 해결](/help/troubleshooting/miscellaneous/tmp-mount-full.md)의 지침은 도움이 되지 않습니다.

a. 예 - 문제를 해결했습니다. \
b. 아니요 - [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), 추가 공간을 요청합니다.

+++

## 5단계 - 기본값 확인 {#step-5}

+++**기본값 확인**

데이터베이스 구성이 더 이상 원래 기본값이 아닐 수 있습니다. [!DNL MySQL] CLI `SELECT @@DATADIR;`에서 실행하여 데이터베이스 tmpdir 구성을 찾습니다. `/data/mysql/`이(가) 출력되면 데이터베이스 tmpdir이 이제 `/data/mysql/`에 기록됩니다. [[!DNL MySQL] 클라우드 인프라의 Adobe Commerce에서 디스크 공간이 부족함](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md)의 단계에 따라 이 디렉터리의 공간을 늘리십시오. 그런 다음 CLI/Terminal에서 `df -h | grep mysql`을(를) 실행한 다음 `df -h | grep tmp`을(를) 실행하여 `/data/mysql` 및 `/tmp`의 디스크 공간 사용량을 확인합니다.\
  70% 미만 사용

a. 예 - 문제를 해결했습니다. \
b. 아니요 - [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), 추가 공간을 요청합니다.

+++

[1단계로 돌아가기](#step-1)

## 관련 읽기

* Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
