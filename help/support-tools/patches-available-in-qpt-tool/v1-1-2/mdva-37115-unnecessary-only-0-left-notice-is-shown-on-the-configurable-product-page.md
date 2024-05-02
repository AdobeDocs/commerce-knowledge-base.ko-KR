---
title: 'MDVA-37115: 제품 페이지에 "0개만 남음" 알림이 표시됨'
description: MDVA-37115 패치는 구성 가능한 제품 페이지에 불필요하게 *0개만 남아* 표시되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37115입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.
exl-id: 08aa6ac7-13ae-44c1-9db4-d449c3d8c985
feature: Configuration, Products, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# MDVA-37115: 제품 페이지에 &quot;0개만 남음&quot; 알림이 표시됨

MDVA-37115 패치는 불필요한 문제를 해결합니다. *0개만 남음* 알림은 구성 가능한 제품 페이지에 표시됩니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치되었습니다. 패치 ID는 MDVA-37115입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 유형) 2.4.2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 유형) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

불필요한 항목 *0개만 남음* 알림은 구성 가능한 제품 페이지에 표시됩니다.

<u>전제 조건</u>:

인벤토리 모듈이 설치되어 있습니다.

<u>재현 단계</u>:

1. 몇 가지 옵션을 사용하여 구성 가능한 제품을 만듭니다.
1. 프론트엔드로 가세요
1. 구성 가능한 제품 페이지를 열고 옵션을 선택합니다.

<u>예상 결과</u>:

아니요 *0개만 남음* 알림은 제품 페이지에 표시됩니다.

<u>실제 결과</u>:

*0개만 남음* 알림은 제품 페이지에 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 유형에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션.
