---
title: 'ACSD-51857: ''aggregate_sales_report_bestsellers_data''의 cron 작업이 성능에 영향을 미침'
description: ACSD-51857 패치를 적용하여 느린 cron 작업 'aggregate_sales_report_bestsellers_data'가 큰 'sales_order' 및 'sales_order_item' 데이터베이스 테이블에 영향을 주는 Adobe Commerce 문제를 해결합니다.
exl-id: 444ab283-c98b-46b3-a492-706f0ce34a27
source-git-commit: a33364531d2efd572cd1b1847dd45e0f427af03b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51857: `aggregate_sales_report_bestsellers_data`의 cron 작업이 느리면 성능에 영향을 줍니다.

ACSD-51857 패치는 느린 cron 작업 `aggregate_sales_report_bestsellers_data`이(가) 큰 `sales_order` 및 `sales_order_item` 데이터베이스 테이블에 영향을 주는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51857입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`sales_order` 및 `sales_order_item` 데이터베이스 테이블에서 `aggregate_sales_report_bestsellers_data`의 Cron 작업 성능이 느립니다.

이 문제를 해결하기 위해 보고서의 데이터를 가져오는 기본 데이터 쿼리가 더 효율적인 양식으로 다시 작성되었습니다. 이제 하위 쿼리를 사용하여 데이터 하위 집합을 결정합니다.

하위 쿼리가 가능한 한 빨리 작동하려면 `sales_order` 데이터베이스 테이블 `SALES_ORDER_STORE_STATE_CREATED`에 대해 `store_id`, `state` 및 `created_at` 열을 기준으로 새 인덱스를 추가했습니다.

<u>필수 구성 요소</u>

매일 많은 주문을 확인하십시오.

<u>재현 단계</u>

1. `aggregate_sales_report_bestsellers_data` cron 작업을 실행합니다.
1. **[!UICONTROL Bestsellers]** 탭 아래의 관리 대시보드에 표시할 데이터를 확인하십시오.

<u>예상 결과</u>:

**[!UICONTROL Configuration]** 탭의 *[!UICONTROL Quantity per source]*&#x200B;은(는) 비워둘 수 없습니다.

<u>실제 결과</u>:

**[!UICONTROL Configuration]** 탭의 *[!UICONTROL Quantity per source]*&#x200B;이(가) 비어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
