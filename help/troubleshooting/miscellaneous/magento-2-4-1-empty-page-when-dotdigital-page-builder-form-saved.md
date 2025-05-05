---
title: 'Adobe Commerce 2.4.1: dotdigital Page Builder 양식을 저장할 때 빈 페이지가 표시됨'
description: 이 문서에서는 Safari 브라우저를 사용할 때 관리 패널에서 Dotdigital Page Builder 양식을 저장한 후 빈 웹 페이지를 표시하는 Adobe Commerce 2.4.1의 알려진 문제에 대한 해결 방법을 제공합니다.
exl-id: 682eac73-1ad2-4093-acfb-6a8da4c05cf5
feature: Page Builder
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: dotdigital Page Builder 양식이 저장될 때 빈 페이지가 표시됨

이 문서에서는 Safari 브라우저를 사용할 때 관리 패널에서 Dotdigital Page Builder 양식을 저장한 후 빈 웹 페이지를 표시하는 Adobe Commerce 2.4.1의 알려진 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.1
* 클라우드 인프라의 Adobe Commerce 2.4.1

## 문제

<u>재현 단계</u>

1. **관리 패널** > **콘텐츠** > **페이지**(으)로 이동한 다음 모든 페이지에서 **편집**&#x200B;을 선택합니다.
1. **콘텐츠**(으)로 이동한 다음 **페이지 빌더로 편집** 단추를 클릭합니다.
1. **dotdigital 양식** 블록을 드래그하고 **편집**&#x200B;을 선택합니다.
1. 테스트 양식 중 하나를 선택한 다음 **임베드됨** 모드를 선택하고 양식을 저장하십시오.
1. 페이지 수정 사항을 저장합니다.

<u>예상 결과:</u>

웹 페이지를 저장해야 합니다.

<u>실제 결과:</u>

웹 페이지가 비어 있습니다. 웹 페이지를 다시 로드하면 변경 사항이 적용됩니다.

## 해결 방법

해결 방법은 Safari에 대한 대체 브라우저를 사용하는 것입니다. 이 문제는 2021년 1분기, 다음 릴리스인 Adobe Commerce 2.4.2에서 수정될 예정입니다.

## 관련 읽기

* [페이지 빌더란 무엇입니까?개발자 설명서에서 ](https://developer.adobe.com/commerce/frontend-core/page-builder/).
* 개발자 설명서에서 [페이지 빌더 설정](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html?lang=ko)을 참조하십시오.
* 사용 안내서의 [페이지 빌더](https://experienceleague.adobe.com/ko/docs/commerce-admin/page-builder/introduction).
* 사용 안내서의 [페이지 빌더 - 요소](https://experienceleague.adobe.com/ko/docs/commerce-admin/page-builder/workspace#elements).
