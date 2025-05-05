---
title: 'ACSD-51294: 가격, 수량, 세금, 배송,  [!DNL Google Analytics] 및 GTM에 문자열로 전송된 수익'
description: ACSD-51294 패치를 적용하여 가격, 수량, 세금, 배송 및 매출이 문자열로  [!DNL Google Analytics]  및 GTM에 전송되는 Adobe Commerce 문제를 해결합니다.
feature: Orders, Shipping/Delivery, Variables
role: Admin
exl-id: 159e1e98-0def-4b20-901d-f5f58c3ead7c
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51294: 가격, 수량, 세금, 배송, [!DNL Google Analytics] 및 GTM에 문자열로 전송된 매출

ACSD-51294 패치는 가격, 수량, 세금, 배송 및 매출이 문자열로 [!DNL Google Analytics] 및 GTM에 전송되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.32가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51294입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko>). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

가격, 수량, 세금, 배송 및 매출은 문자열로 [!DNL Google Analytics] 및 GTM에 전송됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** > **[!UICONTROL Google GTag]** > **[!UICONTROL Google Analytics4]**(으)로 이동하여 [!DNL Google Tag Manager]을(를) 구성합니다.
2. 간단한 제품을 만듭니다.
3. 해당 제품으로 체크아웃을 완료하십시오.
4. 체크아웃 성공 페이지에서 `dataLayer` JavaScript 변수를 확인하십시오.

<u>예상 결과</u>

가격 및 수량 값은 숫자입니다.

<u>실제 결과</u>

가격 및 수량 값은 문자열입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko>)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko>)을 참조하세요.
