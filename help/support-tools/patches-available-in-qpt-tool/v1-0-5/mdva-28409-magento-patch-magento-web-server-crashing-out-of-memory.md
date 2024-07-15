---
title: 'MDVA-28409 패치: Adobe Commerce 웹 서버 충돌 - 메모리 부족'
description: MDVA-28409 패치는 많은 수의 항목을 처리해야 하므로 따옴표 제거를 위한 cron 작업이 중지된 문제를 해결했습니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5가 설치된 경우 사용할 수 있습니다.
exl-id: 175e5f2f-2f76-42ee-83e9-c1b23ff81e96
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-28409 패치: Adobe Commerce 웹 서버 충돌 - 메모리 부족

MDVA-28409 패치는 많은 수의 항목을 처리해야 하므로 따옴표 제거를 위한 cron 작업이 중지된 문제를 해결했습니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5가 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.4 - 2.3.5, 2.4.0

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

문제는 cron 작업에서 처리하려는 데이터 양으로 인해 메모리가 부족해졌다는 것입니다. 이 문제의 증상에는 MySQL의 높은 디스크 사용률과 낮은 웹 서버 메모리로 인한 느린 성능이 포함됩니다.

<u>재현 단계:</u>

오래된 따옴표를 제거할 수 없는 cron 작업이 있는지 확인하려면 다음 쿼리를 실행합니다.

```
select * from cron_schedule where job_code like '%sales_clean_quotes%'
```

<u>예상 결과:</u>

`sales_clean_quotes` cron 작업의 상태는 `success`이어야 합니다.

<u>실제 결과:</u>

`sales_clean_quotes` cron 작업의 상태는 `running` 또는 `error`입니다.

오래된 따옴표를 제거할 수 없는 cron 작업이 있는지 확인하는 또 다른 방법은 **1단계**(`executed_at`)의 쿼리의 출력을 `/var/log/cron.log`의 메모리 오류 타임스탬프에 매핑하는 것입니다. 데이터 양을 처리할 수 없는 cron 작업이 있으면 다음과 유사한 메시지가 표시될 수 있습니다.

```
PHP Fatal error:  Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91

Fatal error: Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91
--
[2020-05-30 05:00:27.224718] Launching command 'php bin/magento cron:run'.
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
