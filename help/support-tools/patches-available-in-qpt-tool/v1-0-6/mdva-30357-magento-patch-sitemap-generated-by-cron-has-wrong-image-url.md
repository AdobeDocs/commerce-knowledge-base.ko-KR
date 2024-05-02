---
title: 'MDVA-30357: cron에 의해 생성된 사이트 맵에 잘못된 이미지 URL이 있습니다.'
description: MDVA-30357 패치는 Commerce 관리자의 cron 생성 사이트 맵에서 잘못된 이미지 URL을 만드는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: c91f7ae0-0970-4918-9d1f-4ede6bfcb05f
feature: Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---

# MDVA-30357: 크론에 의해 생성된 사이트 맵에 잘못된 이미지 URL이 있습니다.

MDVA-30357 패치는 Commerce 관리자의 cron 생성 사이트 맵에서 잘못된 이미지 URL을 만드는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6이 설치되었습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 방법) 2.3.2에서 2.4.0으로

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Adobe Commerce의 cron에 의해 생성된 사이트 맵에 잘못된 이미지 URL 경로가 포함되어 있습니다.

<u>재현 단계</u>:

1. Commerce 관리자에서 새 웹 사이트, 스토어 또는 스토어 보기를 만듭니다.
1. 각 스토어에 하나 이상의 제품을 추가하고, 각 제품에 하나 이상의 이미지를 추가합니다.
1. 사용 **일정별 사이트 맵 생성** 위치: **관리자** > **스토어** > **구성** > **카탈로그** > **XML 사이트 맵** > **생성 설정**.
1. 에서 두 저장소 중 하나에 대한 사이트 맵을 수동으로 생성합니다. **관리자** > **마케팅** > **사이트 맵** 와 같은 사이트 맵 이름 사용&#x200B;*sitemap.xml*&quot;.
   * 파일 이름을 다음과 같이 변경합니다.*manual\_sitemap.xml*&quot;또는 파일 컨텐츠를 모든 텍스트 편집기에 복사합니다.
1. cron 작업으로 동일한 사이트 맵 생성 `sitemap_generate`.
1. 수동으로 생성된 사이트 맵 비교 &quot;*manual\_sitemap.xml*&quot;및 cron에 의해 생성된 사이트맵&quot;*sitemap.xml*&quot;.

<u>예상 결과</u>:

캐시된 사이트 맵 이미지 경로 URL이 올바릅니다.

<u>실제 결과</u>:

cron에 의해 생성된 사이트 맵에 잘못된 이미지 경로 URL이 포함되어 있습니다. 에서 이미지를 열려고 하는 경우&#x200B;*sitemap.xml*&quot;, 기본 자리 표시자가 표시됩니다. 수동으로 생성된 사이트 맵 URL은 이 문제의 영향을 받지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.

사이트맵에 대한 자세한 내용은 개발자 설명서에서 다음 문서를 참조하십시오.

* [사이트 맵 및 검색 엔진 로봇 추가](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html)
* [cron 구성 및 실행](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)
* [브라우저에서 실행할 cron.php 보안](https://devdocs.magento.com/guides/v2.4/config-guide/secy/secy-cron.html)
