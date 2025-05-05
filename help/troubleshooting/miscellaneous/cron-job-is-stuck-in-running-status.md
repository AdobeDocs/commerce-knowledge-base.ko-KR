---
title: "[!DNL Cron] 작업이 **실행 중** 상태에서 중단되었습니다."
description: 이 문서에서는 Adobe Commerce [!DNL cron] 작업 실행이 완료되지 않고 "실행 중" 상태로 유지되어 다른  [!DNL cron] 작업이 실행되지 않는 경우에 대한 해결 방법을 제공합니다. 이 문제는 네트워크 문제, 애플리케이션 충돌, 재배포 문제 등 여러 가지 이유로 발생할 수 있습니다.
exl-id: 11e01a2b-2fcf-48c2-871c-08f29cd76250
feature: Configuration
role: Developer
source-git-commit: 08a241131453725a86eda5f267a209e6705da2e3
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# [!DNL Cron] 작업이 &quot;실행 중&quot; 상태에서 중단되었습니다.

이 문서에서는 Adobe Commerce [!DNL cron] 작업의 실행이 완료되지 않고 &quot;실행 중&quot; 상태로 유지되어 다른 [!DNL cron] 작업이 실행되지 않는 경우에 대한 해결 방법을 제공합니다. 이 문제는 네트워크 문제, 애플리케이션 충돌, 재배포 문제 등 여러 가지 이유로 발생할 수 있습니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce, 모든 버전

## 증상 {#symptom}

재설정해야 하는 [!DNL cron] 작업의 증상은 다음과 같습니다.

* `cron_schedule` 큐에 많은 작업이 나타납니다.
* 사이트 성능 저하 시작
* 작업이 일정에 따라 실행되지 않음

## 솔루션 {#solutions}

### 모든 [!DNL cron] 작업을 한 번에 중지하는 솔루션 {#solution-stop-all-crons-at-once}

>[!WARNING]
>
>`--job-code` 옵션 없이 이 명령을 실행하면 현재 실행 중인 작업을 포함하여 *모든* [!DNL cron] 작업이 재설정되므로 [!DNL cron] 작업을 모두 재설정해야 함을 확인한 후와 같은 예외적인 경우에만 이 명령을 사용하는 것이 좋습니다. 재배포는 기본적으로 이 명령을 실행하여 [!DNL cron] 작업을 재설정하므로 환경이 백업된 후 적절하게 복구됩니다. 인덱서가 실행 중일 때는 이 솔루션을 사용하지 마십시오.

이 문제를 해결하려면 `cron:unlock` 명령을 사용하여 [!DNL cron] 작업을 재설정해야 합니다. 이 명령은 데이터베이스에서 [!DNL cron] 작업의 상태를 변경하여 다른 예약된 작업이 계속 진행될 수 있도록 작업을 강제로 종료합니다.

1. 터미널을 열고 [SSH 키](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/secure-connections)를 사용하여 영향을 받는 환경에 연결합니다.
1. MySQL 데이터베이스 자격 증명 가져오기:    ```shell    echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp    ```
1. `mysql`을(를) 사용하여 데이터베이스에 연결:    ```shell    mysql -hdatabase.internal -uuser -ppassword main    ```
1. `main` 데이터베이스 선택:    ```shell    use main    ```
1. 실행 중인 [!DNL cron]개 작업 모두 찾기:    ```shell    SELECT * FROM cron_schedule WHERE status = 'running';    ```
1. 평소보다 오래 실행되는 작업의 `job_code`을(를) 복사합니다.
1. 이전 단계의 예약 ID를 사용하여 특정 [!DNL cron] 작업의 잠금을 해제하세요.    ```shell    ./vendor/bin/ece-tools cron:unlock --job-code=<job_code_1> [... --job-code=<job_code_x>]    ```

### 단일 [!DNL cron]을(를) 중지하는 솔루션 {#solution-stop-a-single-cron}

1. 터미널을 열고 [SSH 키](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/secure-connections)를 사용하여 영향을 받는 환경에 연결합니다.
1. 다음 명령을 사용하여 장기 실행 작업을 확인하십시오.

   ```date; ps aux | grep '[%]CPU\|cron\|magento\|queue' | grep -v 'grep\|cron -f'```

1. 아래 샘플 출력에서와 같이 출력에서 현재 날짜와 프로세스 목록을 볼 수 있습니다. `START` 열은 프로세스의 시작 시간 또는 날짜를 표시합니다.

   ```
   Wed May  8 22:41:31 UTC 2019
   USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
   root       590  0.0  0.0  27528  2768 ?        Ss   Jan15   0:49 /usr/sbin/cron -f
   bxc2qly+ 25855  0.0  0.0  23724  2184 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe_stg-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe_stg-bxc2qlykqhbqe_stg
   bxc2qly+ 25860 57.7  1.3 584220 222692 ?       S    20:51   0:02 php bin/magento cron:run
   bxc2qly+ 25863  0.0  0.0  23724  2472 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe-bxc2qlykqhbqe
   bxc2qly+ 25876 53.0  0.6 475472 111468 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25878 57.0  0.6 475472 112080 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25880 50.5  0.6 475472 111312 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25882 48.5  0.6 475472 111220 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25884 50.5  0.6 475472 111372 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25890 32.5  0.6 475368 110672 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25892 34.5  0.6 475472 110724 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25894 31.5  0.6 475368 110136 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25896 29.0  0.6 475320 109876 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   ```

1. 배포 프로세스를 차단할 수 있는 오래 실행되는 [!DNL cron] 작업이 표시되면 `kill` 명령을 사용하여 프로세스를 종료할 수 있습니다. **프로세스 ID**(`PID` 열 발견)를 식별한 다음 해당 `PID`을(를) 명령에 추가하여 프로세스를 종료할 수 있습니다.
**프로세스 중지** 명령은 다음과 같습니다.

   ```kill -9 <PID>```

1. 그런 다음 다시 배포하려는 경우 다시 배포할 수 있습니다.
