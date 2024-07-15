---
title: 'MDVA-31343 패치: 일정 업데이트는 범주에 대한 본문 클래스를 제거합니다.'
description: MDVA-31343 패치는 범주의 할당된 레이아웃 본문 CSS 클래스가 예약된 업데이트 중에 제거되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 수정될 예정입니다.
exl-id: 50dbff01-cb77-4cac-b90e-5c4b06f5e4e7
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-31343 패치: 예약 업데이트는 범주에 대한 본문 클래스를 제거합니다.

MDVA-31343 패치는 범주의 할당된 레이아웃 본문 CSS 클래스가 예약된 업데이트 중에 제거되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 수정될 예정입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.5-p2

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

예약된 업데이트 후 레이아웃 본문 클래스가 범주에서 제거됩니다.

<u>재현 단계</u>:

1. Commerce 관리자에서 카테고리를 만듭니다.
1. **디자인** 섹션에서 **레이아웃** = *범주 — 전체 너비*&#x200B;를 설정합니다.
1. 범주를 저장합니다.
1. 카테고리 프론트엔드 페이지로 이동합니다. 페이지 소스 알림에서

   ```css
   page-layout-category-full-width
   ```

   CSS 클래스입니다.
1. **카탈로그** > **범주**&#x200B;에서 새 범주에 대한 *예약된 변경 내용* 섹션에서 **새 업데이트 예약**&#x200B;을 클릭합니다.
1. 예약된 업데이트가 시작될 때까지 기다렸다가 cron 을 실행하고 캐시를 플러시합니다.
1. 프론트엔드의 카테고리 페이지로 이동하여 페이지 소스를 검사합니다.

<u>예상 결과</u>:

페이지 본문에서

```css
page-layout-category-full-width
```

CSS 클래스입니다.

<u>실제 결과</u>:

페이지 본문에서

```css
page-layout-2columns-left
```

CSS 클래스: 카테고리 페이지의 기본값입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
