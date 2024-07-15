---
title: 'MDVA-34469: 장바구니에 지정된 스토어 코드가 잘못되었습니다.'
description: 'MDVA-34469 패치는 사용자가 스토어 보기를 전환한 후 장바구니에 제품을 추가할 때 다음과 같은 오류 메시지를 받는 문제를 해결합니다. *장바구니에 지정된 스토어 코드가 잘못됨*. 이 패치는 [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-34469입니다. Adobe Commerce 2.4.2에서 문제가 해결되었습니다.'
exl-id: 35d4f120-7fcf-4996-8b23-aca99cfc18ac
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-34469: 장바구니에 지정된 스토어 코드가 잘못되었습니다.

MDVA-34469 패치는 사용자가 스토어 보기를 전환한 후 장바구니에 제품을 추가할 때 다음과 같은 오류 메시지를 받는 문제를 해결합니다. *장바구니에 지정된 스토어 코드가 잘못됨*. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-34469입니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.4.1

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

저장소 보기를 전환할 때 사용자에게 장바구니 쿼리 오류 *&quot;장바구니 &quot;*&#x200B;에 대해 잘못된 저장소 코드가 지정되었습니다.

<u>필수 구성 요소</u>:

* Adobe Commerce 2.4.0.
* 하나의 스토어와 두 개의 스토어 보기가 있는 단일 웹 사이트가 구성됩니다.
* 고객 계정이 생성됩니다.

<u>재현 단계</u>:

1. Adobe Commerce 백엔드는 두 개의 스토어 보기(스토어 코드 포함: 기본값, 초)가 있도록 구성되어 있습니다.
1. 사용자가 기본 스토어 코드를 사용하여 장바구니를 만듭니다.
1. 사용자가 `Store` 요청 헤더의 두 번째 스토어 코드를 사용하여 이 장바구니를 검색하려고 합니다.

<u>예상 결과</u>:

저장소를 전환하여 `Store` 요청 헤더에서 새 코드를 보내면 장바구니가 요청된 저장소에 연결되므로 장바구니가 표시됩니다.

<u>실제 결과</u>:

장바구니 쿼리가 오류를 반환하며 장바구니가 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
