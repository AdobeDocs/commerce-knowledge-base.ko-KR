---
title: Adobe Commerce에서 클러스터의 환경 vCPU 계층 보기
promoted: true
description: 이 문서에서는 Observation for Adobe Commerce의 New Relic 인프라 탭을 사용하여 vCPU 계층 할당을 확인하는 방법에 대해 설명합니다. Adobe Commerce 관찰은 Adobe Commerce 사이트의 상태, 현재 및 과거 시간 보기를 표시하는 New Relic nerdlet입니다.
exl-id: a0332e7e-d38d-47d3-b3da-293902f45edc
source-git-commit: 309fda5284de3b8be54e95bf2bfd8ff1777b6c90
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Adobe Commerce에서 클러스터의 환경 vCPU 계층 보기

이 문서에서는 Observation for Adobe Commerce의 New Relic 인프라 탭을 사용하여 vCPU 계층 할당을 확인하는 방법에 대해 설명합니다. Adobe Commerce 관찰은 Adobe Commerce 사이트의 상태, 현재 및 과거 시간 보기를 표시하는 New Relic nerdlet입니다.

## 영향을 받는 제품 및 버전:

클라우드 인프라의 Adobe Commerce 2.4.3 - 2.4.6

## Adobe Commerce에 대한 Observation을 사용하여 vCPU 계층 할당 확인:

Adobe Commerce Nerdlet에 대한 New Relic Observation에 액세스하고 로그인하려면 다음을 수행하십시오.

1. New Relic 홈페이지에서 **앱**&#x200B;을 클릭합니다.
1. **Adobe Commerce에 대한 관찰**&#x200B;을 클릭합니다.
1. Observation for Adobe Commerce nerdlet이 열립니다.
1. **계정 선택** 드롭다운을 클릭하고 계정을 선택합니다.
1. 프로젝트 ID, New Relic 계정 번호 또는 계정 이름을 입력하거나 계정 목록을 검색할 수 있습니다.
1. 시계 아이콘(nerdlet 창의 오른쪽 위)이 있는 밝은 파란색 드롭다운 메뉴를 클릭합니다.
1. 이벤트/문제의 원인을 식별하려는 경우 티켓 날짜 및 시간 이전의 시간을 선택하여 이전 이벤트/데이터가 있는지 확인합니다. **사용자 지정 설정**&#x200B;을 선택하여 사전 설정된 시간대를 사용하거나 사용자 지정 시간대를 설정할 수 있습니다.
1. 탭에서 **인프라**&#x200B;를 클릭합니다. 세 가지 vCPU 계층 그래프가 있습니다.
   * 첫 번째 그래프는 2주 이상 타임라인에 대한 **vCPU 계층 보기를 보여 줍니다(2주 이상 타임라인을 선택해야 함). 참고: 샘플 비율은 일일 입니다. 클러스터 업사이징/다운사이징이 하루에 발생하면 종료 계층 크기가 다음 날**&#x200B;에 표시됩니다.
   * 두 번째 그래프는 타임라인에 대한 **vCPU 계층 보기를 보여 줍니다(24시간 이상, 2주 이하의 타임라인을 선택해야 함)**.
   * 세 번째 그래프는 NODE별 타임라인에 대한 **vCPU 계층 보기를 보여 줍니다. 타임라인을 24시간 미만으로 봐야 함**.

## 관련 읽기

* 지원 기술 자료의 [Adobe Commerce 관찰 개요](/help/support-tools/observation-for-adobe-commerce/observation-adobe-commerce-overview.md).
