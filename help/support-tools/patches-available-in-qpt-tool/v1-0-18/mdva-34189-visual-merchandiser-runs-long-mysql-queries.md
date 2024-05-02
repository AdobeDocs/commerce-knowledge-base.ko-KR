---
title: 'MDVA-34189: 시각적 머천다이저가 긴 MySQL 쿼리를 실행합니다.'
description: MDVA-34189 패치는 관리 카테고리 페이지를 로드할 때 Adobe Commerce에서 큰 Visual Merchandiser 쿼리를 실행하는 문제를 해결합니다.
exl-id: 94143d80-3240-4a18-890d-fb759ea9c30d
feature: Categories, Merchandising, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-34189: 시각적 머천다이저는 긴 MySQL 쿼리를 실행합니다.

MDVA-34189 패치는 관리 카테고리 페이지를 로드할 때 Adobe Commerce에서 큰 Visual Merchandiser 쿼리를 실행하는 문제를 해결합니다.

이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18이 설치되었습니다. 패치 ID는 MDVA-34189입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.** 클라우드 인프라의 Adobe Commerce 2.3.5-p2

**Adobe Commerce 버전과 호환:** Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.4-2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

웹 사이트는 프로덕션 서버에서 큰 MySQL 쿼리를 실행합니다.

<u>재현 단계</u>:

1. Visual Merchandiser에 액세스하려면 *관리자* 사이드바, 클릭 **카탈로그** > **카테고리**.
1. 을(를) 로드합니다 **카테고리** [관리] 패널의 페이지(초기 루트 범주 로드)에서 실행되는 쿼리를 확인합니다.

<u>예상 결과</u>:

관리자 **카테고리** 느린 쿼리를 생성하지 않고 페이지를 로드해야 합니다.

<u>실제 결과</u>:

이는 PHP 구성에 따라 다릅니다. 이 오류의 가장 일반적인 예는 **카테고리** 페이지가 열리지 않고 오류 발생 *오류 503 첫 번째 바이트 시간 초과* 표시됩니다.

또는 Adobe Commerce이 Visual Merchandiser를 로드하면 느린 MySQL 쿼리를 실행합니다. 이 쿼리는에 삽입된 많은 제품 ID를 포함합니다. `ORDER BY FIELD(`e`.`entity_id`,  ...)`

위치: `app/code/Magento/VisualMerchandiser/Model/Category/Products.php:: applyPositions`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT 도구에서 사용할 수 있는 다른 패치에 대한 자세한 내용은 [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션.
