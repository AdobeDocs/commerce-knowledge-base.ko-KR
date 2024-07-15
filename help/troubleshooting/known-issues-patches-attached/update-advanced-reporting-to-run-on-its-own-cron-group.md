---
title: 자체 cron 그룹에서 실행되도록 고급 보고 업데이트
description: 이 문서에서는 고급 보고에 데이터가 표시되지 않는 Adobe Commerce on cloud infrastructure 2.3.0의 알려진 문제에 대한 패치를 제공합니다. 고급 보고 작업 'analytics_collect_data'가 일정에 따라 실행되지 않기 때문입니다. 이 문서에서는 고급 보고 cron 그룹 'analytics'를 만드는 패치를 제공합니다.
exl-id: 8aff9e2b-d9be-4136-975b-05963e23f55c
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# 자체 cron 그룹에서 실행되도록 고급 보고 업데이트

이 문서에서는 고급 보고에 데이터가 표시되지 않는 Adobe Commerce on cloud infrastructure 2.3.0의 알려진 문제에 대한 패치를 제공합니다. 고급 보고 작업 `analytics_collect_data`이(가) 예약에 따라 실행되지 않기 때문입니다. 이 문서에서는 고급 보고 크론 그룹 `analytics`을(를) 만드는 패치를 제공합니다.

## 문제

고급 보고 모듈에 로드되는 데이터가 없습니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 패치가 `analytics` cron 작업 작업을 기본 그룹에서 `analytics`(으)로 이동합니다.

다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-19640\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-19640_EE_2.3.0_COMPOSER_v1.patch.zip)

패치를 적용한 후 다음 SQL 쿼리를 실행합니다. `cron_schedule` 테이블의 레코드를 변경하려면 쿼리를 실행해야 합니다.

```
UPDATE core_config_data
SET `path` = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics")
WHERE `path` LIKE "crontab/default/jobs/analytics%";
```

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* 클라우드 인프라의 Adobe Commerce 2.3.0

이 패치는 Adobe Commerce 온-프레미스 및 Adobe Commerce 온 클라우드 인프라용 Adobe Commerce 버전 및 버전 2.2.2-2.2.10, 2.3.0-2.3.2와 2.3.2-p2 및 2.3.3과도 호환됩니다(하지만 문제를 해결하지는 못할 수 있음)

## 패치 적용 방법

지침은 [Adobe에서 제공한 작성기 패치 적용 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
