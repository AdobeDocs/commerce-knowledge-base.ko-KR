---
title: '"MDVA-34886: "weight" 속성이 사용되면 검색 결과가 없습니다."'
description: MDVA-34886 패치는 가중치 속성을 검색 가능하도록 구성할 때 검색이 결과를 반환하지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.
exl-id: e6f33772-0167-4a54-9d62-0ab89edb5d1d
feature: Attributes, Cache, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-34886: &quot;weight&quot; 속성을 사용할 때 검색 결과가 없음

MDVA-34886 패치는 가중치 속성을 검색 가능하도록 구성할 때 검색이 결과를 반환하지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.5-p1

**Adobe Commerce 버전과 호환:**

Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.2 - 2.4.2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

가중치 속성이 검색 가능한 것으로 구성된 경우 검색에서 결과가 반환됩니다.

<u>재현 단계</u>:

1. 구성 Elasticsearch.
1. **관리자** > **스토어** > **특성** > **제품**(으)로 이동합니다. **Weight** 특성을 편집하고 해당 특성을 **검색 가능** = *예*&#x200B;로 설정합니다.
1. 속성을 저장하고 구성 캐시를 지웁니다.
1. 프런트 엔드에서 텍스트 값을 검색합니다(예: *bag*).
1. 검색 결과가 반환되지 않는지 확인합니다.
1. 예외 로그에는 다음과 같은 오류 메시지가 포함됩니다.

```php
{"type":"number_format_exception","reason":"For input string: \"bag\""}
```

<u>예상 결과</u>:

예상대로 가중치 속성이 검색 가능하도록 구성된 경우에도 검색이 결과를 반환합니다.

<u>실제 결과</u>:

가중치 속성이 검색 가능한 것으로 구성된 경우 검색은 결과를 반환하지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
