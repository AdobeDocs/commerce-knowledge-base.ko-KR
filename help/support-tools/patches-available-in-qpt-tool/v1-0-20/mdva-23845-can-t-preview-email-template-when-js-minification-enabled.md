---
title: "MDVA-23845: JS 축소가 활성화된 경우 이메일 템플릿을 미리 볼 수 없음"
description: MDVA-23845 Magento 패치는 JS 축소가 활성화된 경우 관리자에서 이메일 템플릿을 미리 볼 수 없을 때 문제를 해결합니다.
exl-id: 08579251-a0aa-4e84-9d6a-3fa2999d9c05
feature: Communications, Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-23845: JS 축소가 활성화된 경우 이메일 템플릿을 미리 볼 수 없음

MDVA-23845 Magento 패치는 JS 축소가 활성화된 경우 관리자에서 이메일 템플릿을 미리 볼 수 없을 때 문제를 해결합니다.

이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-23845입니다. 이 문제는 Magento 버전 2.3.5에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Magento 버전:** Magento Commerce Cloud 2.3.3에 대해 패치가 만들어졌습니다.

**Magento 버전과 호환:** Magento Commerce 및 자석 Commerce Cloud 2.3.2-2.3.4-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. **관리 > 저장소 > 구성 > JavaScript 설정 > JavaScript 파일 축소** = *예*&#x200B;에서 **JS 축소**&#x200B;을(를) 활성화합니다.
1. Magento을 프로덕션 모드로 전환합니다.
1. **관리자 > 마케팅 > 커뮤니케이션 > 이메일 템플릿**(으)로 이동합니다.
1. **새 템플릿 추가** 를 클릭합니다.
1. **새 순서** 템플릿을 선택하십시오.
1. **템플릿 로드** 단추를 클릭합니다.
1. **템플릿 이름**&#x200B;을(를) **새 순서로 채웁니다.**
1. **템플릿 저장** 단추를 클릭합니다.
1. 전자 메일 템플릿 그리드에서 **작업** 열의 **미리 보기** 링크를 클릭합니다.

<u>예상 결과</u>:

이메일 템플릿 미리 보기는 예상대로 열린 팝업 창에 나타납니다.

<u>실제 결과</u>:

이메일 템플릿 미리 보기가 열려 있는 팝업 창에 표시되지 않습니다. 팝업 창이 비어 있고 JS 오류가 표시될 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 Magento 제품에 따라 다음 링크를 사용합니다.

* Magento Commerce: DevDocs [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) .
* Magento Commerce Cloud: DevDocs [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) .

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [품질 패치 도구 관련 Magento 문제에 대한 패치 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
