---
title: 'MDVA-40134: 공유 카탈로그가 활성화된 경우 GraphQL에서 관련 제품을 반환하지 않음'
description: MDVA-40134 패치는 공유 카탈로그가 활성화된 경우 GraphQL이 관련 제품을 반환하지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40134입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.
exl-id: 7b14355a-1c14-4c80-9426-6c40505d638b
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-40134: 공유 카탈로그가 활성화되면 GraphQL에서 관련 제품을 반환하지 않음

MDVA-40134 패치는 공유 카탈로그가 활성화된 경우 GraphQL이 관련 제품을 반환하지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-40134입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL은 공유 카탈로그가 활성화된 경우 관련 제품을 반환하지 않습니다.

<u>필수 구성 요소</u>:

B2B 모듈을 설치해야 합니다.
인스턴스는 샘플 데이터만 사용하여 정리되어야 합니다.

<u>재현 단계</u>:

1. **스토어** > **구성** > **일반** > **B2B 기능**(으)로 이동하여 **회사 및 공유 카탈로그**&#x200B;를 사용하도록 설정합니다.
1. **카탈로그** > **공유 카탈로그**(으)로 이동하여 **일반 카탈로그**&#x200B;에 모든 제품을 추가하십시오.
1. 샘플 데이터를 사용하고 Joust Duffle Bag(SKU 24-MB01)를 수정합니다.
1. **관련 제품**&#x200B;에서 두 개의 더플 백(ID 7, 13)을 추가합니다.
1. **Post** 요청 보내기:

<pre>{
  제품(필터: {sku: {eq: "24-MB01"}, 정렬: {name: ASC}) {
    항목 {
      related_products {
        uid
        이름
      }
    }
  }
}</pre>

<u>예상 결과</u>:

관련 제품이 GraphQL 응답에 표시됩니다.

<u>실제 결과</u>:

사용자에게 다음 오류가 표시됩니다.

<pre>Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId()의 반환 값은 int 유형이어야 합니다. null 반환 {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId()의 반환 값은 int 유형이어야 합니다. null 반환 </pre>

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하십시오.
