---
title: "MDVA-22026: 외부 URL에서 제품 이미지를 가져올 수 없음"
description: MDVA-22026 패치는 외부 URL에서 제품 이미지를 가져올 수 없는 문제를 해결했습니다.
exl-id: 29043c6c-daf2-4925-85bf-49eeeee3742c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# MDVA-22026: 외부 URL에서 제품 이미지를 가져올 수 없음

MDVA-22026 패치는 외부 URL에서 제품 이미지를 가져올 수 없는 문제를 해결했습니다.

이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-22026입니다. 이 문제는 Adobe Commerce 버전 2.3.4에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전용 패치가 만들어졌습니다.** 클라우드 인프라 2.3.2-p2의 Adobe Commerce

**Adobe Commerce 버전과 호환:** Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.2-2.3.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. 관리에서 **시스템** > **가져오기**(으)로 이동합니다.
1. **엔터티 형식** = *제품*&#x200B;을 설정합니다.
1. **가져오기 동작** = *추가/업데이트*&#x200B;를 설정합니다.
1. **허용되는 오류 수** = *10000*&#x200B;을(를) 설정합니다.
1. 가져올 파일을 선택합니다.
1. **데이터 확인** 단추를 클릭합니다(파일의 유효성을 검사해야 함).
1. **가져오기** 단추를 클릭합니다.

<u>예상 결과</u>:

예상대로 외부 URL의 이미지를 포함하여 CSV 파일에서 제품을 성공적으로 가져왔습니다.

<u>실제 결과</u>:

외부 URL의 이미지를 포함하여 CSV 파일에서 제품을 가져오지 못했으며 유사한 오류가 수신됩니다.

```php
1. Imported resource (image) could not be downloaded from external resource due to timeout or access permissions in row(s): 4, 5, 8, 9, 16, 18, 20, 21, 22, 23, 26, 27, 28, 52, 53, 55, 58, 63, 70, 71, 77, 78, 83, 84, 91
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html).
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [품질 패치 도구로 Adobe Commerce 문제를 검사하십시오](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
