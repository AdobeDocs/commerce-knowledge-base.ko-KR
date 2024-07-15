---
title: 'MDVA-38468: CMS 페이지를 저장할 때 오류 메시지 수신'
description: 'MDVA-38468 Adobe Commerce 패치는 CMS 페이지를 저장할 때 사용자에게 오류 메시지: *ID가 "PAGE_ID"인 항목이 이미 있음*이 표시되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38468입니다. Adobe Commerce 2.3.6에서 문제가 해결되었습니다.'
exl-id: 7fe80308-50b7-4786-a43c-cce607eb606c
feature: CMS, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-38468: CMS 페이지를 저장할 때 오류 메시지가 표시됨

MDVA-38468 Adobe Commerce 패치를 사용하면 CMS 페이지를 저장할 때 다음과 같은 오류 메시지가 표시되는 문제가 해결됩니다. *ID가 &quot;PAGE_ID&quot;인 항목이 이미 있습니다.*. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-38468입니다. 이 문제는 Adobe Commerce 2.3.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
클라우드 인프라의 Adobe Commerce 2.3.2-p2

**Adobe Commerce 버전과 호환:**
Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.2-2.3.5-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

CMS 페이지를 저장하려고 할 때 다음과 같은 오류 메시지가 표시됩니다. *ID가 &quot;PAGE_ID&quot;인 항목이 이미 있습니다.*

<u>재현 단계</u>:

1. 새 웹 사이트 + 스토어 + 스토어를 만듭니다.
1. 웹 사이트 + 스토어 + 스토어를 하나 더 만듭니다.
1. **콘텐츠** > **계층 구조** > 계층 구조 트리에 기존 CMS 페이지 추가 로 이동합니다.
1. **콘텐츠** > **페이지** > **새 페이지 추가**(으)로 이동:
   * 제목을 추가합니다.
   * 웹 사이트의 페이지에서 생성된 두 스토어에 지정합니다.
   * 계층 섹션에서 모든 범주에 할당합니다.
   * **저장하고 계속 편집**.

<u>예상 결과</u>:

페이지가 오류 없이 저장됩니다.

<u>실제 결과</u>:

페이지가 저장되었지만 다음과 같은 오류 메시지가 표시됩니다. *동일한 ID &quot;PAGE_ID&quot;를 가진 항목(Magento\VersionsCms\Model\Hierarchy\Node)이 이미 있습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
