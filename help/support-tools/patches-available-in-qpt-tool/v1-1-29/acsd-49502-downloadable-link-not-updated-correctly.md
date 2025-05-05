---
title: 'ACSD-49502: 다운로드 가능한 링크가  [!DNL staging] 업데이트 후에 올바르게 업데이트되지 않음'
description: ACSD-49502 패치를 적용하여 다운로드 가능한 제품에  [!DNL staging] 업데이트가 적용된 후 다운로드 가능한 링크가 올바르게 업데이트되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 9e7f0c06-4b7d-42c4-8ec7-cdeefd7e8a08
feature: Staging
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-49502: [!DNL staging] 업데이트 후 다운로드 가능한 링크가 올바르게 업데이트되지 않음

ACSD-49502 패치는 다운로드 가능한 제품에 [!DNL staging] 업데이트가 적용된 후 다운로드 가능한 링크가 올바르게 업데이트되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-49502입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL staging] 업데이트가 다운로드 가능한 제품에 적용된 후에는 다운로드 가능한 링크가 제대로 업데이트되지 않습니다.

<u>재현 단계</u>:

1. 링크를 사용하여 다운로드 가능한 제품을 만듭니다.
1. 고객 계정을 만들고 로그인합니다.
1. 상점 앞에서 다운로드 가능한 제품을 장바구니에 추가합니다.
1. **[!UICONTROL Admin]**&#x200B;에서 다운로드 가능한 제품에 대한 새 업데이트를 예약하고 예약된 업데이트를 완료하도록 합니다.
1. 상점 앞에서 주문을 완료하십시오.

<u>예상 결과</u>:

이전에 추가한 제품이 장바구니에 있는 동안 예약된 업데이트를 사용할 때 다운로드 가능한 링크는 유지됩니다.

<u>실제 결과</u>:

다운로드 가능한 링크가 고객의 *[!UICONTROL My Account]*([!UICONTROL My Downloadable Products]) 및 **[!UICONTROL Admin]**&#x200B;의 주문 보기 페이지 모두에 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
