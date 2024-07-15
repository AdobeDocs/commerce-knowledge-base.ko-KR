---
title: '"ACSD-53750: 다중 스레드 catalog_product_price 리인덱스 도중 "끊어진 파이프 또는 닫힌 연결" 오류 발생"'
description: ACSD-53750 패치를 적용하여 다중 스레드 catalog_product_price 재인덱싱 도중 *파이프가 끊기거나 연결이 닫히는* 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin, Developer
exl-id: afb30384-74e7-4857-9aff-8e99f5abc309
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-53750: 다중 스레드 `catalog_product_price` 다시 인덱싱하는 동안 *파이프가 끊겼거나 연결이 닫혔습니다* 오류

ACSD-53750 패치는 다중 스레드 `catalog_product_price`을(를) 다시 인덱싱하는 동안 *끊어진 파이프 또는 닫힌 연결* 오류가 발생하는 문제를 수정합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.37이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-53750입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다중 스레드 `catalog_product_price` 다시 인덱싱하는 동안 *파이프가 끊겼거나 연결이 닫혔습니다* 오류가 발생했습니다.

<u>재현 단계</u>:

1. RabbitMq를 구성합니다.
1. 첨부된 `small.xml` 파일을 사용하여 샘플 데이터를 생성합니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]**(으)로 이동하여 **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**&#x200B;을(를) 설정합니다.
1. 이를 지원하는 인덱스에 대한 차원 모드를 설정합니다. 예: `catalog_product_price_website_and_customer_group` 또는 `customer_group`.

   ```
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. `catalog_product_price`에 대한 인덱서 재설정을 실행합니다.

   ```
   bin/magento indexer:reset catalog_product_price
   ```

1. 여러 스레드를 사용하여 인덱서 재설정에 대해 인덱서를 실행합니다.

   ```
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>예상 결과</u>:

오류가 발생하지 않습니다.

<u>실제 결과</u>:

AMQP 연결로 인해 다음 오류가 발생합니다. *파이프가 끊어졌거나 연결이 닫혔습니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
