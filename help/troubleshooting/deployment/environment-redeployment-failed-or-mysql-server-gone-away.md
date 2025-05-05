---
title: 환경 재배포에 실패했거나 MySQL 서버가 사라졌습니다.
description: 이 문서에서는 MySQL에 할당된 공간 중단으로 인해 배포 중단 또는 데이터베이스 연결 오류가 발생하는 Adobe Commerce(모든 배포 메서드) 문제에 대한 솔루션을 제공합니다.
exl-id: 2086b45a-0bfe-45cc-bef9-1b6f09ddb70a
feature: Deploy, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 환경 재배포에 실패했거나 MySQL 서버가 사라졌습니다.

이 문서에서는 MySQL에 할당된 공간 중단으로 인해 배포 중단 또는 데이터베이스 연결 오류가 발생하는 Adobe Commerce(모든 배포 메서드) 문제에 대한 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 및 Adobe Commerce 온 클라우드 인프라(모든 버전)

## 문제

* 배포 로그(명령줄 및 UI 로그)에서 다음 오류가 발생하여 배포 프로세스가 실패합니다. ```bash    Re-deploying environment abcdefghijklm-master-7rqtwti         E: Environment redeployment failed    ```
* Adobe Commerce이 503 오류에 응답하고 다음 오류 메시지가 애플리케이션 로그에 표시됩니다.    ```bash    SQLSTATE[HY000] [2006] MySQL server has gone away    ```    그리고 MySQL 서버에 연결할 때 다음 오류가 나타납니다.    ```bash    ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"    ```

## 원인

문제의 가장 가능한 원인은 MySQL 데이터베이스에 할당된 공간이 너무 낮기 때문입니다. 이 경우 MySQL에 사용할 수 있는 공간을 확인합니다(자세한 설명 참조).

### MySQL을 위한 공간이 충분한지 확인

모든 Adobe Commerce on cloud infrastructure Starter 계획 아키텍처 환경 및 [통합 환경](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) of Adobe Commerce on cloud infrastructure Pro 계획 아키텍처의 경우 [환경에 SSH](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=ko)하고 명령을 실행합니다.

```bash
magento-cloud db:size
```

Pro 아키텍처의 스테이징 또는 프로덕션 환경의 경우 [환경에 SSH](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=ko)하고 `df -h`을(를) 실행하십시오   `| grep mysql` 명령입니다. 결과는 다음과 비슷합니다.

```bash
sxpe7gigd5ok2@i-00baa9e24f31dba41:~$ df -h | grep mysql
/dev/xvdj                            40G  7.4G   32G  19% /data/mysql
```

## 솔루션

### 이 문제를 해결하려면 MySQL에 더 많은 공간을 할당해야 합니다.

모든 Starter 아키텍처 및 Pro 아키텍처 통합 환경의 경우 `mysql: disk:` 매개 변수를 늘려 `.magento/services.yaml` 파일에서 이 작업을 수행합니다. For example:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

참조하려면 [MySQL 서비스 설정](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html?lang=ko) 문서를 참조하십시오.

Pro 아키텍처의 스테이징 또는 프로덕션 환경에 대해 이러한 변경 작업을 수행하려면 [지원 티켓](https://support.magento.com)을 만들어야 합니다. 그러나 Adobe Commerce이 이러한 매개 변수를 모니터링하고 경고하거나 계약에 따라 작업을 수행하므로 일반적으로 Pro 아키텍처의 스테이징/프로덕션에서 이 문제를 처리할 필요가 없습니다.

### 변경 사항 적용

`.magento/services.yaml` 파일을 변경한 후에는 변경 내용을 커밋하고 푸시하여 적용해야 합니다. 푸시가 배포 프로세스를 트리거합니다.
