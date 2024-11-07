---
title: 데이터베이스를 업로드하면 MySQL에 대한 연결이 끊어집니다.
description: 이 문서에서는 데이터베이스 업로드가 MySQL에 대한 연결을 끊는 경우에 대한 해결 방법을 제공합니다.
exl-id: 6051cea1-8292-4a81-8908-eb516cb4a32b
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# 데이터베이스를 업로드하면 MySQL에 대한 연결이 끊어집니다.

이 문서에서는 데이터베이스 업로드가 MySQL에 대한 연결을 끊는 경우에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라의 Adobe Commerce 2.2.x., 2.3.x

## 문제

데이터베이스가 Adobe Commerce on cloud infrastructure Pro 계획 아키텍처의 기본/통합 분기 또는 Adobe Commerce on cloud infrastructure Starter 계획 아키텍처의 어떤 분기에도 업로드되지 않으며, 증상은 연결할 수 없는 것입니다. CLI에서 이 오류가 표시됩니다.

```
web@ddc35c264bd89a72042f1f3e5a:~$ mysql -h database.internal -u user -p main
Enter password:
ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"
```

## 원인

이는 일반적으로 데이터베이스를 가져올 디스크 공간이 부족하기 때문입니다.

## 솔루션

디스크 공간이 부족한지 확인합니다. 이렇게 하려면 데이터베이스 포트 3306에 대해 CLI에서 `netcat` 명령을 실행합니다. 꽉 차면 디스크 가득 참 메시지가 나타납니다.

```
web@ddc35c264bd89a72042f1f3e5a:~$ nc database.internal 3306
Database out of space
```

`services.yaml`의 데이터베이스에 더 많은 공간을 할당하고 사용하지 않는 공간이 있는 경우 배포해야 합니다. 단계는 [서비스 디스크 공간](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#service-disk-space)을 참조하세요.

참고: Pro 아키텍처 계획에서 다음 명령을 실행하여 파티션에 할당된 공간을 확인할 수 있습니다. `df -h`

다음 출력과 비슷한 출력이 예상됩니다. 이 예에서는 할당된 25GB 중 10GB가 사용되고 MySQL 공간 15GB는 사용되지 않습니다.

```
f240jestone3wt@i-087r2a25fdac80726:~$ df -h|grep 'File\|xvd'
Filesystem                                         Size  Used Avail Use% Mounted on
/dev/xvda1                                          59G   15G   42G  26% /
/dev/xvdj                                           25G   10G   15G  41% /data/mysql
/dev/xvdi                                           25G   22G  2.6G  90% /data/exports
```

## 관련 읽기

개발자 설명서에서 [디스크 공간 관리](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space)
