---
title: 'MDVA-36853: 대형 미디어 갤러리에서 이미지가 로드되지 않음'
description: MDVA-36853 패치는 큰 미디어 디렉터리가 있을 때 페이지 빌더 미디어 갤러리 위젯이 로드되지 않으므로 이미지가 로드되지 않을 때 문제를 수정합니다.
exl-id: 64e089d9-d443-4aa7-8e04-a3598b05958d
feature: CMS, Cache, Media
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-36853: 대형 미디어 갤러리에서 이미지가 로드되지 않음

MDVA-36853 패치는 큰 미디어 디렉터리가 있을 때 페이지 빌더 미디어 갤러리 위젯이 로드되지 않으므로 이미지가 로드되지 않을 때 문제를 수정합니다.

이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-36853입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전용 패치가 만들어졌습니다.** 클라우드 인프라 2.4.2의 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. **관리 > 저장소 > 구성 > 고급 > 시스템 > 미디어 갤러리**&#x200B;에서 **이전 미디어 갤러리 사용** = *예*&#x200B;을(를) 설정합니다.
1. **콘텐츠 > 블록**(으)로 이동하여 새 CMS 블록을 만들거나 기존 CMS 블록을 편집하십시오.
1. **Edit with Pagebuilder** 단추를 클릭합니다.
1. 미디어 요소를 추가합니다.
1. **갤러리에서 선택** 단추를 클릭합니다.

<u>예상 결과</u>:

미디어 갤러리 위젯 및 미디어 갤러리 이미지가 예상대로 로드됩니다.

<u>실제 결과</u>:

`pub/media/catalog/product/cache/` 디렉터리가 큰 경우 미디어 갤러리 위젯과 미디어 갤러리 이미지가 모두 로드되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 다음 링크를 사용하십시오.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
