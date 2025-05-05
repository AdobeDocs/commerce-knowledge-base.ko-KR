---
title: 'ACSD-53347: 가격 인덱싱 성능은 점진적으로 초과 작업 시간을 감소시킵니다.'
description: ACSD-53347 패치를 적용하면 대규모 제품 카탈로그의 가격을 리인덱싱할 때 성능이 점차 저하되는 Adobe Commerce 문제를 해결할 수 있습니다.
feature: Price Indexer
role: Admin
exl-id: 28795673-54b0-4282-bd43-344401cbe140
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-53347: 가격 인덱싱 성능은 점진적으로 초과 작업 시간을 감소시킵니다.

ACSD-53347 패치는 대형 제품 카탈로그의 가격을 다시 색인화할 때 성능이 점차 저하되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-53347입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

대규모 제품 카탈로그의 가격을 리인덱싱하는 경우 인덱싱 프로세스 중에 실행되는 쿼리의 성능이 점진적으로 저하됩니다.

<u>재현 단계</u>:

1. 큰 단순 카탈로그를 만들고 사용자 지정 옵션을 이러한 제품에 할당합니다(사용자 지정 옵션은 색인화 중에 임시 테이블을 사용).
1. 문제에 대한 가시성을 높이기 위해 최소 200개 이상의 고객 그룹을 만드십시오.
1. 10개 이상의 웹 사이트를 만들고 각 웹 사이트에 모든 제품을 할당합니다.
1. 가져온 제품은 SKU와 이름만 다를 뿐 거의 동일합니다.
1. **[!UICONTROL DB Logging]** 사용
1. `bin/magento index:reindex catalog_product_price` 명령을 실행합니다.
1. `db.log`에서 `catalog_product_index_price_opt_agr_temp`*의* DELETE을 확인하십시오.

<u>예상 결과</u>:

*DB 쿼리* 실행이 효율적으로 실행됩니다.

<u>실제 결과</u>:

임시 테이블에서 *DB 쿼리*&#x200B;의 성능이 시간 초과로 느려지므로 가격 색인화 테이블을 완료하는 데 많은 시간이 소요됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
