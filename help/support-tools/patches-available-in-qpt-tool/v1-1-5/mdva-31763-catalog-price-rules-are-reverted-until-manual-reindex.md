---
title: 'MDVA-31763: 수동으로 다시 색인화할 때까지 카탈로그 가격 규칙이 되돌려짐'
description: MDVA-31763 패치는 수동 색인 재지정 전까지 카탈로그 가격 규칙이 되돌아가는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-31763입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: eb2dfd1a-6d12-4676-82c1-bf92c6fa9fda
feature: Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-31763: 수동으로 다시 색인화할 때까지 카탈로그 가격 규칙이 되돌려짐

MDVA-31763 패치는 수동 색인 재지정 전까지 카탈로그 가격 규칙이 되돌아가는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5가 설치되었습니다. 패치 ID는 MDVA-31763입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.3.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

날짜 `catalogrule_product` 구성 가능한 제품에서 partial 인덱서가 실행되면 카탈로그 규칙이 사라집니다.

<u>재현 단계</u>:

1. 관리 백엔드에 로그인합니다.
1. 다음으로 이동 **스토어** > **속성** > **제품** 및에서 &quot;manufacturer&quot; 속성을 검색합니다.
   * 몇 가지 옵션을 추가하고 &quot;프로모션 규칙 조건에 사용&quot;을 로 설정합니다. *예*.
1. 다음으로 이동 **스토어** > **속성** > **속성 집합**.
   * 기본 속성 세트를 선택하고 &quot;manufacturer&quot; 속성을 추가합니다.
1. 몇 가지 변형을 사용하여 구성 가능한 제품을 만듭니다.
1. 이전에 만든 구성 가능한 제품에 대해 &quot;manufacturer&quot; 속성 값을 설정합니다.
1. 카탈로그 규칙 만들기:
   * 활성 = 예
   * 웹 사이트 = 기본 웹 사이트
   * 고객 그룹 = 로그인되지 않음
   * 조건: 제조업체 = \&lt;selected value=&quot;&quot; for=&quot;&quot; configurable=&quot;&quot; product=&quot;&quot;>
   * 작업: 모든 할인
1. 전체 인덱스를 수행합니다.
1. PDP에서 제품 가격을 확인하고 가격이 정확한지 확인합니다.
1. 작성된 구성 가능한 제품의 &quot;weight&quot; 속성을 업데이트합니다.
1. PDP에서 제품 가격을 확인합니다.

<u>예상 결과</u>:

구성 가능한 제품에 설정된 카탈로그 가격 규칙은 부분 색인 재지정 중 제거되지 않습니다.

<u>실제 결과</u>:

구성 가능한 제품에 설정된 카탈로그 가격 규칙은 부분 색인 재지정 중에 사라집니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션.
