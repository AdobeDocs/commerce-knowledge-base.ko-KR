---
title: 'ACSD-50116: 관리자는 레벨 3 이하의 하위 범주에 대한 URL 다시 작성을 만들 수 없습니다'
description: ACSD-50116 패치를 적용하여 관리자가 레벨 3 이하의 하위 범주에 대한 URL 재작성을 만들 수 없는 Adobe Commerce 문제를 해결합니다.
exl-id: 3fa8ebc1-b55d-437e-9dc7-bf6c300b9bbe
feature: Admin Workspace, Categories
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-50116: 관리자는 레벨 3 이하의 하위 범주에 대한 URL 다시 작성을 만들 수 없습니다

ACSD-50116 패치는 관리자가 수준 3 이하의 하위 범주에 대한 URL 다시 쓰기를 만들 수 없는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-50116입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

관리자는 레벨 3 이하의 하위 범주에 대한 URL 재작성을 만들 수 없습니다.

<u>재현 단계</u>:

1. 세 개 이상의 하위 범주 수준이 있는 범주 트리를 만듭니다.
1. *[!UICONTROL For Product]* 및 *[!UICONTROL For Category]* 옵션을 모두 사용하여 수준 4 범주에 대한 *[!UICONTROL URL Rewrite]*&#x200B;을(를) 만들어 보세요.

<u>예상 결과</u>:

범주 트리에는 레벨 4 이하의 하위 범주가 표시됩니다.

<u>실제 결과</u>:

범주 트리에는 최대 레벨 3개의 하위 범주만 표시됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
