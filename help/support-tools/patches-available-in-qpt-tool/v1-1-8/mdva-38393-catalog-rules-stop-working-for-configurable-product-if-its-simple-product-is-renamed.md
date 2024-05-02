---
title: 'MDVA-38393: 간단한 제품의 이름이 변경된 경우 구성 가능한 제품에 대한 카탈로그 규칙 작동이 중지됨'
description: MDVA-38393 패치는 구성 가능한 제품의 단순 제품 이름이 변경된 경우 해당 제품에 대한 카탈로그 규칙 작동이 중지되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38393입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: a20856c4-8aff-427b-a404-7afe706be06f
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38393: 간단한 제품의 이름이 변경된 경우 구성 가능한 제품에 대한 카탈로그 규칙 작동이 중지됩니다.

MDVA-38393 패치는 구성 가능한 제품의 단순 제품 이름이 변경된 경우 해당 제품에 대한 카탈로그 규칙 작동이 중지되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8이 설치되었습니다. 패치 ID는 MDVA-38393입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.3.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구성 가능한 제품의 단순 제품 이름이 변경된 경우 해당 제품에 대한 카탈로그 규칙 작동이 중지됩니다.

<u>재현 단계</u>:

1. 연결된 단순 제품을 사용하여 구성 가능한 제품을 만듭니다.
1. 카테고리를 만듭니다.
1. 구성 가능한 제품만 새 범주에 할당합니다.
1. 새 카탈로그 규칙 만들기:
   * 조건 = 범주 포함 \&lt;new category=&quot;&quot; id=&quot;&quot;>
   * 조치 = 50% 할인
   * 활성 = 예
1. 색인 재지정을 수행합니다.
1. 구성 가능한 제품은 프론트엔드에서 확인합니다(할인이 적용되어야 함).
1. 다음 확인: `catalogrule_product` 표(간단한 제품은 할인이 필요합니다.)
1. 관리자로 이동하여 간단한 제품의 이름을 변경합니다. 이렇게 하면 레코드가 `catalogrule_product_cl` 테이블.
1. cron 또는 `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1` 명령입니다.
1. 다음 확인: `catalogrule_product` 테이블.

<u>예상 결과</u>:

구성 가능한 제품에는 할인이 적용됩니다.

<u>실제 결과</u>:

* 단순 제품에 대해 생성된 할인 레코드가 `catalogrule_product` 테이블.
* 프론트엔드에서 구성 가능한 제품은 정가 그대로 판매됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
