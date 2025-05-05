---
title: 'ACSD-57565: 주문 대시보드에 잘못된 주문 정보가 표시됨'
description: ACSD-57565 패치를 적용하여 기간이 업데이트될 때까지 주문 대시보드에 잘못된 주문 정보가 표시되는 Adobe Commerce 문제를 해결합니다.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 5b292fef-23f6-479f-bf76-adad53d30cf4
source-git-commit: fdf6e6e85f903a26a7b44674937ccf88ee769d06
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-57565: 주문 대시보드에 잘못된 주문 정보가 표시됨

ACSD-57565 패치는 기간이 업데이트될 때까지 주문 대시보드에 잘못된 주문 정보가 표시되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.48이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-57565입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다

## 문제

주문 대시보드에 잘못된 주문 정보가 표시됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL dashboard charts]** 사용
1. 주문을 생성하고 송장을 발행합니다.
1. 주문 생성 후 최소 24시간 동안 기다립니다.
1. **[!UICONTROL dashboard chart]** 데이터를 확인합니다.
1. 전체 주문 수를 기록합니다.
1. 시간을 *현재 월*(으)로 변경한 다음 *오늘*(으)로 다시 변경하세요.

<u>예상 결과</u>:

대시보드 차트는 항상 올바른 통계를 보여 주어야 합니다.

<u>실제 결과</u>:

대시보드 차트는 첫 번째 로드 시 잘못된 통계를 표시합니다. 차트의 정확한 통계는 기간 후에 업데이트됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
