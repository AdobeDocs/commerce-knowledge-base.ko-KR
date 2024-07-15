---
title: 'ACSD-47937: 애플리케이션 수준 캐싱으로 인해 가격 하락 알림이 전송되지 않음'
description: ACSD-47937 패치를 적용하여 애플리케이션 수준 캐싱으로 인해 가격 하락 알림이 항상 전송되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: f39c9ef6-4689-427f-bd61-3a52dec88be2
feature: Admin Workspace, Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-47937: 애플리케이션 수준 캐싱으로 인해 가격 하락 알림이 전송되지 않음

ACSD-47937 패치는 애플리케이션 수준 캐싱으로 인해 가격 하락 알림이 항상 전송되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-47937입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4 및 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4, 2.4.5 및 2.4.5-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객이 이후 제품 가격 변경에 대한 제품 가격 인하 이메일을 받지 못하고 있습니다.

<u>재현 단계</u>:

1. **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**&#x200B;에서 *[!UICONTROL Price Changes]* 및 *[!UICONTROL Back in Stock]*&#x200B;에 대해 **[!UICONTROL Product Alert]**&#x200B;을(를) 사용하도록 설정하십시오.
1. **[!UICONTROL Display Out of Stock Products]** 사용
1. 수량 = 0인 단순 제품(ABC)을 생성합니다.
1. 상점에서 고객을 만들고 위의 제품에 가입하여 가격 하락에 대한 제품 알림을 받으십시오.
1. 고객에 대한 제품 경고를 시작합니다.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. ABC 제품의 가격을 낮춰주세요.
1. 제품 경고 cron을 트리거합니다.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. ABC 제품의 가격을 다시 깎아 주세요.
1. 제품 경고 cron을 트리거합니다.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>[!DNL n98] 도구에 익숙하지 않은 경우 평소대로 `bin/magento cron:run command`을(를) 실행하고 `cron_schedule` 테이블을 모니터링하여 `catalog_product_alert` 작업이 성공 상태가 되도록 할 수 있습니다.

<u>예상 결과</u>:

두 번째 가격 인하 이메일이 전송됩니다.

<u>실제 결과</u>:

두 번째 가격 인하 이메일은 전송되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
