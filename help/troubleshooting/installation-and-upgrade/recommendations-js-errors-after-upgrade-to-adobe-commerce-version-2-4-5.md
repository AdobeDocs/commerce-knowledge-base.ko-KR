---
title: Adobe Commerce 버전 2.4.5로 업그레이드한 후 [!UICONTROL Recommendations]개의 [!DNL JS] 오류
description: 이 문서에서는 Adobe Commerce(모든 배포 메서드)로 업그레이드한 후 제품 [!UICONTROL Recommendations] 모듈과 관련된 콘솔에 [!DNL JS]개의 오류가 있는 경우에 대한 수정 사항을 제공합니다.
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%
---
# Adobe Commerce 버전 2.4.5로 업그레이드한 후 [!UICONTROL Recommendations]개의 [!DNL JS] 오류

이 문서에서는 Adobe Commerce(모든 배포 메서드)로 업그레이드한 후 제품 [!UICONTROL Recommendations] 모듈/단위와 관련된 콘솔에 [!DNL JS]개의 오류가 있는 경우에 대한 수정 사항을 제공합니다.

현재 향후 버전에서 이 문제를 해결할 계획이 없습니다.

## 영향을 받는 버전 및 제품

* 버전 2.4.5로 업그레이드할 때 Adobe Commerce(모든 배포 방법)

## 문제

Storefront 웹 페이지가 홈 페이지 [!DNL CMS]에서 일부 삭제된 제품 [!UICONTROL Recommendations] 모듈/단위(블록 및/또는 위젯)를 계속 참조하기 때문에 문제가 발생합니다.

<u>재현 단계</u>:

1. Adobe Commerce 2.4.5로 업그레이드하십시오.
1. Storefront 웹 페이지에 액세스합니다.
1. 마우스를 마우스 오른쪽 단추로 클릭하고 **검사**&#x200B;를 선택하여 웹 브라우저에서 웹 검사기를 엽니다.
1. **[!UICONTROL Console]** 탭을 클릭합니다.
1. [!DNL JS] 오류를 검토합니다.

<u>예상 결과</u>:

[!DNL JS] 오류 없이 성공적으로 업그레이드했습니다.

<u>실제 결과</u>:

웹 브라우저 콘솔에 여러 유형의 [!DNL JS] 오류가 표시됩니다.

## 해결 방법

해결 방법으로 페이지에서 사용한 모든 [!UICONTROL Recommendations] 단위를 검토하고 삭제된 단위를 제거할 수 있습니다.
