---
title: "ACSD-54060: 제한된 관리자는 다른 제품의 하위 항목인 경우 제품을 저장할 수 없습니다."
description: ACSD-54060 패치를 적용하여 제한된 관리자가 다른 범위에 할당된 다른 제품의 하위 항목인 경우 제품을 저장할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: Admin Workspace, Roles/Permissions, Products
role: Admin, Developer
exl-id: 28fa3c99-f2b6-4c6d-955a-bd6638a1b077
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54060: 제한된 관리자는 다른 제품의 하위 항목인 경우 제품을 저장할 수 없습니다.

ACSD-54060 패치는 제한된 관리자가 다른 범위에 할당된 다른 제품의 하위 항목인 경우 제품을 저장할 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-54060입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다른 범위에 할당된 다른 제품의 하위 항목인 경우 제한된 관리자가 제품을 저장할 수 없습니다.

<u>재현 단계</u>:

1. 추가 웹 사이트를 만듭니다.
1. 간단한 제품을 만들어 두 웹 사이트에 할당합니다.
1. 간단한 제품을 유일한 변형으로 사용하여 구성 가능한 제품을 만들고 구성 가능한 제품을 기본 웹 사이트에만 할당합니다.
1. 두 번째 웹 사이트에만 액세스할 수 있는 제한된 관리자 사용자를 만듭니다.
1. 제한된 관리자로 로그인합니다.
1. 두 번째 웹 사이트 범위에서 간단한 제품 이름을 변경해 보십시오.

<u>예상 결과</u>:

제한된 관리자는 제품 이름을 변경할 수 있습니다.

<u>실제 결과</u>:

오류가 발생했습니다. *이 항목을 보려면 더 많은 권한이 필요합니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
