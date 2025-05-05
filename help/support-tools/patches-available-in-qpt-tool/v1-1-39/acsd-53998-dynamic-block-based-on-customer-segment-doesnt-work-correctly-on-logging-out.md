---
title: 'ACSD-53998: 고객 세그먼트를 기반으로 한 동적 블록이 로그아웃 후 잘못 작동함'
description: ACSD-53998 패치를 적용하여 고객 계정에서 로그아웃한 후 고객 세그먼트를 기반으로 하는 다이내믹 블록이 제대로 작동하지 않는 Adobe Commerce 문제를 해결합니다.
feature: Customers, Page Builder, Personalization
role: Admin, Developer
exl-id: 5a82a6b8-e8f7-47ff-89f6-93a39b72fe38
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-53998: 고객 세그먼트를 기반으로 한 동적 블록은 로그아웃 후 제대로 작동하지 않음

ACSD-53998 패치는 고객 계정에서 로그아웃한 후 고객 세그먼트를 기반으로 하는 동적 블록이 제대로 작동하지 않는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.39가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-53998입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4-p2 - 2.4.4-p6, 2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객 세그먼트를 기반으로 하는 다이내믹 블록은 고객 계정에서 로그아웃한 후 제대로 작동하지 않습니다.

<u>필수 구성 요소</u>:

[!DNL Page Builder] 모듈을 설치하고 사용하도록 설정합니다.

<u>재현 단계</u>:

1. 조건 없이 두 개의 고객 세그먼트를 만듭니다.
1. 각 세그먼트에 대해 두 개의 동적 블록을 만듭니다.
1. 두 개의 동적 블록을 [!DNL Page Builder] 동적 블록으로 포함하는 블록을 만듭니다.
1. 위의 블록을 포함하는 위젯을 만들고 모든 페이지의 바닥글 섹션 아래에 블록이 표시되도록 합니다.
1. 캐시를 지웁니다.
1. 홈 페이지를 엽니다.
1. 고객으로 로그인.
1. 로그아웃.

<u>예상 결과</u>:

로그인 고객을 위해 만든 배너는 게스트 사용자에게 표시되지 않습니다.

<u>실제 결과</u>:

로그인한 고객 세그먼트에 대해 만든 배너는 고객 계정에서 로그아웃한 후에도 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
