---
title: 'ACSD-57315: 가져오기 단추를 클릭할 때마다  [!DNL PayPal Payflow Pro] 에 새 트랜잭션이 만들어집니다.'
description: ACSD-57315 패치를 적용하여 [!UICONTROL Admin]의 트랜잭션 보기 화면에서 가져오기 단추를 클릭할 때마다  [!DNL PayPal Payflow Pro] 에 새 트랜잭션이 만들어지는 Adobe Commerce 문제를 해결합니다.
feature: Payments
role: Admin, Developer
exl-id: bcc7467d-09f9-4235-9f9f-46d3034567b8
source-git-commit: d7ace1f20defb01105d4a241f971b06fca052215
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315: 가져오기 단추를 클릭할 때마다 [!DNL PayPal Payflow Pro]에 새 트랜잭션이 만들어집니다.

ACSD-57315 패치는 [!UICONTROL Admin]의 트랜잭션 보기 화면에서 가져오기 단추를 클릭할 때마다 [!DNL PayPal Payflow Pro]에서 새 트랜잭션이 만들어지는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.48이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-57315입니다. 이 문제는 Adobe Commerce 2.5.0에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!UICONTROL Admin]의 트랜잭션 보기 화면에서 가져오기 단추를 클릭할 때마다 [!DNL PayPal Payflow Pro]에서 새 트랜잭션이 만들어집니다.

<u>재현 단계</u>:

1. [!DNL PayPal Payflow Pro] 구성.
1. 트랜잭션 메서드를 *[!UICONTROL Sale]*(으)로 설정하십시오.
1. *신용 카드*&#x200B;를 사용하여 주문합니다.
1. [!UICONTROL Admin]에서 트랜잭션을 엽니다.
1. **[!UICONTROL Fetch]** 단추를 클릭합니다.
1. [!DNL PayPal] 계정에서 주문과 관련된 트랜잭션을 확인하세요.

<u>예상 결과</u>:

신규 결제 거래가 생성되지 않습니다.

<u>실제 결과</u>:

이미 지급된 주문에 대해 신규 지급 거래가 생성됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
