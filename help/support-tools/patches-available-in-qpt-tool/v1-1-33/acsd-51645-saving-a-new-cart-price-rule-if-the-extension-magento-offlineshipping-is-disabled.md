---
title: 'ACSD-51645: 확장 Magento_OfflineShipping이 비활성화된 경우 새 장바구니 가격 규칙 저장'
description: 확장 Magento_OfflineShipping이 비활성화된 경우 새 장바구니 가격 규칙을 저장할 때 오류가 발생하는 Adobe Commerce 문제를 해결하려면 ACSD-51645 패치를 적용합니다.
exl-id: 301086bb-7aab-4e74-93e6-9080eebcb026
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-51645: 확장 Magento_OfflineShipping이 비활성화된 경우 새 장바구니 가격 규칙 저장

ACSD-51645 패치는 확장 Magento_OfflineShipping이 비활성화된 경우 새 장바구니 가격 규칙을 저장할 때 오류가 발생하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-51645입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko>). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

확장 `Magento_OfflineShipping`이(가) 비활성화된 경우 새 장바구니 가격 규칙을 저장할 때 오류가 발생합니다.

<u>재현 단계</u>:

1. `Magento_OfflineShipping` 모듈을 사용하지 않도록 설정합니다.
1. **관리자**&#x200B;에 로그인합니다.
1. **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**(으)로 이동합니다.
1. 새 **[!UICONTROL Cart Price Rule]** 만들기
1. 필수 필드를 채웁니다.
1. **[!UICONTROL Cart Price Rule]** 저장.

<u>예상 결과</u>:

장바구니 가격 규칙이 정상적으로 저장되었습니다.

<u>실제 결과</u>:

다음 오류가 발생합니다.
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko>)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko>)을 참조하세요.
