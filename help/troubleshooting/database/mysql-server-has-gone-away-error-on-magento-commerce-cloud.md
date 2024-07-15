---
title: MySQL Server가 클라우드의 Adobe Commerce​에서 오류를 제거했습니다.
description: 이 문서에서는 'cron.log' 파일에 "*SQL Server가 없어짐*" 오류 메시지가 표시되는 문제에 대한 해결 방법에 대해 설명합니다. 이미지 파일 가져오기 문제 또는 배포 실패 등 다양한 증상이 나타날 수 있습니다.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# MySQL Server가 클라우드의 Adobe Commerce&#x200B;에서 오류를 제거했습니다.

이 문서에서는 `cron.log` 파일에 &quot;*SQL Server가 없어짐*&quot; 오류 메시지가 표시되는 문제에 대한 해결 방법에 대해 설명합니다. 이미지 파일 가져오기 문제 또는 배포 실패 등 다양한 증상이 나타날 수 있습니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 [지원되는 버전](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## 문제

`cron.log` 파일에서 &quot;*SQL Server가 없어짐*&quot; 오류 메시지를 받습니다.

<u>재현 단계</u>

파일을 가져오고 배포를 트리거합니다.

<u>예상 결과</u>

배포에 성공했습니다.

<u>실제 결과</u>

`cron.log`의 오류 메시지:&quot; *SQLSTATE\[HY000\] \[2006\] MySQL 서버가 at/app/AAAAAAAAA/vendor/magento/zendframework1/library/Zend/Db/Adapter/Pdo/Abstract.php:144&quot;* 제거됨

## 원인

`default_socket_timeout` 값이 너무 낮게 설정되었습니다. 이 문제는 `default_socket_timeout` 설정으로 인해 발생합니다. php가 이 기간 내에 MySQL 데이터베이스에서 아무 것도 받지 못하면 연결이 끊어진 것으로 가정하고 오류를 발생시킵니다.

## 솔루션

1. CLI에서 실행하여 `default_socket_timeout`의 현재 시간 제한 기간을 확인하십시오.    ```    php -i |grep default_socket_timeout    ```
1. 시간 제한 설정 증가에 따라 `default_socket_timeout` 변수가 `/etc/platform/<project_name>/php.ini` 파일에서 가능한 가장 긴 실행 시간으로 설정됩니다. 10~15분 사이를 설정하는 것이 좋습니다.
1. GIT에 커밋하고 재배포합니다.

## 관련 읽기

* [데이터베이스를 업로드하면 MySQL에 대한 연결이 끊어집니다.](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md)
* [클라우드 인프라의 Adobe Commerce에 대한 데이터베이스 모범 사례](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
* [클라우드 인프라에서 Adobe Commerce의 가장 일반적인 데이터베이스 문제](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)
