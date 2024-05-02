---
title: 'MDVA-40545: 페이지의 첫 번째 노드만 검색됨'
description: MDVA-40545 패치는 동일한 페이지에 대한 노드가 두 개 이상 있더라도 페이지에 대한 첫 번째 노드만 검색되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40545입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: ac7aaed9-5e81-45fe-b699-40d9c086a05c
feature: CMS, Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-40545: 페이지의 첫 번째 노드만 검색됨

MDVA-40545 패치는 동일한 페이지에 대한 노드가 두 개 이상 있더라도 페이지에 대한 첫 번째 노드만 검색되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5가 설치되었습니다. 패치 ID는 MDVA-40545입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

동일한 페이지에 대한 노드가 두 개 이상인 경우에도 페이지의 첫 번째 노드만 검색됩니다.

<u>재현 단계</u>:

1. 관리 패널에서 다음 위치로 이동합니다. **계층** 메뉴 항목/노드를 두 개 추가합니다.
1. 각 노드에 동일한 CMS 페이지를 추가합니다.
1. 캐시를 지우고 프런트 엔드를 확인합니다.
1. 처음 추가한 하위 메뉴에 대한 링크 및 탐색 표시를 확인합니다.
1. 두 번째로 추가된 하위 메뉴에 대한 링크 및 탐색 표시를 확인합니다.

<u>예상 결과</u>:

두 번째 하위 메뉴의 탐색 표시 및 링크는 두 번째 노드와 관련이 있습니다.

<u>실제 결과</u>:

두 번째 하위 메뉴의 탐색 표시 및 링크는 첫 번째 하위 메뉴와 동일합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션.
