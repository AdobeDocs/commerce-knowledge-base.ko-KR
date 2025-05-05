---
title: 'ACSD-49464: 송장, 선적 및 대변 메모가 아카이브에서 이동되지 않음'
description: orderId가 다른 경우 송장, 선적 및 대변 메모가 아카이브에서 다시 이동되지 않는 Adobe Commerce 문제를 해결하려면 ACSD-49464 패치를 적용합니다.
exl-id: 845f9878-5f7e-4e58-8f8a-b02af17b3f11
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-49464: 송장, 선적 및 대변 메모가 아카이브에서 이동되지 않음

ACSD-49464 패치는 orderId가 다른 경우 송장, 선적 및 대변 메모가 아카이브에서 다시 이동되지 않는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29가 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-49464입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

orderId가 다른 경우 송장, 선적 및 대변 메모는 아카이브에서 다시 이동되지 않습니다.

<u>재현 단계</u>:

1. 주문, 송장, 선적 및 대변 메모 보관을 활성화합니다.
1. 운송, 송장 및 대변 메모를 포함하는 주문을 생성하고 완료합니다.
1. 배송, 송장 및 대변 메모 ID가 주문 번호와 같지 않은지 확인하십시오.
1. 보관으로 주문을 이동합니다.
1. Order Management에 보관된 주문 복원
1. 각 [!UICONTROL Invoice], [!UICONTROL Shipping] 및 [!UICONTROL Credit Memo] 그리드 페이지에서 송장, 배송 및 대변 메모 세부 정보를 확인하십시오.

<u>예상 결과</u>:

해당 주문이 아카이브 목록에서 주문 관리로 이동될 때 원래 관련 기록이 복원됩니다.

<u>실제 결과</u>:

* 모든 ID가 다른 경우 배송, 송장 및 대변 메모에 대한 레코드가 없습니다.
* 주문 및 관련 레코드에 동일한 ID가 있는 경우 레코드가 반환됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
