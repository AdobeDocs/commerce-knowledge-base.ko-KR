---
title: 'MDVA-30782: 장바구니 규칙에 관계없이 동적 블록이 표시됨'
description: MDVA-30782 패치는 장바구니 규칙과 관계없이 동적 블록이 표시되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 88da8853-aae7-4fd9-82ba-a4e9fc99cf53
feature: Cache, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30782: 장바구니 규칙에 관계없이 동적 블록이 표시됨

MDVA-30782 패치는 장바구니 규칙과 관계없이 동적 블록이 표시되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.5-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.5 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관련 카탈로그 가격 규칙 조건이 충족되지 않은 경우에도 동적 블록이 페이지에 표시됩니다.

<u>재현 단계</u>:

1. 두 제품을 만듭니다.
1. 이러한 제품 중 하나에 대해서만 적용할 수 있는 카탈로그 가격 규칙을 만듭니다.
1. 동적 블록을 만들고 새로 만든 카탈로그 가격 규칙을 이 블록에 할당합니다.
1. 다음 매개 변수를 사용하여 위젯을 만듭니다.
   * 유형 = 동적 블록 회전기
   * 표시할 동적 블록 = 지정된 동적 블록
   * 동적 블록 지정 = 블록 양식 단계 \#3Layout 업데이트(모두 가능)
   * 표시 위치 = 모든 제품 유형
   * 컨테이너 = 제품 보조 정보
1. 리인덱싱하고 캐시를 플러시합니다.
1. 두 제품 페이지에서 동적 블록 양식 단계를 확인하십시오. \#3

<u>예상 결과</u>:

동적 블록은 첫 번째 제품 페이지에만 나타납니다.

<u>실제 결과</u>:

동적 블록은 두 제품 페이지에 나타납니다. 표시할 동적 블록 = \#3단계와 관련된 카탈로그 가격 규칙을 사용할 경우 결과는 동일합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
