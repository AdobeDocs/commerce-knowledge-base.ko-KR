---
title: 'MCP-87 Adobe Commerce 패치: storefront broken'
description: MCP-87 Adobe Commerce 패치를 통해 카탈로그의 스톡 리인덱싱이 느려지는 문제를 해결했습니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13이 설치된 경우 사용할 수 있습니다.
exl-id: 048b2764-6bbf-4a02-9a0a-dbea4e48f92a
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# MCP-87 Adobe Commerce 패치: storefront 손상

MCP-87 Adobe Commerce 패치를 통해 카탈로그의 스톡 리인덱싱이 느려지는 문제를 해결했습니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13이 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce on cloud infrastructure 2.4.0.

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.1 - 2.4.1.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

프로필이 큰 카탈로그의 재고 리인덱스는 매우 느립니다.

<u>재현 단계:</u>

1. 관리 패널에 로그인합니다.
1. **제품** > **카탈로그**(으)로 이동합니다.
1. 제품 그리드에서 모든 항목을 선택합니다.
1. 제품 작업 선택 드롭다운 목록에서 **특성 업데이트**&#x200B;를 선택합니다. **제출**&#x200B;을 클릭합니다.
1. 고급 설정 탭에서 **고급 인벤토리**&#x200B;를 클릭합니다. **재고 가용성**&#x200B;을(를) *재고*(으)로 변경합니다. **저장**&#x200B;을 클릭합니다.
1. 전체 다시 인덱스를 수동으로 수행하고 루트에서 다음 명령을 실행합니다. `bin/magento indexer:reindex`

<u>예상 결과:</u>

Stock Indexer는 빠르게 인덱스를 다시 매깁니다.

<u>실제 결과:</u>

Stock 인덱서는 매우 느리고 완료되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
