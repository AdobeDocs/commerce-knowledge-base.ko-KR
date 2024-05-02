---
title: Redis 서비스 충돌
description: 이 문서에서는 Redis 수정 방법을 권장합니다.
exl-id: 5eb8fb70-0f41-433a-8d3f-c368781a2d1d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Redis 서비스 충돌

이 문서에서는 Redis 수정 방법을 권장합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.2.x., 2.3.x
* Adobe Commerce 온-프레미스 2.2.x., 2.3x
* Redis의 모든 버전

## 문제

Redis의 메모리 오버플로로 인해 웹 사이트가 느려지거나 중단되었습니다.

## 원인

메모리 오버플로로 인해 Redis 서비스가 충돌할 수 있습니다. 피크 타임 동안, Redis 서비스는 현재 할당된 것보다 더 많은 메모리를 필요로 할 수 있다.

## 솔루션

현재 구성 및 사용된 메모리를 확인하려면 CLI에서 다음 명령을 실행합니다. 사용된 메모리, maxmemory, 제거된 키 및 Redis 작동 시간(일 단위)을 확인합니다.

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

다음 *REDIS\_PORT* 및 *REDIS\_HOST* 변수는에서 검색할 수 있습니다. `app/etc/env.php`.

위의 쿼리를 실행한 결과 사용 가능한 메모리 비율이 40% 미만이면 [Adobe Commerce 지원에 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 의 증가 요청 `maxmemory` redis Server에서 설정합니다. 제거된 키 값이 &quot;0&quot;이 아니거나 일 단위의 Redis 작동 시간이 0인 경우(Redis가 오늘 충돌했음을 나타냄) [Adobe Commerce 지원에 티켓 제출](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 이 문제에 대한 조사 및 수정 요청.

## 관련 읽기

Redis 메모리에 대한 자세한 내용은 다음을 참조하십시오. [Redis 메모리 최적화](https://redis.io/topics/memory-optimization).
