---
title: 'MDVA-32634 패치: 계층 url_path의 범주 이동 오류'
description: MDVA-32634 패치는 계층에서 범주를 이동한 후 카탈로그 범주의 url\_path가 변경되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: a445dea6-3834-479b-9044-b6d2b863a0b5
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# MDVA-32634 패치: 계층 url_path의 범주 이동 오류

MDVA-32634 패치는 계층에서 범주를 이동한 후 카탈로그 범주의 url\_path가 변경되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.4-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.1 - 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

계층 구조에서 카탈로그 범주를 이동하면 잘못된 url\_path가 생성됩니다. 기본 저장소 범위 \[ **id:0** \]에 할당된 범주의 url\_path는 계층에서 범주를 이동한 후에도 변경되지 않습니다.

<u>재현 단계</u>:

1. Commerce 관리자에 로그인합니다. 루트 범주 아래에 다음의 범주 구조를 만듭니다. move-cat sub-move-cat sub-move-cat2 new-cat-move
1. 다음 쿼리를 사용하여 \[ catalog\_category\_entity\_varchar \] 테이블의 값 지정에 대한 범주 \[ url\_path \] 속성 \[ id: 120 \]을 확인하십시오.

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   이는 다음과 같은 결과를 제공합니다.

   ```sql
   MariaDB [m24dev]> SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   \[ url\_path \] 값이 생성되어 모든 저장소 범위 \[ 0 \]에 할당되었습니다. 이는 B2B가 없는 인스턴스와 비교하여 올바릅니다.
1. 백엔드 범주 목록으로 이동하여 \[ move-cat \]을 \[ new-cat-move \]에 끌어다 놓습니다. 이제 카테고리는 다음과 같아야 합니다. new-cat-move-cat sub-move-cat sub-move-cat2
1. 다음 쿼리를 사용하여 \[ catalog\_category\_entity\_varchar \] 테이블을 확인합니다.

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 16;
   ```

<u>예상 결과</u>:

모든 저장소 범위 \[ 0 \]에 할당된 url\_path도 새 경로로 업데이트해야 합니다.

<u>실제 결과</u>:

이동 후 사용할 수 있는 경로가 없어도 모든 저장소 범위 \[ 0 \]에 할당된 url\_path는 변경되지 않습니다. 또한 각 저장소에 대해 새 url\_path 값이 작성됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
