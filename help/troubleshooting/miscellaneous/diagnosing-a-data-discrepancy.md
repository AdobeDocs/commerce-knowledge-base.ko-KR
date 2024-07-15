---
title: 데이터 불일치 진단
description: 이 문서에서는 MBI(Magento Business Intelligence) 보고서와 쿼리 또는 타사 보고서 간 불일치를 해결하는 방법을 제공합니다.
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 데이터 불일치 진단

이 문서에서는 MBI(Magento Business Intelligence) 보고서와 쿼리 또는 타사 보고서 간 불일치를 해결하는 방법을 제공합니다.

분석의 복잡성에 따라 해당 MBI 보고서를 생성하려면 플랫폼의 여러 다른 패싯에 익숙해야 할 수 있습니다. 이 체크리스트 및 관련 링크는 모든 불일치의 출처를 식별할 수 있도록 보고서 이면의 논리를 이해하는 데 도움이 됩니다.

1. 팀의 다른 구성원이 보고서를 만든 경우 먼저 분석의 목적과 매개 변수를 확인합니다.
1. 쿼리, 서드파티 보고 도구 또는 수식을 기반으로 MBI 보고서와 비교할 예상 데이터 포인트를 생성합니다.
1. Report Builder의 지표 링크에서 또는 [시스템 요약](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary) 탭을 방문하여 [지표](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html) 정의를 검토하고 확인합니다.
   * 데이터 테이블
   * 작업
   * 피연산자 열, 파생된 경우 해당 계산 포함(시스템 요약을 통해)
   * 타임스탬프
   * 구독 지표의 경우: 시작 및 종료 날짜
   * 적용된 [필터 집합](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html)에 포함된 필터 포함
1. 보고서에서 다른 데이터 조작을 검토하고 확인합니다.
   * 계산된 공식
   * [그룹화](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html#groupby)
   * [관점](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * [시간 옵션](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * [집단 분석](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis)의 경우: 집단 날짜
   * [집단 분석](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis)의 경우: 집단 관점
1. 불일치에 최근 데이터가 포함된 경우 연결 페이지의 **업데이트 세부 정보** 섹션을 참조하여 사용 가능한 최신 데이터 포인트를 확인하십시오.
1. 분석에 사용된 지표가 해당 테이블에서 행이 삭제된 데이터베이스의 테이블에 작성되어 있는 경우 테이블이 삭제된 행에 대해 검사되고 있는지, 다시 검사 빈도 및 테이블에 대한 [복제 방법](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html)을(를) MBI 지원 팀에 확인하십시오.
1. 마찬가지로, 행을 추가한 후 분석에 사용된 열을 수정할 수 있는 경우 이러한 열이 [수정 확인됨](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html)과 재확인 빈도를 확인하고 있는지 확인하십시오.

**아직 걸렸어요?** 걱정하지 마세요. 도와드리겠습니다. [이 지침](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md)을 사용하여 요청을 보냅니다.
