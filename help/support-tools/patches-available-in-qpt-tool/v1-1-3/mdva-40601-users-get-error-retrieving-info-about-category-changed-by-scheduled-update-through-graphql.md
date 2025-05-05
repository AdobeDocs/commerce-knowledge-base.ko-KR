---
title: 'MDVA-40601: GraphQL을 통해 예약된 업데이트로 변경된 범주에 대한 데이터를 검색할 수 없음'
description: MDVA-40601 Adobe Commerce 품질 패치는 GraphQL을 통해 예약된 업데이트로 변경된 범주에 대한 정보를 가져올 때 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.3이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40601입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: b1ea93e7-8d4a-4bdd-8267-cc60de25bd39
feature: Categories, GraphQL
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-40601: GraphQL을 통해 예약된 업데이트로 변경된 범주에 대한 데이터를 검색할 수 없음

MDVA-40601 Adobe Commerce 품질 패치는 GraphQL을 통해 예약된 업데이트로 변경된 범주에 대한 정보를 가져올 때 오류가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://experienceleague.adobe.com/ko/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.3이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-40601입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.3.3 및 2.4.2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.1 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

GraphQL을 통해 예약된 업데이트로 변경된 카테고리에 대한 정보를 검색하려고 하면 오류가 발생합니다.

<u>재현 단계</u>:

1. 다음과 같이 하위 범주가 있는 범주 구조를 설정합니다.

   <pre>
   <code class="language-graphql">
   - Root
    - Some category
         - Some child category

   </code>
   </pre>

1. &quot;일부 범주&quot; ID 49로 GraphQL 쿼리를 실행합니다.

   <pre>
    <code class="language-graphql">
    query &lbrace;
     category(id: 49) &lbrace;
      name
      children &lbrace;
        name
       &rbrace;
     &rbrace;
   &rbrace;
   </code>
   </pre>

   결과:

   <pre>
    <code class="language-graphql">
    &lbrace;
      "data": &lbrace;
        "category": &lbrace;
          "name": "Some category",
          "children": &lbrack;
            &lbrace;
              "name": "Some child category"
            &rbrace;
          &rbrack;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. 다른 범주 이름으로 &quot;일부 범주&quot;에 대한 일정 업데이트를 만듭니다.
1. 예약 업데이트가 활성화될 때까지 기다립니다.
1. 위에 지정된 것과 동일한 쿼리를 실행합니다.

<u>예상 결과</u>:

동일한 결과를 받았지만 업데이트된 카테고리 이름이 제공됩니다.

<u>실제 결과</u>:

다음 오류가 발생합니다.

<pre>
<code class="language-graphql">
&lbrace;
  "errors": &lbrack;
    &lbrace;
      "debugMessage": "uasort() expects parameter 1 to be array, string given",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 2,
          "column": 3
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "category"
      &rbrack;
    &rbrace;
  &rbrack;,
  "data": &lbrace;
    "category": null
  &rbrace;
&rbrace;
</code>
</pre>

## 패치 적용

개별 패치를 적용하려면 배포 유형에 따라 다음 링크를 사용합니다.

&#x200B;* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
&#x200B;* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

Adobe Commerce용 품질 패치에 대한 자세한 내용은 다음을 참조하십시오.

&#x200B;* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
&#x200B;* [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
