---
title: 'MDVA-42269: 관리자 사용자가 "TypeError" 오류로 인해 Admin에 로그인할 수 없음'
description: MDVA-42269 패치는 관리자 사용자가 TypeError로 인해 관리자에 로그인할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11이 설치된 경우 사용할 수 있습니다.  패치 ID는 MDVA-42269입니다.  최신 패치 업데이트는 QPT 1.1.15에 있습니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: 66d744a2-054e-493c-a060-9ed78447e35b
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-42269: &quot;TypeError&quot; 오류로 인해 관리자가 Admin에 로그인할 수 없음

MDVA-42269 패치는 관리자 사용자가 TypeError로 인해 관리자에 로그인할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11이 설치된 경우에 사용할 수 있습니다.  패치 ID는 MDVA-42269입니다.  최신 패치 업데이트는 QPT 1.1.15에 있습니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1, 2.3.7-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1 - 2.4.3-p2, 2.3.7-p3

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음 오류로 인해 관리자 사용자가 관리자에 로그인할 수 없습니다. *TypeError: strtotime() 매개 변수 1은 문자열이어야 하고 null이 주어져야 합니다.*

<u>재현 단계</u>:

Commerce 관리자에 로그인합니다.

<u>예상 결과</u>:

관리자는 올바른 사용자 이름과 암호로 로그인할 수 있습니다.

<u>실제 결과</u>:

관리자가 로그인할 수 없습니다. 다음 오류가 기록됩니다. *TypeError: strtotime() 매개 변수 1은 문자열이어야 하며 null이 주어져야 합니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
