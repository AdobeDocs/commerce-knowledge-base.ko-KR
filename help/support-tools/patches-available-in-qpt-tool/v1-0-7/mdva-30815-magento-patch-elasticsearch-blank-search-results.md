---
title: 'MDVA-30815: 빈 검색 결과 Elasticsearch'
description: MDVA-30815 패치는 Elasticsearch 결과의 제한 옵션이 변경될 때 검색 결과에 빈 페이지가 표시되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.3.5에서 해결되었습니다.
exl-id: dbe41a43-e248-407e-8cf9-319ad5843935
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30815: 빈 검색 결과 Elasticsearch

MDVA-30815 패치는 Elasticsearch 결과의 제한 옵션이 변경될 때 검색 결과에 빈 페이지가 표시되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.3.5에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라의 Adobe Commerce 2.3.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

Elasticsearch을 사용할 때 검색 결과의 제한 옵션을 변경하면 Adobe Commerce에 빈 페이지가 표시됩니다.

<u>필수 구성 요소</u>:

Elasticsearch은 **사용**&#x200B;입니다. **스토어** > **설정** > **구성** > **카탈로그** > **카탈로그 검색**&#x200B;으로 이동합니다.

<u>재현 단계</u>:

1. 사이트로 이동합니다.
1. 기본 검색 필드에서 제품을 검색합니다.
1. 검색 결과 페이지가 표시되면 검색 결과 페이지의 마지막 페이지를 클릭합니다.
1. 제한기 옵션에서 **페이지당 xx 표시**&#x200B;를 선택합니다. 현재 구성된 검색 결과 번호와 다른 검색 결과 번호 제한인지 확인하십시오.

<u>예상 결과</u>:

페이지에 구성된 제품 결과 수가 표시됩니다.

<u>실제 결과</u>:

빈 페이지가 표시됩니다. 이 오류는 `var/report`: *\`&quot;0&quot;:&quot;SQLSTATE\[42000\]: 구문 오류 또는 액세스 위반: 1064 SQL 구문에 오류가 있습니다. MySQL 서버 버전에 해당하는 설명서에서 &#39;\`* 근처에 사용할 올바른 구문을 확인하십시오.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
