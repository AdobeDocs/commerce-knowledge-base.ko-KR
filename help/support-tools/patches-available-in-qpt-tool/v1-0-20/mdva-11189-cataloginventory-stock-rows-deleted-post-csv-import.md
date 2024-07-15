---
title: 'MDVA-11189: cataloginventory_stock 행이 CSV 가져오기 이후 삭제됨'
description: MDVA-11189 Adobe Commerce 패치는 제품 재고를 업데이트하기 위해 .csv 파일을 가져온 후 'cataloginventory_stock' 테이블의 행이 삭제될 때 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-1189입니다. 이 문제는 Adobe Commerce 2.3.5에서 해결되었습니다.
exl-id: 84e1979c-826c-4c01-b0c7-8054bb4b23f0
feature: Catalog Management, Data Import/Export, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# MDVA-11189: CSV 가져오기 후 cataloginventory_stock 행이 삭제됨

MDVA-11189 Adobe Commerce 패치는 제품 재고를 업데이트하기 위해 .csv 파일을 가져온 후 `cataloginventory_stock` 테이블의 행이 삭제될 때 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-1189입니다. 이 문제는 Adobe Commerce 2.3.5에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.** 클라우드 인프라 2.2.3의 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce(모든 배포 방법) 2.3.0-2.3.4-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

제품 재고를 업데이트하기 위해 `.csv`을(를) 가져온 후 `cataloginventory_stock` 테이블의 행이 삭제되는 문제를 해결했습니다.

<u>재현 단계:</u>

1. 데이터베이스에서 다음 MySQL 명령을 실행합니다. `select count(*) from cataloginventory_stock_status;`
1. 행 수를 확인합니다.
1. crontab을 다음과 같이 설정합니다. `* * * * * /usr/bin/php <path to installation>/bin/magento cron:run  | grep -v "Ran jobs by schedule" >> <path to installation>/var/log/cron.log 2>&1`
1. **시스템** > **도구** > **색인 관리**&#x200B;의 관리 패널로 이동합니다.
1. 인덱서를 *일정별 업데이트*(으)로 설정합니다.
1. **시스템** > *데이터 전송* > **내보내기**&#x200B;로 이동합니다.
1. **엔터티 형식**&#x200B;을(를) *제품* > **계속**&#x200B;과(와) 동일하게 설정합니다.
1. 저장된 `.csv` 파일을 열고 > SKU 및 수량을 제외한 모든 열을 제거합니다.
1. 모든 제품에 대한 수량을 150으로 업데이트합니다.
1. `.csv` 파일을 저장합니다.
1. **시스템** > *데이터 전송* > **가져오기** 로 이동합니다.
1. 다음 값을 설정합니다.
   1. 엔터티 형식: *제품*
   1. 가져오기 동작: *추가/업데이트*
   1. 다른 모든 값은 기본값으로 둡니다.
   1. 파일을 선택하여 카탈로그 제품 스프레드시트를 선택합니다.
1. **데이터 확인** > **가져오기**&#x200B;를 클릭합니다. 5-10분 정도 소요됩니다.
1. 데이터베이스에서 다음 MySQL 명령을 실행합니다.
   `select count(*) from cataloginventory_stock_status;`

<u>실제 결과:</u>

재고를 업데이트하기 위해 CSV를 가져온 후 `cataloginventory_stock`의 행 수가 줄어듭니다.

<u>예상 결과:</u>

재고를 업데이트하려면 CSV 가져오기 후에도 `cataloginventory_stock`의 행 수는 동일하게 유지되어야 합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
