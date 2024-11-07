---
title: 'MDVA-39305: 활성화된 Google reCAPTCHA의 로그인 문제'
description: MDVA-39305 패치는 등록된 고객이 활성화된 Google reCAPTCHA로 로그인할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39305입니다. 이 문제는 Adobe Commerce 버전 2.4.4 및 2.4.7에서 수정됩니다.
exl-id: 1e8e7dc7-f8f1-4432-90f4-dc73d85f353a
feature: Console
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-39305: Google reCAPTCHA가 활성화된 경우 로그인 문제

MDVA-39305 패치는 등록된 고객이 활성화된 Google reCAPTCHA로 로그인할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-39305입니다. 이 문제는 Adobe Commerce 버전 2.4.4 및 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라의 Adobe Commerce 2.4.2-p1, 2.4.3-p3, 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1-p1 - 2.4.3-p3, 2.4.4-p1 - 2.4.4-p5, 2.4.5 - 2.4.6-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

등록된 고객은 활성화된 Google reCAPTCHA를 사용하여 로그인할 수 없습니다.

<u>재현 단계</u>:

1. **스토어** > **구성** > **보안** > **Google reCAPTCHA 상점**(으)로 이동하여 **Google reCAPTCHA**&#x200B;를 사용하도록 설정합니다.
1. **Frontend**(으)로 이동합니다.
1. 브라우저에서 **개발자 도구 콘솔**&#x200B;을 엽니다.

<u>예상 결과</u>:

콘솔에 CSP 경고가 없습니다.

<u>실제 결과</u>:

콘솔의 CSP 경고.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하십시오.
