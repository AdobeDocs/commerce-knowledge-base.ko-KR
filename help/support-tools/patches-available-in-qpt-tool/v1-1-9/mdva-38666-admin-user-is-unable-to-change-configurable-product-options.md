---
title: 'MDVA-38666: 관리자가 구성 가능한 제품 옵션을 변경할 수 없음'
description: MDVA-38666 패치는 관리자가 고객 장바구니에서 구성 가능한 제품 옵션을 변경할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38666입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: 72440e47-1deb-41da-a225-d4bc73029ad5
feature: Admin Workspace, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-38666: 관리자가 구성 가능한 제품 옵션을 변경할 수 없음

MDVA-38666 패치는 관리자가 고객 장바구니에서 구성 가능한 제품 옵션을 변경할 수 없는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9가 설치되었습니다. 패치 ID는 MDVA-38666입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.3.4-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

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

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
