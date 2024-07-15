---
title: "MDVA-33614 패치: 용어 페이지를 저장할 수 없음"
description: 'MDVA-33614 패치는 페이지 빌더에서 다음 오류가 발생하여 용어 페이지에 대한 편집 내용을 저장할 수 없는 문제를 해결했습니다. *페이지 빌더를 시작하는 동안 오류가 발생했습니다. 기술 지원 담당자에게 문의하십시오*. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-33614입니다. Adobe Commerce 2.4.2에서 문제가 해결되었습니다.'
exl-id: d9b287bb-eab4-4c33-b725-ae0074962447
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-33614 패치: 용어 페이지를 저장할 수 없음

MDVA-33614 패치는 페이지 빌더에서 다음 오류가 발생하여 용어 페이지에 대한 편집 내용을 저장할 수 없는 문제를 해결했습니다. *페이지 빌더를 시작하는 동안 오류가 발생했습니다. 기술 지원 문의*&#x200B;에게 문의하십시오. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-33614입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전용 패치가 만들어졌습니다.** 클라우드 인프라 2.4.1의 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

페이지 빌더에 오류가 발생하여 용어 페이지에 대한 편집 내용을 저장할 수 없습니다.

<u>재현 단계</u>:

1. Commerce 관리에서 **컨텐츠** > 요소 > **페이지**(으)로 이동합니다.
1. 용어 페이지를 선택합니다.
1. **편집**&#x200B;을 클릭합니다.
1. 편집하고 **저장**&#x200B;을 클릭하세요.

<u>예상 결과</u>:

페이지가 오류 없이 저장됩니다.

<u>실제 결과</u>:

다음 오류가 표시됩니다. *페이지 빌더를 시작하는 동안 오류가 발생했습니다. 기술 지원 문의*&#x200B;에게 문의하십시오.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
