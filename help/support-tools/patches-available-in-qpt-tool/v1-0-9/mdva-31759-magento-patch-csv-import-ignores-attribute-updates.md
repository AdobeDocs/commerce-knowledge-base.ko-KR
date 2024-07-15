---
title: 'MDVA-31759 패치: CSV 가져오기는 특성 업데이트를 무시합니다.'
description: MDVA-31759 패치는 CSV 가져오기로 *드롭다운* 및 *텍스트 영역* 유형이 있는 추가 속성이 무시되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9가 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 5426866c-893f-4abe-bfbc-6e7b30dd8dab
feature: Attributes, Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-31759 패치: CSV 가져오기는 특성 업데이트를 무시합니다.

MDVA-31759 패치는 CSV 가져오기에서 *드롭다운* 및 *텍스트 영역* 형식의 추가 특성을 무시하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.4.0

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

CSV 가져오기는 *드롭다운* 및 *텍스트 영역* 형식의 추가 특성을 무시합니다.

<u>재현 단계</u>:

1. Commerce 관리자에 로그인합니다.
1. 다음 구성으로 제품 속성을 만듭니다.
   * **기본 레이블**: *G003*
   * **저장소 소유자의 카탈로그 입력 형식**: *텍스트 영역* 또는 *드롭다운*
   * **특성 코드**: *G003*
   * **범위**: *전역*
1. 위의 속성을 기본 속성 집합에 추가합니다.
1. 기본 속성이 설정된 제품을 만들고 새 속성의 값을 지정합니다.
1. 제품을 CSV로 내보냅니다.
1. **additional\_attributes** 열의 특성 값을 업데이트합니다.
1. 업데이트된 CSV를 가져옵니다.

<u>예상 결과</u>:

G003 속성 값이 업데이트됩니다.

<u>실제 결과</u>:

G003 속성 값이 업데이트되지 않았습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
