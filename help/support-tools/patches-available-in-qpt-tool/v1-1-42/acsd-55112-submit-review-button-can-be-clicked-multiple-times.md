---
title: 'ACSD-55112: [!UICONTROL Sumbit Review] 단추를 여러 번 클릭할 수 있습니다.'
description: ACSD-55112 패치를 적용하여  [!DNL Google reCAPTCHA v3] 유효성 검사 없이 [!UICONTROL Submit Review] 단추를 여러 번 클릭할 수 있는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin, Developer
exl-id: db202472-1d96-4ac0-8ecd-eab84c9f4cbf
source-git-commit: b5894687704594a4e751c230246bdf167b1b6402
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# ACSD-55112: [!UICONTROL Submit Review] 단추를 여러 번 클릭할 수 있습니다.

>[!NOTE]
>
>이 패치는 [ACSD-51890](/help/support-tools/patches-available-in-qpt-tool/v1-1-35/acsd-51890-submit-review-button-can-be-clicked-multiple-times.md)을(를) 대체합니다.

ACSD-55112 패치는 [!DNL Google reCAPTCHA v3] 유효성 검사 없이 [!UICONTROL Submit Review] 단추를 여러 번 클릭할 수 있는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-55112입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

다음 오류를 가져오는 중:

```JS
_jquery.validate.js:799 Uncaught TypeError: Cannot read properties of undefined (reading 'call'). Exception occurred when checking element login-email, check the 'validate' method.
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
