---
title: '[!DNL Live Search] 패싯이 알파벳순으로 정렬되지 않음'
description: 이 문서에서는  [!DNL Live Search] 패싯이 알파벳순으로 정렬되지 않은 경우의 문제 해결 정보를 제공합니다.
feature: Admin Workspace, Categories, Search
role: Developer
source-git-commit: b20a98e44cfad6667b9fe0ab232b0020ed834ca2
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# [!DNL Live Search] 패싯이 알파벳순으로 정렬되지 않음

## 영향을 받는 제품 및 버전

Adobe Commerce 버전 2.4.x 이상

## 문제

모든 Adobe Commerce 상점 첫 번째 패싯은 해당 속성에 할당된 입력 유형에 관계없이 단일 선택 옵션을 사용하여 알파벳순으로 정렬됩니다.

## 해결 방법

그러나 특정 경계 사례에서는 패싯이 [[!DNL Live Search] 페이스팅 작업 영역](https://experienceleague.adobe.com/ko/docs/commerce-merchant-services/live-search/live-search-admin/facets/faceting-workspace)에 설정된 대로 알파벳순으로 정렬되지 않을 수 있습니다.

해결 방법으로 [!UICONTROL Admin] 특성 섹션에서 제품 특성을 정렬할 수 있습니다.

1. **[!UICONTROL Admin]** 사이드바에서 **스토어** > *특성* > **제품**(으)로 이동합니다.
1. 테이블에서 속성을 선택합니다.

   ![특성 목록](assets/attribute-list.png)

1. 정렬할 값이 있는 특성을 열고 **특성 정보** > **속성**&#x200B;을 선택합니다.
1. **옵션 관리**&#x200B;에서 특성 값을 정렬할 수 있습니다.

   ![특성 정렬](assets/sort-attributes.png)
