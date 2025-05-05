---
title: 'ACSD-53722: 번들 제품 옵션 가격이 $0로 변경됨'
description: ACSD-53722 패치를 적용하여 다양한 범위에 대한 예정된 업데이트가 활성화될 때 번들 제품 옵션의 가격이 $0로 변경되는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin, Developer
exl-id: da4c25ac-78bc-4d4e-a55e-826924a099e9
source-git-commit: e587b70a270bca624fb60a1b0940c05221da3aef
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-53722: 번들 제품 옵션 가격이 $0로 변경됨

ACSD-53722 패치는 다양한 범위의 예약된 업데이트가 활성화될 때 번들 제품 옵션의 가격이 $0로 변경되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-53722입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다양한 범위의 예약된 업데이트가 활성화되면 번들 제품 옵션의 가격은 $0로 변경됩니다.

<u>재현 단계</u>:

1. A와 B, 이렇게 두 개의 웹 사이트를 만듭니다.
1. **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]**&#x200B;에서 구성을 설정합니다.
1. 웹 사이트 A 및 B에서 고정 가격으로 번들 제품을 만듭니다.

   * 번들 제품 가격 = 고정 = *0*

1. 번들에 대한 드롭다운 옵션으로 간단한 제품 하나를 추가합니다. 다음 가격을 설정합니다.

   * 번들 옵션 = *120*&#x200B;에 포함된 간단한 제품의 모든 스토어 보기 가격
   * 간단한 제품의 웹 사이트 번들 옵션 내 가격 = *130*
   * 번들 옵션 = *140*&#x200B;에 포함된 간단한 제품의 웹 사이트 B 가격

1. 웹 사이트 A에서 번들 제품을 비활성화하도록 업데이트 일정을 예약합니다.

<u>예상 결과</u>:

웹 사이트 A에 대한 예약된 업데이트는 웹 사이트 B의 가격에 영향을 주지 않습니다.

<u>실제 결과</u>:

예정된 업데이트 이후 웹 사이트 B의 번들 제품 옵션 가격이 **$0**(으)로 변경됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
