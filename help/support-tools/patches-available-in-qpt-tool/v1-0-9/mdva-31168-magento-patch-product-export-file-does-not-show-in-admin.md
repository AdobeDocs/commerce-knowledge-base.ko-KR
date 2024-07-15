---
title: 'MDVA-31168 패치: 제품 내보내기 파일이 관리자에 표시되지 않음'
description: MDVA-31168 패치는 제품 내보내기 CSV 파일이 내보내기 가능한 CSV 파일 목록에 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 해결되었습니다.
exl-id: 780a926b-2aea-47c2-8f95-907cc779bfa4
feature: Admin Workspace, Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# MDVA-31168 패치: 제품 내보내기 파일이 관리자에 표시되지 않음

MDVA-31168 패치는 제품 내보내기 CSV 파일이 내보내기 가능한 CSV 파일 목록에 표시되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.** Adobe Commerce 온-프레미스 2.3.5-p2.

**Adobe Commerce 버전과 호환:** Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.4.1.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>필수 구성 요소</u>:

샘플 데이터를 사용하여 Adobe Commerce을 설치합니다.

<u>재현 단계:</u>

1. 다운로드 가능한 제품을 만들어 **Bags** 범주에 할당합니다.
1. 모든 제품에 대한 내보내기를 시작합니다.
1. CLI에서 다음 명령을 실행합니다.    ```php    bin/magento queue:consumers:start exportProcessor --single-thread --max-messages=10000    ```

<u>예상 결과:</u>

모든 제품과 함께 제품 내보내기 CSV 파일은 예상대로 관리자의 파일 목록에 표시됩니다.

<u>실제 결과:</u>

모든 제품이 포함된 제품 내보내기 CSV 파일이 Admin의 목록에 표시되지 않습니다. 하지만 헤더만 포함된 파일은 서버의 `/var` 폴더에 생성됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
