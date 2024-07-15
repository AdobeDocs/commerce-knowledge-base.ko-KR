---
title: 전체 리인덱싱으로 인한 성능 저하
description: 이 문서에서는 전체 리인덱싱으로 인해 성능이 저하되는 문제를 해결합니다(인덱싱 관련 데이터베이스 테이블의 데이터가 업데이트되는 경우).
exl-id: 4f20a862-cf54-4196-8a88-101f0c80f8f1
feature: Best Practices
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# 전체 리인덱싱으로 인한 성능 저하

이 문서에서는 전체 리인덱싱으로 인해 성능이 저하되는 문제를 해결합니다(인덱싱 관련 데이터베이스 테이블의 데이터가 업데이트되는 경우).

## 영향을 받는 버전 및 제품

* 클라우드 인프라의 Adobe Commerce 2.x.x
* Adobe Commerce 온-프레미스 2.x.x

### 문제

지속적인 플러시 및 인덱스 재구축이 성능 저하의 원인 중 일부입니다. 또한 지속적인 전체 리인덱싱은 테이블에 잠금을 추가하여 웹 사이트의 작업을 예상보다 훨씬 느리게 만듭니다.

### 원인

전체 리인덱싱을 생성할 수 있는 작업은 다음을 포함하여 책임자로부터 수행되었습니다.

* 제품 속성 저장
* 웹 사이트/스토어/스토어 조회수 저장
* 구성 저장

>[!NOTE]
>
>이러한 작업이 업무 시간 중에 성능에 영향을 주지 않도록 하려면 이러한 작업을 업무 시간 외에 실행해야 합니다.

[타사 확장](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento)로 인해 전체 다시 색인이 발생할 수도 있습니다. 전체 색인 재지정은 CLI에서 수동으로 실행할 수도 있습니다. 색인이 재지정되고 성능 다운그레이드를 초래할 수 있는 색인이 있는지 확인하려면 다음을 수행하십시오.

1. 지난 15분 동안 완전히 다시 인덱싱된 인덱서를 찾으려면 이 쿼리를 수행하십시오.

   ```
   SELECT * FROM indexer_state WHERE updated > NOW() - INTERVAL 15 MINUTE;
   ```

   출력에서 인덱서 이름은 지난 15분 동안 인덱서가 적어도 한 번 다시 인덱싱되었음을 의미합니다.

1. 빈번한 전체 색인 재지정을 발견한 경우 다음을 조사하십시오.
   * CLI에서 수동으로 이러한 작업을 수행할 수 있는 사람
   * 재인덱싱을 수행하는 타사 모듈
   * 인덱서를 *잘못됨*(으)로 표시하는 타사 모듈

### 솔루션

필요한 경우에만 리인덱싱을 실행합니다. 단계는 개발자 설명서에서 [인덱서 구성](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html#configure-indexers)을 검토하십시오. 일반적인 권장 사항 및 모범 사례는 부분 재인덱싱 메커니즘이 판매자의 수동 작업 없이 데이터 재인덱싱을 처리할 수 있도록 하는 것입니다. 모든 색인 재지정은 기본 Adobe Commerce 기능(Mview)을 사용하여 수행해야 합니다. Mview는 데이터를 다시 인덱싱하는 가장 효율적인 방법인 부분 다시 인덱싱을 수행합니다. Mview에 대한 자세한 내용은 개발자 설명서에서 [색인화 개요: Mview](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview)을(를) 참조하십시오.

## 관련 읽기

* 개발자 설명서에서 [인덱싱 개요: 다시 인덱싱하는 방법](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#how-to-reindex)을 참조하십시오.
* [무효화된 캐시는 지원 기술 자료에서 응답 시간 저하를 일으킵니다](/help/troubleshooting/miscellaneous/invalidated-cache-causes-response-time-degradation.md).
