---
title: 'MDVA-41229: 구성 가능한 제품 가져오기 후 백엔드에서 사용할 수 있는 이미지가 프론트엔드에 표시되지 않음'
description: MDVA-41229 패치는 구성 가능한 제품 가져오기 후 백엔드에서 사용할 수 있는 이미지가 프론트엔드에 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-41229입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: 69d7374f-9f8b-4ec4-8a7f-135ee06135a3
feature: Data Import/Export, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 2%

---

# MDVA-41229: 구성 가능한 제품 가져오기 후 백엔드에서 사용할 수 있는 이미지가 프론트엔드에 표시되지 않음

MDVA-41229 패치는 구성 가능한 제품 가져오기 후 백엔드에서 사용할 수 있는 이미지가 프론트엔드에 표시되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-41229입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.2-p2 및 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

백엔드에서 사용할 수 있는 이미지는 구성 가능한 제품 가져오기 후에는 프론트엔드에 표시되지 않습니다.

<u>재현 단계</u>:

1. 깨끗한 Adobe Commerce을 설치합니다.
1. 아래 설정으로 **스토어** > **특성** > **제품** > **새 특성 추가**&#x200B;로 이동하여 사용자 지정 특성을 추가하십시오.

   * 속성:
      * 속성 속성:

         * 기본 레이블: 크기 설정
         * 저장소 소유자에 대한 카탈로그 입력 유형: 텍스트 견본
         * 필수 값: 아니요
         * 제품 미리 보기 이미지 업데이트: 예

      * 견본 관리(속성 값):

        | 기본임 | 관리자 견본 | 관리자 설명 | 기본 스토어 보기 견본 | 기본 저장소 보기 설명 |
        |---|---|---|---|---|
        | 아니요 | 4 | 4 | 4 | 4 |
        | 아니요 | 24 | 24 | 24 | 24 |
        | 아니요 | 30 | 30 | 30 | 30 |
        | 아니요 | 60 | 60 | 60 | 60 |
        | 아니요 | 68 | 68 | 68 | 68 |

      * 고급 속성 속성:

         * 속성 코드: set_size
         * 범위: 글로벌
         * 고유 값: 아니요
         * 저장소 소유자에 대한 입력 유효성 검사: 없음
         * 열에 추가 옵션: 아니요
         * 필터 옵션에서 사용: 아니요

   * 레이블 관리:

      * 제목(크기, 색상 등) 관리

         * 기본 저장소 보기: 크기 설정

   * Storefront 속성:

      * 검색에 사용: 예
      * 검색 가중치: 1
      * 고급 검색에 표시: 아니요
      * Storefront 비교 가능: 예
      * 레이어 탐색에서 사용: 필터링 가능(결과 포함)
      * 검색 결과 레이어 탐색에서 사용: 예
      * 프로모션 규칙 조건에 사용: 아니요
      * 상점 첫 화면의 카탈로그 페이지에 표시: 예
      * 제품 목록에 사용됨: 예
      * 제품 목록에서 정렬에 사용됨: 아니요

1. 이 특성을 제품 세부 정보 그룹(**스토어** > **특성** > **특성 집합**) 내의 기본 특성 집합에 추가합니다.
1. Adobe Commerce 루트 디렉터리 내의 var 폴더에 설정된 이미지를 다운로드합니다.
1. **시스템** > **데이터 전송** >(으)로 이동하여 아래 옵션을 사용하여 파일을 가져옵니다.

   * 가져오기 설정:

      * 엔티티 유형: 제품

   * 가져오기 동작:

      * 가져오기 동작: 추가/업데이트
      * 유효성 검사 전략: 오류 시 중지
      * 허용된 오류 수: 1
      * 필드 구분 기호: `;`
      * 다중 값 구분 기호: `,`
      * 속성 값 상수: EMPTYVALUE
      * 필드 엔클로저: 선택 취소됨

   * 가져올 파일:

      * 가져올 파일 선택
      * 이미지 파일 디렉터리: 비워 둡니다.

1. `/product-set.html` 페이지로 상점 첫 화면으로 이동하여 다른 설정 크기 간에 전환하십시오. Set Size 24의 경우 갤러리가 없습니다.

<u>예상 결과</u>:

구성 가능한 제품 내의 모든 간단한 제품에 대한 갤러리가 모든 관련 이미지와 함께 표시됩니다.

<u>실제 결과</u>:

그 제품들을 위한 갤러리는 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하십시오.
