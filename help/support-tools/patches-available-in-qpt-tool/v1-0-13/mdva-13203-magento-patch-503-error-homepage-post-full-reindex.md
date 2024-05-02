---
title: 'MDVA-13203 패치: 503 오류 홈페이지 전체 색인 다시 지정'
description: '''MDVA-13203 Adobe Commerce 패치는 사이트에 유지 관리 페이지가 표시되고 *위험: SQLSTATE\[23000\]: ''system.log''에 무결성 제약 조건 위반* 오류가 있는 문제를 해결합니다. 패치 ID는 MDVA-13203입니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13이 설치된 경우 사용할 수 있습니다.'''
exl-id: 8e09010b-9aa4-4a79-b546-a24bb72e0e40
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-13203 패치: 503 오류 홈페이지 전체 색인 재지정

MDVA-13203 Adobe Commerce 패치는 사이트에서 유지 관리 페이지가 표시되고 가 표시되는 문제를 해결합니다. *위험: SQLSTATE\[23000\]: 무결성 제약 조건 위반* 의 오류 `system.log`. 패치 ID는 MDVA-13203입니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13이 설치되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.** 클라우드 인프라의 Adobe Commerce 2.2.4.

**Adobe Commerce 버전과 호환:** Adobe Commerce(모든 배포 방법) 2.3.0-2.4.1.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계:</u>

1. 영향을 받는 URL로 이동합니다.
1. 유지 관리 페이지가 표시됩니다.
1. SSH를 통해 사이트가 유지 관리 상태가 아닌지 확인합니다.
   <pre> bin/magento 유지 관리:상태: 유지 관리 모드가 활성화되지 않음 제외 IP 주소 목록: 없음</pre>
1. 다음 항목 보기 `system.log`:

<pre>grep critical -i var/log/system.log |테일 [2018-09-04 17:05:18] report.CRITICAL: SQLSTATE[23000]: 무결성 제약 조건 위반: 1062 키 'PRIMARY'에 대한 중복된 항목 '4613', 쿼리 위치: 'search_tmp_5b8ebb4e994da5_88027289'('entity_id', 'score') 값(?, ?),... (?, ?), (?, ?) [] [] [2018-09-04 17:05:21] report.CRITICAL: SQLSTATE[23000]: 무결성 제약 조건 위반: 1062 키 'PRIMARY'에 대한 중복된 항목 '4613', 쿼리: 'search_tmp_5b8ebb51579943_52333638'('entity_id', 'score') 값(?, ?),...,(?, ?) [] [] [2018-09-04 17:05:47] report.CRITICAL: SQLSTATE[23000]: 무결성 제약 조건 위반: 1062 키 'PRIMARY'에 대한 중복된 항목 '1350', 쿼리: 'search_tmp_5b8ebb6b7028f4_68065024'('entity_id', 'score') 값(?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, (?, ?)에 삽입 [] [] [2018-09-04 17:05:47] report.CRITICAL: SQLSTATE[23000]: 무결성 제약 조건 위반: 1062 키 'PRIMARY'에 대한 중복된 항목 '1350', 쿼리: 'search_tmp_5b8ebb6b7885a9_23360993'('entity_id', 'score') 값(?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, (?, ?)에 삽입 [] [] 일자: 9월 4일 17:06:11 UTC 2018</pre>

<u>예상 결과:</u> 사이트가 표시됩니다.

<u>실제 결과:</u> 데이터베이스 일관성 문제로 인해 유지 관리 페이지가 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
