---
title: 'MDVA-30102: Redis 캐시가 꽉 찼습니다.'
description: MDVA-30102 패치는 Redis 캐시가 가득 차서 오류가 발생하는 문제를 해결하며, 제품 목록 페이지(PLP) 및 제품 세부 사항 페이지(PDP)에 제품 누락 등의 문제가 발생합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6이 설치된 경우 사용할 수 있습니다.
exl-id: 34772296-8c93-471c-b5ad-6815adb78ca6
feature: Cache, Categories, Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-30102: Redis 캐시가 꽉 찼습니다.

MDVA-30102 패치는 Redis 캐시가 가득 차서 오류가 발생하는 문제를 해결하며, 제품 목록 페이지(PLP) 및 제품 세부 사항 페이지(PDP)에 제품 누락 등의 문제가 발생합니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6이 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라의 Adobe Commerce 2.3.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.2 - 2.4.1-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Redis 캐시가 꽉 찼으며 할당된 `maxmemory`이(가) 부족한 것 같습니다. 레이아웃 캐시에 TTL이 없고 제거되지 않아 캐시 증가와 Redis의 다른 키가 제거되었습니다. 그 결과 모든 Redis 메모리가 레이아웃 캐시에 할당되었습니다.

<u>필수 구성 요소</u>:

* 사용자는 Adobe Commerce 2.4를 사용하고 있어야 하며 100K 단순 제품(제품 유형은 중요하지 않음)과 50개의 카테고리를 가지고 있어야 합니다.
* Redis 캐시는 개발자 설명서에서 [Adobe Commerce 구성 안내서 > Adobe Commerce 페이지 및 기본 캐시에 Redis 사용](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html#example-command)에 지정된 단계에 따라 구성해야 합니다.

<u>재현 단계</u>:

1. 모든 PDP 및 PLP를 탐색합니다. [OWASP ZAP](https://www.zaproxy.org/)을 사용하여 사이트를 크롤링할 수 있습니다.
1. Redis 메모리 사용을 확인합니다.
1. 또한 현재 구성과 사용 중인 메모리를 확인합니다. CLI에서 다음 명령을 실행합니다. 사용된 메모리, maxmemory, 제거된 키 및 Redis 작동 시간(일 단위)을 확인합니다.

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

<u>예상 결과</u>:

Redis 캐시는 급속히 증가해서는 안 됩니다.

<u>실제 결과</u>:

Redis 캐시는 최대 5GB까지 증가합니다. Redis 메모리에는 최대 8GB의 제한이 있으므로 1M 제품이 있으면 메모리가 매우 빠르게 부족하게 됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
