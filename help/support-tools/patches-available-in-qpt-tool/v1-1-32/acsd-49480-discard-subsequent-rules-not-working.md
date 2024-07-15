---
title: 'ACSD-49480: 작동하지 않는 후속 규칙 버리기'
description: ACSD-49480 패치를 적용하여 [!UICONTROL Cart Price Rule - Discard Subsequent Rules]이(가) 의도한 대로 작동하지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: 8d306a9e-ed1a-4295-8130-81700cbf31a6
feature: Price Rules
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules]이(가) 의도한 대로 작동하지 않습니다.

ACSD-49480 패치는 [!UICONTROL Cart Price Rule - Discard Subsequent Rules]이(가) 의도한 대로 작동하지 않는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.32가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-49480입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!UICONTROL Cart Price Rule - Discard Subsequent Rules]이(가) 의도한 대로 작동하지 않습니다.

<u>재현 단계</u>:

1. [!UICONTROL Discard Subsequent Rules]이(가) *[!UICONTROL Yes]*(으)로 설정되고 [!UICONTROL Priority]이(가) *1*(으)로 설정된 **[!UICONTROL Actions]** 탭에서 *제품 ID 1*&#x200B;에 $10 할인을 제공하는 쿠폰 코드(이름: *TEST*)로 **[!UICONTROL Cart Price Rule]**&#x200B;을(를) 만듭니다.
1. [!UICONTROL Priority]이(가) *2*(으)로 설정된 **[!UICONTROL Actions]** 탭에서 *제품 ID 2*&#x200B;에 $5 할인을 제공하는 쿠폰 코드 없이 다른 **[!UICONTROL Cart Price Rule]**&#x200B;을(를) 만드십시오. 여기에서 *제품 ID 2*&#x200B;에 대한 글로벌 세일이라고 가정합니다.
1. 프론트엔드 사이트로 이동하여 *제품 ID 1* 및 *제품 ID 2*&#x200B;을(를) 장바구니에 추가하십시오.
1. *TEST* 쿠폰 코드를 적용합니다.

<u>예상 결과</u>

* *할인 1*&#x200B;이 *제품 ID 1*&#x200B;에 적용됩니다.
* *할인 2*&#x200B;이 *제품 ID 2*&#x200B;에 적용됩니다.

<u>실제 결과</u>

* *제품 ID 1*&#x200B;에는 *할인 1*&#x200B;만 적용됩니다.
* *할인 2*&#x200B;은(는) *제품 ID 2*&#x200B;에 적용되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
