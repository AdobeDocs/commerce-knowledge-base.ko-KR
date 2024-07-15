---
title: 'ACSD-54264: 고객이 협상 가능 견적으로 체크아웃하려고 할 때 오류 발생'
description: ACSD-54264 패치를 적용하여 "요청한 속성을 업데이트할 수 없습니다."라는 오류 메시지가 표시되는 Adobe Commerce 문제를 해결합니다. Row ID:store_id"는 고객이 다른 스토어 뷰에서 협상 가능한 견적을 사용하여 체크아웃하려고 할 때 표시됩니다.
feature: B2B, Checkout
role: Admin, Developer
exl-id: de8f451e-3b0a-4721-9ff4-18553477db1d
source-git-commit: 2e344b1ca4bc075bdbc9074bb431a398f0871698
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-54264: 고객이 협상 가능한 견적으로 체크아웃하려고 할 때 오류가 표시됩니다.

ACSD-54264 패치가 오류 메시지 *을(를) 업데이트할 수 없는 문제를 해결했습니다. 행 ID: store_id*&#x200B;은 고객이 다른 스토어 보기에서 협상 가능한 견적을 사용하여 체크아웃하려고 할 때 표시됩니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-54264입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

오류 메시지 *요청한 특성을 업데이트할 수 없습니다. 행 ID: store_id*&#x200B;은 고객이 다른 스토어 보기에서 협상 가능한 견적을 사용하여 체크아웃하려고 할 때 표시됩니다.

<u>필수 구성 요소</u>:

Adobe Commerce B2B 모듈이 설치되고 활성화됩니다.

<u>재현 단계</u>:

1. 기본 웹 사이트에 대한 추가 스토어 보기를 만듭니다.
1. 구성에서 *[!UICONTROL B2B Quote]*&#x200B;을(를) 사용하도록 설정합니다.
1. 스토어 조회수 중 하나에서 회사 고객으로 로그인합니다.
1. *[!UICONTROL Shopping Cart]*&#x200B;에 제품을 추가합니다.
1. 검토를 위해 견적을 제출합니다.
1. 관리자는 **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**(으)로 이동하여 승인된 견적을 제출합니다.
1. 회사 고객인 경우 스토어 보기를 다른 스토어 보기로 변경합니다.
1. 한번 확인해 보세요

<u>예상 결과</u>:

고객이 이 견적을 주문합니다.

<u>실제 결과</u>:

* 배송 정보를 저장하는 동안 오류가 발생했습니다.

  `You cannot update the request attribute. Row ID: store_id =#`

* 다음 오류가 기록됩니다.

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
