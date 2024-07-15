---
title: 'MDVA-29389: 고급 보고 관련 크론 작업 실패'
description: '''MDVA-29389 패치는 고급 보고에서 ''analytics_collect_data'' cronjob이 "*포트를 호스트 매개 변수(예: localhost:3306)*" 내에 구성해야 하는 문제를 해결했습니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-29389입니다. Adobe Commerce 2.4.2에서 문제가 해결되었습니다.'''
exl-id: eee909d5-9d0d-46b6-846a-665f89db0eee
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-29389: 고급 보고 관련 cron 작업 실패

MDVA-29389 패치는 고급 보고에서 `analytics_collect_data` cronjob이 &quot;*Port가 호스트 매개 변수(예: localhost:3306)*&quot; 내에 구성되어야 하는 문제를 해결했습니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-29389입니다. Adobe Commerce 2.4.2에서 문제가 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 메서드) 2.3.4.

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.1.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. Adobe Commerce 인스턴스에서 고급 보고를 활성화합니다.
1. 다음 쿼리를 실행하여 DB에 analytics/general/token 값을 삽입합니다.

   ```sql
   INSERT INTO core_config_data VALUES(NULL,'default',0,'analytics/general/token','ABCDE',now());
   ```

1. env.php를 열고 다음 형식으로 DB 구성의 호스트 매개 변수에 포트를 추가합니다. `'host' => 'hostname:port',`
1. 캐시를 지웁니다.
1. `analytics_collect_data` cron 작업을 실행합니다.

<u>예상 결과</u>:

기본 또는 기본이 아닌 포트를 사용하여 env.php의 MySQL에 연결할 때 `analytics_collect_data` 작업이 성공적으로 실행됩니다.

<u>실제 결과</u>:

`analytics_collect_data` 작업에서 기본이 아닌 포트를 사용하여 env.php의 MySQL에 연결할 때 &quot;*호스트 매개 변수(예: localhost:3306)*&quot; 내에 포트를 구성해야 한다는 오류가 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
