---
title: "B2B-2674: customAttributeMetadata GraphQL 쿼리에 캐싱 기능을 추가합니다."
description: B2B-2674 패치를 적용하여 customAttributeMetadata GraphQL 쿼리에 캐싱 기능을 추가합니다.
feature: Attributes, B2B, Cache, GraphQL
role: Admin
exl-id: a4efb268-f811-41f2-a788-a8cfc3016f61
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# B2B-2674: `customAttributeMetadata` GraphQL 쿼리에 캐싱 기능을 추가합니다.

B2B-2674 패치는 `customAttributeMetadata` GraphQL 쿼리에 캐싱 기능을 추가합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 B2B-2674입니다. 이 문제는 Adobe Commerce 2.4.7-Beta1에서 수정될 예정입니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`customAttributeMetadata` GraphQL 쿼리를 캐시할 수 없습니다.

<u>필수 구성 요소</u>:

* 서버가 Adobe Commerce 백엔드에 프록싱하는 [!DNL Varnish]을(를) 가리키고 있습니다.
* 구성 설정 `system/full_page_cache/caching_application`이(가) *2*([!DNL Varnish])(으)로 설정되어 있거나 Adobe Commerce 관리자 > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** >(으)로 이동하여 [!DNL Varnish](으)로 설정하십시오.

패치를 적용한 후 다음 단계를 실행하여 캐싱 기능을 사용할 수 있는지 확인합니다.

1. 임의의 필드를 사용하여 위에 나열된 GraphQL 쿼리에 `GET` 요청을 보냅니다.
1. 변경 없이 요청을 다시 보내면 훨씬 더 빨라집니다. 요청이 백엔드로 전송되지 않지만 [!DNL Varnish]에 의해 캐시 히트로 완전히 처리됩니다.
1. 추가 증명이 필요한 경우 [VCL](https://github.com/magento/magento2/blob/2.4-develop/app/code/Magento/PageCache/etc/varnish6.vcl#L239)에 있는 `X-Magento-Debug` 헤더 집합을 주석 처리한 다음 [!DNL Varnish]을(를) 다시 시작하고 위의 단계를 다시 실행하십시오.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
