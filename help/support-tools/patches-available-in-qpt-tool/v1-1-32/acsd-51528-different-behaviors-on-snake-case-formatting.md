---
title: 'ACSD-51528: snake_case 서식에 대한 다양한 동작'
description: ACSD-51528 패치를 적용하여 snake_case 서식에 다른 동작이 있는 Adobe Commerce 문제를 수정합니다.
exl-id: dd878321-8032-41f3-8dcd-acb0cc023b44
feature: Variables
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-51528: snake_case 서식에 대한 다양한 비헤이비어

ACSD-51528 패치는 snake_case 서식에 대한 다양한 동작을 수정합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.32가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51528입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

snake_case 서식에 대한 다양한 비헤이비어

<u>재현 단계</u>:

1. 다양한 속성 이름으로 `\Magento\Framework\Api\DataObjectHelper::populateWithArray` 함수를 테스트하십시오.
1. 이름이 *NewPName*&#x200B;인 속성은 *new_p_name*(으)로 변환해야 합니다. 대신 *new_pname*(으)로 변환됩니다.
1. 또한 개체에서 *getNewPName* 함수를 사용하는 경우 *추상 모델*&#x200B;이(가) 호출을 *new_p_name*(으)로 올바르게 변환하여 두 함수가 서로 호환되지 않도록 하므로 *null*&#x200B;이 반환됩니다.

<u>예상 결과</u>

**[!UICONTROL populateWithArray]** 함수는 개체 속성을 **[!DNL AbstractModel's]** `Getters` 및 `Setters`과(와) 호환되도록 snake_case로 올바르게 변환해야 합니다.

<u>실제 결과</u>

**[!UICONTROL populateWithArray]** 함수를 사용할 때 이름에 두 개 이상의 대문자가 연속으로 들어 있는 개체 속성을 사용하면 최종 데이터 배열에서 snake_case 변환이 올바르지 않게 됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
