---
title: 'MDVA-44887: 관리 패널에 ''Uncatch SyntaxError: 예기치 않은 토큰 상수'' 오류'
description: 'MDVA-44887 패치는 관리자가 메뉴 옵션을 클릭할 수 없는 문제를 해결합니다. *확인할 수 없는 구문Error: 예기치 않은 토큰 const* 오류가 관리 패널에 표시됩니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-44887입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.'
exl-id: 66555e66-49d0-4f80-8f77-84ee107ab12e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44887: 관리 패널에 &#39;Uncatch SyntaxError: 예기치 않은 토큰 상수&#39; 오류

MDVA-44887 패치는 관리자가 메뉴 옵션을 클릭할 수 없는 문제를 해결합니다. *확인할 수 없는 SyntaxError: 예기치 않은 토큰 const* 오류가 [관리] 패널에 표시됩니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-44887입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자가 메뉴 옵션을 클릭할 수 없습니다. *확인할 수 없는 SyntaxError: 예기치 않은 토큰 const* 오류가 [관리] 패널에 표시됩니다.

<u>재현 단계</u>:

1. JS 번들링을 활성화합니다.
1. JS 파일을 축소합니다.
1. Commerce 관리 패널에 로그인합니다.

<u>예상 결과</u>:

관리자가 메뉴 옵션을 클릭할 수 없습니다. 브라우저 콘솔에 오류가 있습니다. *확인할 수 없는 구문오류: 예기치 않은 토큰 상수*.

<u>실제 결과</u>:

관리자 패널은 관리자가 액세스할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하십시오.
