---
title: 'ACSD-54887: 고객 세션이 만료된 후 고객 장바구니가 지워짐'
description: ACSD-54887 패치를 적용하여 고객 세션이 [!UICONTROL Persistent Shopping Cart]을(를) 활성화한 상태로 만료된 후 고객 장바구니가 지워지는 Adobe Commerce 문제를 해결합니다.
feature: Shopping Cart
role: Admin, Developer
source-git-commit: fd73d89e8d60f6a4ab2ff5ba08df385adbd3faaa
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---


# ACSD-54887: 고객 세션이 만료된 후 고객 장바구니가 지워짐

ACSD-54887 패치는 고객 세션이 [!UICONTROL Persistent Shopping Cart]을(를) 활성화한 상태로 만료된 후 고객의 장바구니가 지워지는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-54887입니다. 이 문제는 Adobe Commerce 2.4.8에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p8, 2.4.5-p3 - 2.4.5-p7 및 2.4.6-p1 - 2.4.6-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객 장바구니가 [!UICONTROL Persistent Shopping Cart]이(가) 활성화된 상태에서 고객 세션이 만료된 후 지워집니다.

<u>재현 단계</u>:

1. [!UICONTROL Persistent Shopping Cart] 사용 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** = *예*(으)로 이동합니다.

   지속성이 활성화된 상태로 로그인합니다(참고: 팝업 권한 부여에서는 사용할 수 없지만 직접 [!UICONTROL Sign in] 페이지에서만 사용할 수 있음).

1. 장바구니에 제품을 추가합니다.
1. 체크아웃을 진행하고 결제 방법을 선택합니다.
1. 세션 만료(`PHPSESSID` 삭제).
1. 페이지를 새로 고칩니다. 결제 방법이 이미 선택되고 [!UICONTROL Persistent Cart] 쿠키가 제거되었기 때문에 견적이 즉시 게스트 견적으로 변환되었는지 확인하십시오.
1. 세션 만료(`PHPSESSID` 삭제).
1. 페이지를 새로 고칩니다. 장바구니가 비어 있는지 확인합니다.
1. 다시 로그인합니다.

<u>예상 결과</u>:

다시 로그인하면 장바구니에 제품이 있습니다.

<u>실제 결과</u>:

다시 로그인하면 장바구니가 비어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.

