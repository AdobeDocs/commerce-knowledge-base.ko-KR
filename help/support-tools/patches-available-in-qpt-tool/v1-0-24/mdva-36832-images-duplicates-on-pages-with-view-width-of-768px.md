---
title: 'MDVA-36832: 보기 너비가 768px인 페이지에서 이미지가 중복됨'
description: MDVA-36832 패치는 보기 너비가 768px인 페이지에서 이미지가 중복되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-36832입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 3eb0c11b-d93a-4676-afd1-8f6592c6cd6d
feature: Configuration, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-36832: 보기 너비가 768px인 페이지에서 이미지가 중복됨

MDVA-36832 패치는 보기 너비가 768px인 페이지에서 이미지가 중복되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-36832입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전용 패치가 만들어졌습니다.** 클라우드 인프라 2.3.5-p2의 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

보기 너비가 768px인 페이지에서 이미지가 중복됩니다.

<u>재현 단계:</u>

1. 백엔드 > 컨텐츠 > 페이지로 이동하여 페이지를 편집합니다.
1. 페이지에 이미지를 추가합니다.
1. 프론트엔드로 이동하여 편집된 페이지를 엽니다.
1. Chrome에서 개발자 도구를 엽니다.
1. &quot;장치 보기&quot;를 활성화하고 iPad 보기를 선택하거나 페이지 너비를 768px로 설정합니다.

<u>실제 결과:</u>

이미지가 복제됩니다.

<u>예상 결과:</u>

추가된 이미지는 페이지에 하나만 표시되어야 합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
