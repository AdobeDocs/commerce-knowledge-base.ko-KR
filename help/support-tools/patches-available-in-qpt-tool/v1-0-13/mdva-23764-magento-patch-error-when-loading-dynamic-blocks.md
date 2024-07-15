---
title: 'MDVA-23764 Magento 패치: 동적 블록을 로드할 때 오류 발생'
description: MDVA-23764 Magento 패치가 의 버그를 수정합니다
exl-id: b884ade6-f88d-4c79-8e84-5a59252abb75
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# MDVA-23764 Magento 패치: 동적 블록을 로드할 때 오류 발생

MDVA-23764 Magento 패치가 의 버그를 수정합니다

```php
JsFooterPlugin.php
```

동적 블록의 표시에 영향을 줍니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13이 설치된 경우에 사용할 수 있습니다. 이 문제는 Magento 2.3.5에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Magento 버전:** Magento Commerce Cloud 2.3.3에 대해 패치가 만들어졌습니다.

**Magento 버전과 호환:** Magento Commerce 및 Magento Commerce Cloud 2.3.2 - 2.3.4-p2.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계:</u>

다음과 같은 URL을 로드해 보십시오. https://\[magento domain\]/banner/ajax/load/.

<u>실제 결과:</u>

다음과 유사한 오류가 발생합니다. *발견되지 않은 TypeError: strpos() 매개 변수 1은 문자열이어야 합니다. null이 제공됩니다...(코드 줄)* .

<u>예상 결과:</u>

URL이 오류 없이 로드됩니다.

## 패치 적용

QPT 패치를 적용하는 방법에 대한 지침은 Magento 제품에 따라 다음 링크를 사용하십시오.

* Magento Commerce: DevDocs [품질 패치 도구를 사용하여 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud: DevDocs [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) .

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [품질 패치 도구를 사용하여 Magento 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
