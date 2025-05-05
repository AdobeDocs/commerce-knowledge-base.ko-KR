---
title: 'MDVA-38666: 관리자가 구성 가능한 제품 옵션을 변경할 수 없음'
description: MDVA-38666 패치는 관리자가 고객 장바구니에서 구성 가능한 제품 옵션을 변경할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38666입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: 72440e47-1deb-41da-a225-d4bc73029ad5
feature: Admin Workspace, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-38666: 관리자가 구성 가능한 제품 옵션을 변경할 수 없음

MDVA-38666 패치는 관리자가 고객 장바구니에서 구성 가능한 제품 옵션을 변경할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-38666입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.3.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자가 고객 장바구니에서 구성 가능한 제품 옵션을 변경할 수 없습니다.

<u>재현 단계</u>:

1. 고객 계정 범위를 글로벌로 설정합니다.
1. 스토어를 사용하여 웹 사이트 두 개를 만듭니다.
1. 구성 가능한 두 제품을 만들어 각 웹 사이트에 할당합니다.
1. 프론트엔드에 고객 계정을 만들고 로그인합니다.
1. 장바구니에 제품을 추가하고 체크아웃을 수행합니다(이 작업은 각 웹 사이트에서 견적 ID를 다르게 만들기 위해 수행됨).
1. 장바구니에 제품을 추가하고 둡니다.
1. 두 번째 웹 사이트로 전환하여 제품을 장바구니에 추가합니다(고객 계정 범위가 글로컬로 설정되어 있으므로 동일한 로그인이 작동해야 함).
1. 관리자에서 고객을 열고 장바구니 탭으로 이동합니다.
1. 드롭다운에서 스토어를 전환하고 구성을 변경해 보십시오.

<u>예상 결과</u>:

사용자가 구성 가능한 옵션이 있는 팝업을 가져옵니다.

<u>실제 결과</u>:

팝업 양식이 표시되지 않습니다. 구성을 변경할 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
