---
title: 모든 Adobe Commerce 버전에서 Google 맵 액세스 손실에 대한 패치를 수정했습니다.
description: '이 문서는 3.54+의 최신  [!DNL Google Maps] 버전과 호환되지 않는 Adobe Commerce 가맹점에 대한 수정 사항을 제공합니다.'
feature: Install, Upgrade
role: Developer
source-git-commit: cf235c2fdd7a36d7e3b126de35c51e6711cd3845
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# 모든 Adobe Commerce 버전에서 [!DNL Google Maps] 액세스 손실에 대한 패치를 수정했습니다.

이 문서에서는 3.54+의 최신 [!DNL Google Maps] 버전과 호환되지 않는 Adobe Commerce 판매자에 대한 수정 사항을 제공합니다. 이 수정 사항은 Adobe Commerce 판매자가 더 이상 Adobe Commerce 버전의 [!DNL Google Maps]에 액세스할 수 없는 문제를 해결하기 위한 것입니다.

## 영향을 받는 버전 및 제품

* Adobe Commerce 및/또는 기타 사용된 기술의 버전.
* Cloud 및 온-프레미스 버전의 Adobe Commerce *2.4.4* - *2.4.7*.

## 문제

*2024년 6월 14일*&#x200B;에 [!DNL Google Maps] 버전 *3.53*&#x200B;이(가) 수명이 종료되었으며 [!DNL Google]에 의해 해제되었습니다.

자세한 내용은 [[!DNL Google Maps Platform: Maps JavaScript API]](https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions)을(를) 참조하세요.

Adobe Commerce은 3.54+의 최신 [!DNL  Google Maps] 버전과 호환되지 않습니다.

호환되지 않는 이유는 레거시 `prototype.js script`이(가) `lib/web/legacy-build.min.js`을(를) 통해 로드되어 네이티브 Array.from 함수를 재정의했기 때문입니다. 재정의하면 [!DNL  Google Maps] API와 직접적으로 충돌합니다.

[[!DNL Google Maps: JS Best Practices]](https://developers.google.com/maps/documentation/javascript/best-practices)을(를) 참조하세요.

<u>재현 단계</u>:

1. **[!UICONTROL Content]** > **[!UICONTROL Pages]** > 을(를) 클릭하고 **[!UICONTROL New Page]**&#x200B;을(를) 선택합니다.
1. 콘텐츠 블록을 확장하고 **[!DNL PageBuilder]** 편집 단추를 클릭합니다.
1. **[!DNL PageBuilder]** 메뉴에서 [콘텐츠 블록 매핑]을 페이지로 끕니다.

<u>예상 결과:</u>

[!DNL Google Maps]이(가) 예상대로 작동해야 합니다.

<u> 실제 결과:</u>

**[!DNL PageBuilder]** 메뉴에서 페이지로 맵 콘텐츠 블록을 끌어 놓을 때 *&quot;죄송합니다! 문제가 발생했습니다.&quot;*&quot;이(가) 표시됩니다.

## 솔루션

* 패치 버전 2.4.4, 2.4.5, 2.4.6 또는 2.4.7의 모든 판매자는 해당 패치를 해당 버전에 적용해야 합니다.

## 패치

Adobe Commerce 버전에 따라 다음과 같은 첨부 패치를 사용합니다.

**버전 2.4.4의 경우:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**버전 2.4.5의 경우:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**버전 2.4.6의 경우:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**버전 2.4.7의 경우:**
[ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**참고**

이 문제는 8월 보안 전용 패치 릴리스의 범위에서 영구적으로 수정됩니다.
2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10

## 관련 읽기

[Adobe에서 제공하는 작성기 패치를 적용하는 방법](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)