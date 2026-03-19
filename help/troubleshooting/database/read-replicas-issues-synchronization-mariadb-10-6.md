---
title: MariaDB 10.6이 있는 Adobe Commerce Cloud 2.4.6에서 복제본 문제 읽기
description: 이 문서에서는 MariaDB 10.6을 사용하는 Adobe Commerce Cloud 2.4.6에서 복제본 읽기 문제를 해결하는 방법에 대해 설명합니다.
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: 724a30310c3841f8280628436925f9a3e5933b14
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# MariaDB 10.6이 있는 Adobe Commerce Cloud 2.4.6에서 복제본 문제 읽기

이 문서에서는 MariaDB 10.6+와 함께 Adobe Commerce Cloud 2.4.6에서 읽기 전용 복제본을 사용할 때 예기치 않은 비헤이비어에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* MariaDB 10.6+
* 클라우드 인프라의 Adobe Commerce 2.4.6

## 문제

중요하지 않은 읽기에 잘못된 정보가 표시됩니다.

## 원인

값이 `slave_parallel_mode`보수적&#x200B;*이어야 하는 경우 데이터베이스의* 구성이 기본적으로 *optimistics*(으)로 변경되었으며, 값이 `synchronous_replication`false *여야 하는 경우 Ece-Tools의* 값이 *true*(으)로 기본 설정됩니다.

## 솔루션

1. `slave_parallel_mode` 매개 변수가 *conservative*(값이 [conservative](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket)&#x200B;(으)로 표시되지 않는 경우 *지원 티켓을 높여야 함*)로 설정되어 있는지 확인하십시오. 확인하려면 다음 명령을 실행합니다.

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. `.magento.env.yaml` 데이터베이스 구성을 다음으로 업데이트:

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



데이터베이스 구성을 업데이트하는 단계는 Commerce on Cloud Infrastructure Guide의 Deploy variables 항목에서 [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#database_configuration)을 참조하십시오.


## 관련 읽기

* Commerce on Cloud Infrastructure 안내서의 [배포를 위한 환경 변수 구성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html).
* 구현 플레이북의 [데이터베이스 구성 모범 사례](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
