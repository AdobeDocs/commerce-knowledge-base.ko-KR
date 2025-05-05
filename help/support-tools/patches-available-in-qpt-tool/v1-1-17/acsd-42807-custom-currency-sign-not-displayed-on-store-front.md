---
title: 'ACSD-42807: 사용자 지정 통화 기호가 상점 앞에 표시되지 않음'
description: ACSD-42807 패치는 상점 첫 화면에 사용자 지정 통화 기호가 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-42807입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
exl-id: 21bd17b4-d9d8-4c40-8f89-d6f7b930b475
feature: Storefront
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-42807: 사용자 지정 통화 기호가 상점 앞에 표시되지 않음

ACSD-42807 패치는 상점 첫 화면에 사용자 지정 통화 기호가 표시되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-42807입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

사용자 지정 통화 기호가 상점 정면에 표시되지 않습니다.

<u>재현 단계</u>:

1. **스토어** > **설정** > **구성** > **일반** > **통화 설정**(으)로 이동하여 사용자 지정 통화를 선택합니다. 예: **멕시코 페소**.
1. **스토어** > **설정** > **구성** > **일반** > **로케일 옵션**&#x200B;으로 이동한 다음 **스페인어(멕시코)**&#x200B;를 선택합니다.
1. **스토어** > **통화 기호**(으)로 이동하여 통화 기호를 **MX$**(으)로 구성하십시오.
1. 앞줄에 있는 통화 기호를 확인합니다.

<u>예상 결과</u>:

기본 통화 기호는 &quot;MX$&quot;로, 통화는 &quot;멕시코 페소&quot;로, 로케일은 &quot;스페인어(멕시코)&quot;로 설정됩니다.

<u>실제 결과</u>:

기본 통화 기호는 &quot;$&quot;을(를) 표시합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
