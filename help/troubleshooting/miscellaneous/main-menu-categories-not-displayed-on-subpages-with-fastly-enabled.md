---
title: Fastly가 활성화된 하위 페이지에 메인 메뉴(카테고리)가 표시되지 않음
description: '이 문서에서는 Fastly 또는 Vannish가 활성화된 경우 기본 메뉴(또는 사용자 안내서의 [카테고리 상단 탐색 메뉴](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html))가 하위 페이지(예: *블로그/페이지*)의 상점 앞에 표시되지 않는 경우에 대한 수정 사항을 제공합니다.'
exl-id: 7c54791d-8aa6-4f01-a28b-a7aecdb8ff74
feature: Categories, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Fastly가 활성화된 하위 페이지에 메인 메뉴(카테고리)가 표시되지 않음

이 문서에서는 Fastly 또는 Vannish가 활성화된 경우 기본 메뉴(또는 사용자 안내서의 [카테고리 상단 탐색 메뉴](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html))가 하위 페이지(예: *블로그/페이지*)의 상점 앞에 표시되지 않는 경우에 대한 수정 사항을 제공합니다.

**원인:** 페이지의 *URL 키* 매개 변수(검색 엔진 최적화 설정)에 허용되지 않는 `/` 문자(슬래시)가 있습니다. *URL 키*(예: *page\_name* 대신 *blog/page\_name*) 대신 *URL 경로*(전체 페이지 위치 포함)를 잘못 지정하면 문자가 추가됩니다.

**해결 방법:** `/` 문자(슬래시)를 제거합니다. *URL 키* 매개 변수에는 페이지 이름만 지정하십시오.

## 영향을 받는 버전

* Adobe Commerce 온-프레미스 2.X.X
* 클라우드 인프라의 Adobe Commerce 2.X.X
* fastly 또는 Vanish

## 문제

Fastly 또는 기타 바니시 기반 서비스를 사용하는 경우 기본 메뉴(사용자 안내서에서는 [범주 위쪽 탐색 메뉴](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html)라고도 함)가 하위 페이지의 상점 앞에 표시되지 않습니다.

## 원인

이 문제는 *URL 키* 매개 변수(검색 엔진 최적화 설정)에 추가된 허용되지 않는 `/` 문자(슬래시)로 인해 발생합니다.

일반적으로 *URL 경로*(전체 페이지 위치와 함께, 페이지의 상위 리소스/디렉터리 포함)이 *URL 키* 대신 잘못 지정되면 문자가 추가됩니다(예: *page\_name* 대신 *blog/page\_name*).

![SEO 설정에 대한 URL 키 매개 변수](assets/seo_url_key.png)

## 솔루션

저장소의 모든 페이지에 대한 *URL 키* 매개 변수에서 `/` 문자(슬래시)를 제거합니다.

즉, *URL 경로* 대신 *URL 키*&#x200B;를 사용하십시오. 상위 리소스/디렉터리가 없는 페이지 이름만 언급하십시오.

### 페이지 계층 구조 및 SEO의 Recommendations

페이지 계층을 설정하려면 [페이지 편집] 메뉴의 **계층** 섹션을 사용하십시오.

![계층 설정](assets/hierarchy_hr.png)

또한 보다 복잡한 계층 솔루션의 경우 **콘텐츠** > **요소** > **계층** 메뉴를 사용할 수 있습니다.

제품 페이지에서 SEO 용도로 사용하려면 URL 다시 쓰기(**마케팅** > **SEO 및 검색** > **URL 다시 쓰기**)를 사용하십시오.

## 추가 정보는 사용 안내서를 참조하십시오

SEO의 *URL 키* 매개 변수:

* [검색 엔진 최적화](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [새 페이지 추가](/docs/commerce-admin/content-design/elements/pages/page-add.html)

페이지 계층 구조:

* [개요](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [노드 추가](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
