---
title: 'ACSD-57086: 약관이 활성화된 기본이 아닌 웹 사이트의 주문이 잘못 처리됨'
description: ACSD-57086 패치를 적용하여 약관이 활성화된 기본이 아닌 웹 사이트에서 주문된 주문이 올바르게 처리되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Orders
role: Admin, Developer
source-git-commit: ab90568b0333415e73ca42b9c127a2a599f00aa7
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---


# ACSD-57086: 약관이 활성화된 기본이 아닌 웹 사이트의 주문이 잘못 처리됨

ACSD-57086 패치는 약관이 활성화된 기본이 아닌 웹 사이트에서 주문된 주문이 올바르게 처리되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-57086입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

AsyncOrder 처리를 통해 다중 스토어 설정을 사용하는 동안 큐 소비자 코드에서 범위 처리 문제로 인해 기본 웹 사이트가 아닌 웹 사이트/스토어에서 수행한 주문이 거부됩니다.

<u>재현 단계</u>:

1. [!DNL RabbitMQ]을(를) 설치하고 `bin/magento setup:upgrade`을(를) 실행하여 [!DNL RabbitMQ]에 대한 큐를 만드십시오.
1. 다음을 사용하여 AsyncOrder 처리 구성:

   ```bash
   bin/magento setup:config:set --checkout-async 1
   ```

1. 보조 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. 두 웹 사이트 간에 공유되는 제품을 만듭니다.
1. 사용 약관:
   1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**(으)로 이동합니다.
   1. *[!UICONTROL Enable Terms And Conditions]*&#x200B;을(를) *예*(으)로 설정합니다.
1. 두 웹 사이트에 대한 약관을 구성합니다.
   1. **[!UICONTROL Stores]** > **[!UICONTROL Terms And Conditions]** > **[!UICONTROL Add New Condition]**(으)로 이동합니다.
   1. 다음 설정을 사용하십시오.
      * *[!UICONTROL Condition Name]*: *모두*
      * *[!UICONTROL Status]*: *[!UICONTROL Enabled]*
      * *[!UICONTROL Applied]*: *[!UICONTROL Manually]*
      * *[!UICONTROL Store View]*: *[!UICONTROL Default Store View]*
   1. 두 번째 웹 사이트/스토어 보기에 대한 다른 조건을 만듭니다.
1. **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**(으)로 이동하여 기본 웹 사이트를 변경합니다. 두 번째 웹 사이트를 클릭하고 *[!UICONTROL Set as Default]*&#x200B;을(를) 확인한 다음 저장합니다.
1. 다음을 사용하여 캐시를 지웁니다.

   ```bash
   bin/magento cache:clear
   ```

1. 상점 첫 화면으로 이동하여 장바구니에 제품을 추가합니다. 체크아웃을 진행하고 주문합니다(약관에 동의하려면 결제 방법 단계에 확인란이 표시되어야 함).
1. 주문 후 관리자로 돌아간 후 기본 웹 사이트를 다시 원래 기본 웹 사이트로 변경하고 저장합니다.
1. 캐시를 지웁니다.

   ```bash
   bin/magento cache:clear
   ```

1. 다음 명령을 실행하여 큐 소비자를 시작합니다.

   ```bash
   bin/magento queue:cons:start placeOrderProcessor
   ```

<u>예상 결과</u>:

주문은 이행되며 자동으로 거부되지 않습니다.

<u>실제 결과</u>:

주문 상태가 *거부됨*&#x200B;이고 다음 댓글이 있습니다.

*주문이 실행되지 않았습니다. 먼저 약관에 동의한 후 다시 주문해 보십시오.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
