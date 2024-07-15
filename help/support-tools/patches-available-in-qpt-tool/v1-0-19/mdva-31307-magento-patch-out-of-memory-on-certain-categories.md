---
title: 'MDVA-31307: 특정 범주의 메모리가 부족합니다.'
description: MDVA-31307 패치는 'Magento\_Csp/모델/블록 캐시'가 많은 메모리를 사용하고 엄청난 양의 캐시된 문자열을 생성하여 스크립트와 스타일이 동적으로 많이 화이트리스트에 추가되는 특정 페이지에 문제를 발생시키는 문제를 해결합니다. 제공된 패치는 이 프로세스를 최적화합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-31307입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 15d82f5b-bd43-4a0a-b756-d109dac6d2cd
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-31307: 특정 범주에 메모리가 부족합니다.

MDVA-31307 패치는 `Magento\_Csp/Model/BlockCache`에서 많은 메모리를 사용하고 캐시된 문자열이 대량으로 생성되는 문제를 해결합니다. 이 경우 스크립트와 스타일을 동적으로 화이트리스트에 많이 추가하는 특정 페이지에 문제가 발생합니다. 제공된 패치는 이 프로세스를 최적화합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-31307입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전용 패치가 생성되었습니다.** 클라우드 인프라 2.4.0의 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

캐시된 블록에 대한 동적 CSP 허용 목록에 문제가 있어 특정 범주에 *메모리 부족* 오류가 발생하는 문제를 해결합니다.

<u>재현 단계:</u>

1. 작은 프로필 고정장치(`bin/magento setup:performance:generate-fixtures`)를 생성합니다.
1. 다른 탭에서 모든 범주 페이지를 엽니다.

<u>실제 결과:</u>

*[날짜 및 시간] PHP 치명적 오류: 0행에 있는 알 수 없음에서 1073741824바이트의 허용된 메모리 크기(90112바이트를 할당하려고 함)를 모두 사용했습니다.
[날짜 및 시간] PHP 치명적 오류: 31*&#x200B;행의 /app/`<project-id>`/vendor/magento/module-csp/Model/Collector/DynamicCollector.php에서 1073741824바이트의 허용된 메모리 크기(33554440바이트를 할당하려고 함)를 사용함

<u>예상 결과:</u>

모든 페이지가 올바르게 열렸습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
