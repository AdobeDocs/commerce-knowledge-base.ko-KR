---
title: 'MDVA-43726: 부분 색인 재지정 후 카탈로그 가격 규칙이 적용되지 않음'
description: MDVA-43726 패치는 부분 색인 재지정 후 저장소 수준 특성 일치를 기반으로 하는 카탈로그 가격 규칙이 적용되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43726입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: 70e7e1d2-e601-4fed-9274-a1a619de29e1
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-43726: 부분 색인 재지정 후 카탈로그 가격 규칙이 적용되지 않음

MDVA-43726 패치는 부분 색인 재지정 후 저장소 수준 특성 일치를 기반으로 하는 카탈로그 가격 규칙이 적용되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-43726입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

저장소 수준 속성 일치를 기반으로 하는 카탈로그 가격 규칙이 부분 색인 재지정 후 적용되지 않습니다.

<u>재현 단계</u>:

1. 인덱서 모드를 일정에 따라 실행하도록 설정하십시오.
1. 구성 가능한 두 제품 속성을 만듭니다. 예: 색상(시각적 견본) 및 크기(텍스트 견본).
1. 2단계에서 작성한 두 속성을 모두 사용하여 구성 가능한 제품을 작성합니다.
1. 제품을 만든 후 **예/아니요** 형식 특성을 만들고 규칙 조건에 표시합니다.
1. 이 속성을 기본 속성 집합에 추가합니다.
1. 이 특성이 **예**(으)로 설정된 경우 적용할 카탈로그 가격 규칙을 만듭니다.
1. 구성 가능한 제품과 관련된 간단한 제품 중 하나를 엽니다.
1. 보기를 저장하고 특성 값을 **예**(으)로 업데이트하도록 범위를 변경합니다.
1. `CRON`을(를) 실행하고 프런트 엔드에서 가격을 확인합니다.
1. 전체 색인 재지정을 실행합니다. 프론트엔드에서 가격을 다시 한번 확인해 보세요.
1. 구성 가능한 제품 카테고리를 업데이트합니다.
1. `CRON`을(를) 실행하고 프런트 엔드에서 가격을 다시 확인하세요.

<u>예상 결과</u>:

증분 인덱서를 사용하여 전체 인덱스를 다시 작성하지 않아도 카탈로그 규칙이 올바르게 적용됩니다.

<u>실제 결과</u>:

전체 색인 재지정을 실행하지 않으면 카탈로그 규칙이 적용되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
