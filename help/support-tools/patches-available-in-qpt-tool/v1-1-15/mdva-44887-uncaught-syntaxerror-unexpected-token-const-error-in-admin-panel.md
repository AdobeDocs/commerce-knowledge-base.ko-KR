---
title: "MDVA-44887: 관리 패널에 'Uncatch SyntaxError: 예기치 않은 토큰 상수' 오류가 발생했습니다."
description: "MDVA-44887 패치는 관리자가 메뉴 옵션을 클릭할 수 없는 문제를 해결합니다. *확인할 수 없는 구문Error: 예기치 않은 토큰 const* 오류가 관리 패널에 표시됩니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-44887입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정될 예정입니다."
exl-id: 66555e66-49d0-4f80-8f77-84ee107ab12e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44887: 관리 패널에 &#39;Uncatch SyntaxError: 예기치 않은 토큰 상수&#39; 오류

MDVA-44887 패치는 관리자가 메뉴 옵션을 클릭할 수 없는 문제를 해결합니다. 다음 *확인할 수 없는 구문 오류: 예기치 않은 토큰 const* 관리 패널에 오류가 표시됩니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15가 설치되어 있습니다. 패치 ID는 MDVA-44887입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자가 메뉴 옵션을 클릭할 수 없습니다. 다음 *확인할 수 없는 구문 오류: 예기치 않은 토큰 const* 관리 패널에 오류가 표시됩니다.

<u>재현 단계</u>:

1. JS 번들링을 활성화합니다.
1. JS 파일을 축소합니다.
1. Commerce 관리 패널에 로그인합니다.

<u>예상 결과</u>:

관리자가 메뉴 옵션을 클릭할 수 없습니다. 브라우저 콘솔에 오류가 있습니다. *확인할 수 없는 구문 오류: 예기치 않은 토큰 const*.

<u>실제 결과</u>:

관리자 패널은 관리자가 액세스할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
