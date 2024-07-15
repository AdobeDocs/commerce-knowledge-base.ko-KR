---
title: 'ACSD-53098: 공유 카탈로그의 제품이 프론트엔드를 반영하지 않음'
description: ACSD-53098 패치를 적용하여 공유 카탈로그에 할당된 제품이 부분 인덱스를 실행할 때 프론트엔드를 반영하지 않는 Adobe Commerce 문제를 해결합니다.
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
exl-id: 19c66a3a-04b2-48ee-aff3-ad2b592ff876
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-53098: 공유 카탈로그의 제품이 프론트엔드를 반영하지 않음

ACSD-53098 패치는 부분 인덱스를 실행할 때 공유 카탈로그에 할당된 제품이 프론트엔드를 반영하지 않는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.38이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-53098입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

API를 통해 공유 카탈로그에 할당된 제품은 부분 인덱서가 cron 작업을 실행한 후 소비자 cron이 실행되면 프론트엔드에 표시되지 않습니다.

<u>재현 단계</u>:

1. [!DNL RabbitMQ]을(를) 큐 서비스로 설정합니다.
1. 인덱서를 **[!UICONTROL Update on Schedule]** 모드로 전환합니다.
1. 공유 카탈로그를 만들어 회사에 할당합니다.
1. 간단한 제품을 만들고 카테고리에 할당합니다. 부분 색인 재지정을 실행합니다.

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. 다음 API 요청을 사용하여 생성된 제품을 공유 카탈로그에 할당합니다.

   ```
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. 다음 cron을 실행하여 대기열을 지우고 부분 색인 재지정을 실행합니다.

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. 회사 사용자로 프론트엔드에 로그인합니다.
1. 프론트엔드 카테고리 페이지를 확인하십시오.

<u>예상 결과</u>:

새로 배정된 제품이 앞줄에 나타납니다.

<u>실제 결과</u>:

새로 배정된 제품은 앞줄에 나타나지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
