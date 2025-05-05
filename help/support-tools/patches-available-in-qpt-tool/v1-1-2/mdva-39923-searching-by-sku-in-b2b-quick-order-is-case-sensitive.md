---
title: 'MDVA-39923: B2B 빠른 주문 기능에서 SKU로 검색하는 것은 대/소문자를 구분합니다.'
description: MDVA-39923 패치는 고객이 이름이 저장된 것과는 다른 대/소문자를 사용하여 B2B 빠른 주문 기능에서 SKU로 주문을 검색할 때 오류가 발생하는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39923입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 52e435df-28a7-49be-a257-7e5801601d57
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-39923: B2B 빠른 주문 기능에서 SKU로 검색하는 것은 대/소문자를 구분합니다.

MDVA-39923 패치는 고객이 이름이 저장된 것과는 다른 대/소문자를 사용하여 B2B 빠른 주문 기능에서 SKU로 주문을 검색할 때 오류가 발생하는 문제를 수정합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-39923입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.1-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

B2B 빠른 주문 기능에서 SKU로 검색하는 것은 대/소문자를 구분하며 SKU가 저장된 대/소문자와 다른 대/소문자가 사용되는 경우 오류를 표시합니다.

<u>필수 구성 요소</u>:

B2B 모듈이 설치되어 있습니다.

<u>재현 단계</u>:

1. 관리자에 로그인하고 **스토어** > **구성** > **B2B**(으)로 이동합니다.
1. **공유된 카탈로그** 및 **빠른 주문**&#x200B;을 사용하도록 설정하십시오.
1. 대문자 SKU로 제품을 만듭니다(예: TEST20-1234).
1. 만든 제품을 **공유 카탈로그**&#x200B;에 할당합니다.
1. 고객으로 로그인하고 **빠른 주문**&#x200B;을 클릭하세요.
1. SKU를 소문자(예: test20-1234)로 입력합니다.

<u>예상 결과</u>:

제품은 사용된 사례와 관계없이 발견되어야 합니다.

<u>실제 결과</u>:

다음 오류 메시지를 받았습니다. *1개 제품에 주의가 필요합니다*.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
