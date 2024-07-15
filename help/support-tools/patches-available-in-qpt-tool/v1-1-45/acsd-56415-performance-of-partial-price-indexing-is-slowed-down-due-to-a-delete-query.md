---
title: '''ACSD-56415: ''DELETE'' 쿼리로 인해 [!UICONTROL Partial Price Indexing]의 성능이 저하되었습니다.'''
description: 데이터베이스에 색인화할 부분 가격 데이터가 많을 때 'DELETE' 쿼리로 인해 [!UICONTROL Partial Price Indexing]의 성능이 느려지는 Adobe Commerce 문제를 해결하려면 ACSD-56415 패치를 적용하십시오.
feature: Catalog Service
role: Admin, Developer
exl-id: 0b099570-9f27-4ae2-9384-6b69ea50bd98
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56415: `DELETE` 쿼리로 인해 [!UICONTROL Partial Price Indexing]의 성능이 느려졌습니다.

ACSD-56415 패치는 데이터베이스에 부분 가격 데이터 인덱스가 많은 경우 `DELETE` 쿼리로 인해 [!UICONTROL Partial Price Indexing]의 성능이 느려지는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-56023입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

데이터베이스에 부분 가격 데이터 인덱스가 많은 경우 `DELETE` 쿼리로 인해 [!UICONTROL Partial Price Indexing]의 성능이 느려집니다.

<u>재현 단계</u>:

1. 고성능 프로필을 사용하여 *300000 제품* 및 *10개의 웹 사이트*&#x200B;를 만듭니다.
1. 관리 패널에 로그인합니다.
1. *10개의 고객 그룹을 만듭니다*.
1. 아래 쿼리를 실행하여 `_cl` 표에 제품을 추가하십시오.

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. 아래 명령을 실행하여 부분 가격 색인화 프로세스를 트리거합니다.

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u>예상 결과</u>:

`catalog_product_index_price`의 SQL 쿼리 DELETE `main_table`이(가) 빠르게 실행됩니다.

<u>실제 결과</u>:

`catalog_product_index_price`의 SQL 쿼리 DELETE `main_table`이(가) 매우 느리게 실행됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
