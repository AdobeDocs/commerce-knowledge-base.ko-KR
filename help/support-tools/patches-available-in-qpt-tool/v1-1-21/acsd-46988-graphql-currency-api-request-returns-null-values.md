---
title: 'ACSD-46988: GraphQL 통화 API 요청이 null 값을 반환합니다.'
description: ACSD-46988 패치는 GraphQL 통화 API 요청이 사용자 지정 통화에 대한 null 값을 반환하는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21이 설치된 경우 사용할 수 있습니다. 패치 ID는 ACSD-46988입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.
exl-id: 8da0ab99-8db9-4222-9400-6df1520267f0
feature: REST, GraphQL
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-46988: GraphQL 통화 API 요청이 null 값을 반환합니다.

ACSD-46988 패치는 GraphQL 통화 API 요청이 사용자 지정 통화에 대한 null 값을 반환하는 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-46988입니다. 이 문제는 Adobe Commerce 2.4.6에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL 통화 API 요청이 사용자 지정 통화에 대한 null 값을 반환합니다.

<u>재현 단계</u>:

1. 관리자에서 사용자 지정 통화를 구성합니다. **시스템** > **구성** > **일반** > **통화 설정**(으)로 이동합니다.
1. 다음 페이로드를 사용하여 GraphQL 요청 보내기:

<pre>
<code class="language-graphql">
&lbrace;
    currency &lbrace;
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates &lbrace;
            currency_to
            rate
        &rbrace;
    &rbrace;
&rbrace;
</code>
</pre>

<u>예상 결과</u>:

이 요청은 null 값 대신 통화 값을 반환합니다.

<u>실제 결과</u>:

요청은 여러 null 값을 반환합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: 품질 패치 도구 안내서의 [품질 패치 도구 > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 패치 설치 후 추가 단계 필요

온-프레미스 사용자의 경우:

* 실행: `composer require symfony/intl:"~5.4.11"`

Cloud 사용자의 경우:

* 실행: `composer require symfony/intl:"~5.4.11"`
* 패치 파일과 함께 `composer.json` 및 `composer.lock` 파일을 git 저장소에 푸시합니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 품질 패치 도구 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하십시오.
