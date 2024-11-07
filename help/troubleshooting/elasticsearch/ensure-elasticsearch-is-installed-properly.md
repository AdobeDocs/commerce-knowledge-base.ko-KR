---
title: Elasticsearch이 제대로 설치되었는지 확인
description: 이 문서에서는 잘못된 Elasticsearch(ES) 설치 및 구성으로 인해 발생하는 문제에 대한 해결 방법에 대해 설명합니다.
exl-id: d2c5971c-4db4-4857-ae79-970313bce981
feature: Install
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Elasticsearch이 제대로 설치되었는지 확인

이 문서에서는 잘못된 Elasticsearch(ES) 설치 및 구성으로 인해 발생하는 문제에 대한 해결 방법에 대해 설명합니다.

>[!WARNING]
>
>클라우드 인프라의 Adobe Commerce에서 서비스 업그레이드는 인프라 팀에 48시간 전에 통보하지 않으면 프로덕션 환경으로 푸시할 수 없습니다. 이는 인프라 지원 엔지니어가 운영 환경에 대한 가동 중지 시간을 최소화하면서 원하는 기간 내에 구성을 업데이트할 수 있도록 해야 하기 때문에 필요합니다. 따라서 변경 내용이 프로덕션에 적용되기 48시간 전에 [지원 티켓을 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)하여 필요한 서비스 업그레이드에 대해 자세히 설명하고 업그레이드 프로세스를 시작할 시간을 지정하십시오.

## Adobe Commerce과의 Elasticsearch 버전 호환성

* Adobe Commerce 온-프레미스 및 Adobe Commerce 온 클라우드 인프라:
   * v2.2.3+에서 ES 5.x 지원
   * v2.2.8+ 및 v2.3.1+에서 ES 6.x 지원
   * ES v2.x 및 v5.x는 [수명 종료](https://www.elastic.co/support/eol) 때문에 사용하지 않는 것이 좋습니다. 그러나 Adobe Commerce v2.3.1이 있고 ES 2.x 또는 ES 5.x를 사용하려면 [Elasticsearch php 클라이언트를 변경](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search)해야 합니다.
* Magento Open Source v2.3.0+는 ES 5.x 및 6.x를 지원합니다(6.x가 권장됨).

## 문제

다음 증상은 Elasticsearch이 올바르게 구성되지 않았음을 나타냅니다.

* `Error: No alive nodes in your cluster` - 이 오류는 Adobe Commerce 로그에 표시될 수 있습니다.
   * `var/log/system.log`
   * `var/log/support_report.log`
   * `var/log/cron.log`
   * `var/log/exception.log`
   * 또는 프롬프트(예: 색인 재지정 실행 시)
* Elasticsearch 버전이 현재 버전의 Adobe Commerce과 호환되지 않음을 나타내는 오류(클라우드 인프라의 Adobe Commerce 관련 오류):

  ```
  [YYYY-MM-DD HH:MM:SS] CRITICAL: Fix configuration with given suggestions:    - Elasticsearch version #<version> is not compatible with current version of magento    Upgrade elasticsearch version to ~5.0
  ```

여기서 *version*&#x200B;은(는) 클라우드 환경에서 실행되는 Elasticsearch 서비스입니다.

## 원인

Elasticsearch이 제대로 설치되지 않았습니다. 이는 다음 때문일 수 있습니다.

* 구성 파일의 오타.
* 구성 파일의 버전이 환경에 설치된 Elasticsearch 버전과 일치하지 않습니다.
* 환경에 올바르게 설치되고 구성 파일에 올바르게 구성된 버전이지만 현재 설치된 Adobe Commerce 버전에 대해 지원되는 버전이 아닙니다.

## 솔루션

Elasticsearch을 올바르게 설정하려면 다음을 수행하십시오.

* 클라우드 인프라의 Adobe Commerce에 있는 판매자는 개발자 설명서에 나와 있는 단계를 따를 수 있습니다. [Elasticsearch 서비스 설정](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).
* Adobe Commerce 온-프레미스 및 Magento Open Source의 판매자는 개발자 설명서에 있는 단계를 따를 수 있습니다. [Elasticsearch 설치 및 구성](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search).

Elasticsearch을 설정한 후 제대로 구성되었는지 확인합니다.

1. 서버에 로그인.
1. 명령 실행 출력의 Elasticsearch 버전 번호(2.x, 5.x 또는 6.x)를 확인합니다. `curl -XGET <Elasticsearch hostname>:<Elasticsearch server port>` 예를 들어 클라우드 인프라의 Adobe Commerce에서 다음을 수행합니다. `curl -XGET localhost:9200`
1. `php bin/magento config:show catalog/search` 명령을 실행하여 Adobe Commerce on cloud infrastructure 구성에 구성된 내용을 확인하십시오.
1. `catalog/search/engine`을(를) 확인하고 Elasticsearch 버전 번호와 일치하는지 확인하십시오. 예를 들어 클라우드 인프라의 Adobe Commerce에서는
   * Elasticsearch 5.X - elasticsearch5
   * Elasticsearch 6.X - elasticsearch6
   * Elasticsearch 2.X - elasticsearch
1. `index_prefix` 확인. 환경이 여러 개인 경우 해당 환경에 대해 서로 다른 `index_prefix` 값이 있는지 확인하십시오.
