---
title: 'ACSD-51408: 주문 항목 상태가 [!UICONTROL backordered](으)로 잘못 설정되었습니다.'
description: ACSD-51408 패치를 적용하여 주문 항목 상태가 [!UICONTROL backordered](으)로 잘못 설정된 Adobe Commerce 문제를 해결합니다.
feature: B2B, Orders
role: Admin
exl-id: 0355beca-4612-438f-8f91-be42d8d637e9
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# ACSD-51408: 주문 항목 상태가 *[!UICONTROL backordered]*(으)로 잘못 설정되었습니다.

ACSD-51408 패치는 주문 항목 상태가 [!UICONTROL backordered](으)로 잘못 설정된 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.33이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-51408입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

주문 항목 상태가 *[!UICONTROL backordered]*(으)로 잘못 설정되었습니다.

<u>필수 구성 요소</u>:

Adobe Commerce B2B 및 Inventory management(MSI) 모듈이 설치되어 있습니다.

<u>재현 단계</u>:

1. 새 웹 사이트, 스토어 및 스토어 보기를 만듭니다.
1. 새 소스를 만듭니다.
1. 1단계에서 생성한 새 웹 사이트에 연결된 새 스톡을 생성하고 2단계에서 생성한 소스를 지정합니다.
1. 회사를 만들고 1단계에서 만든 새 웹 사이트에 할당합니다.
1. 새 고객을 만들고 4단계에서 만든 회사에 할당합니다.
1. 제품을 만들어 새 웹 사이트에 할당하고 **[!UICONTROL default stock]** = *0*, **[!UICONTROL new stock]**&#x200B;을(를) *0*&#x200B;보다 크게 설정합니다.
1. **[!UICONTROL backorders]** 사용
1. 새 웹 사이트 범위에 **[!UICONTROL Check/Money Order]** 결제 방법을 사용하도록 설정합니다.
1. 새 웹 사이트 범위에 대해 **[!UICONTROL Flat Rate shipping method]**&#x200B;을(를) 사용하도록 설정합니다.
1. **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**&#x200B;에서 새 주문을 만듭니다.
1. 5단계에서 생성된 새 고객을 선택합니다.
1. 1단계에서 만든 새 스토어를 선택합니다.
1. 6단계에서 만든 제품을 선택합니다.
1. 결제 및 배송 방법을 포함한 주문 정보를 작성하십시오.
1. 주문을 제출합니다.
1. *항목 상태*&#x200B;를 확인하세요.

<u>예상 결과</u>

그 상품은 재고에서 발송할 수 있다. 항목 상태는 *[!UICONTROL ordered]*&#x200B;입니다.

<u>실제 결과</u>

항목 상태는 *[!UICONTROL backordered]*&#x200B;입니다.

>[!MORELIKETHIS]
>
>제품 재고가 0일 때 [주문 항목 상태가 *[!UICONTROL Ordered]*(으)로 잘못 설정되었습니다.](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
