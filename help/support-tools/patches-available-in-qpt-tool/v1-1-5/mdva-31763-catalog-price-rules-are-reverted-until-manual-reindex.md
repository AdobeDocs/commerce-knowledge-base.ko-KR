---
title: 'MDVA-31763: 수동으로 다시 색인화할 때까지 카탈로그 가격 규칙이 되돌려짐'
description: MDVA-31763 패치는 수동 색인 재지정 전까지 카탈로그 가격 규칙이 되돌아가는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-31763입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: eb2dfd1a-6d12-4676-82c1-bf92c6fa9fda
feature: Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-31763: 수동으로 다시 색인화할 때까지 카탈로그 가격 규칙이 되돌려짐

MDVA-31763 패치는 수동 색인 재지정 전까지 카탈로그 가격 규칙이 되돌아가는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-31763입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 제품에서 `catalogrule_product` 부분 인덱서가 실행되면 카탈로그 규칙이 사라집니다.

<u>재현 단계</u>:

1. 관리 백엔드에 로그인합니다.
1. **스토어** > **특성** > **제품**(으)로 이동하여 &quot;제조업체&quot; 특성을 검색합니다.
   * 몇 가지 옵션을 추가하고 &quot;프로모션 규칙 조건에 사용&quot;을 *예*(으)로 설정합니다.
1. **스토어** > **특성** > **특성 집합**(으)로 이동합니다.
   * 기본 속성 세트를 선택하고 &quot;manufacturer&quot; 속성을 추가합니다.
1. 몇 가지 변형을 사용하여 구성 가능한 제품을 만듭니다.
1. 이전에 만든 구성 가능한 제품에 대해 &quot;manufacturer&quot; 속성 값을 설정합니다.
1. 카탈로그 규칙 만들기:
   * 활성 = 예
   * 웹 사이트 = 기본 웹 사이트
   * 고객 그룹 = 로그인되지 않음
   * 조건: 제조업체 = \&lt;구성 가능한 제품에 대해 선택된 값>
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

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
