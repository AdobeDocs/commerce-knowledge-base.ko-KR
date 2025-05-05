---
title: 'ACSD-52831:  [!DNL Google reCAPTCHA v3 Invisible] 이(가) 활성화된 경우 협상 가능한 견적 주문을 할 수 없음'
description: ACSD-52831 패치를 적용하여  [!DNL Google reCAPTCHA v3 Invisible] 이(가) 활성화된 경우 협상 가능한 견적 주문을 할 수 없는 Adobe Commerce 문제를 해결합니다.
feature: Quotes, B2B, Checkout
role: Admin
exl-id: 80cf5592-0784-4b37-8373-abec0847a9f0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52831: [!DNL Google reCAPTCHA v3 Invisible]이(가) 활성화된 경우 협상 가능한 견적 주문을 할 수 없음

ACSD-52831 패치는 [!DNL Google reCAPTCHA v3 Invisible]이(가) 활성화된 경우 협상 가능한 견적 주문을 할 수 없는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.35가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-52831입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL Google reCAPTCHA v3 Invisible]이(가) 활성화된 경우 협상 가능한 견적 주문을 할 수 없습니다.

<u>재현 단계</u>:

1. B2B 견적 기능을 활성화합니다.
1. 상점 첫 화면에서 [!DNL Google reCAPTCHA v3 Invisible]을(를) 활성화하여 체크아웃/주문 처리를 활성화합니다.
1. 견적을 제시하고 해당 견적을 사용하여 체크아웃을 진행합니다.
1. CAPTCHA 오류로 인해 주문할 수 없습니다.

<u>예상 결과</u>:

견적은 체크아웃까지 진행됩니다.

<u>실제 결과</u>:

오류 *reCAPTCHA 유효성 검사에 실패했습니다. 다시 시도해 주십시오*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
