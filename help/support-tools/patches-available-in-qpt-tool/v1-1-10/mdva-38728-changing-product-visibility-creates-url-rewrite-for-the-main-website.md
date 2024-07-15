---
title: 'MDVA-38728: 제품 가시성을 변경하면 기본 웹 사이트에 대한 URL 다시 쓰기가 생성됩니다.'
description: MDVA-38728 패치는 두 번째 웹 사이트의 제품 가시성을 변경하면 기본 웹 사이트에 대한 URL 다시 쓰기가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38728입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: ad1d5f82-294d-485d-acd3-28c3cd0fbf56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-38728: 제품 가시성을 변경하면 기본 웹 사이트에 대한 URL 다시 쓰기가 생성됩니다.

MDVA-38728 패치는 두 번째 웹 사이트의 제품 가시성을 변경하면 기본 웹 사이트에 대한 URL 다시 쓰기가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-38728입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.2 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

두 번째 웹 사이트의 제품 가시성을 변경하면 기본 웹 사이트에 대한 URL 다시 쓰기가 생성됩니다.

<u>재현 단계</u>:

1. 추가 웹 사이트, 스토어 및 스토어를 만듭니다.
1. 간단한 제품을 만듭니다.
1. 가시성을 **개별적으로 표시되지 않음**(으)로 설정하십시오.
1. 두 번째 웹 사이트에만 제품을 할당합니다.
1. 기타 모든 필수 필드를 채웁니다.
1. 제품을 저장합니다.
1. MySQL 큐 시작:

   ```mysql
   bin/magento queue:consumers:start product_action_attribute.update &
   bin/magento queue:consumers:start product_action_attribute.website.update &
   ```

1. 제품 목록으로 이동합니다.
1. 카탈로그 및 검색에 대한 대량 업데이트를 사용하여 생성된 제품 및 업데이트 가시성 속성을 선택합니다.
1. URL 다시 작성을 확인합니다.

<u>예상 결과</u>:

제품이 지정된 두 번째 웹 사이트에 대해 재작성됩니다.

<u>실제 결과</u>:

기본 웹 사이트에 대해 다시 작성됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
