---
title: 'MDVA-37913: API를 통해 확장 속성을 업데이트한 후 제품 다운로드 링크가 사라짐'
description: 용 MDVA-37913 패치는 API를 통해 확장 속성을 업데이트한 후 다운로드 가능한 제품 링크가 사라지는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-37913입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: e4b2cf59-5c35-4a28-a63e-15cd7d0d5a5d
feature: REST, Attributes, Extensions, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-37913: API를 통해 확장 속성을 업데이트한 후 제품 다운로드 링크가 사라짐

용 MDVA-37913 패치는 API를 통해 확장 속성을 업데이트한 후 다운로드 가능한 제품 링크가 사라지는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37913입니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.


## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**
클라우드 인프라의 Adobe Commerce 2.3.6

**Adobe Commerce 버전과 호환:**
Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.0 - 2.4.0-p1
>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.


## 문제

API를 통해 확장 속성을 업데이트하면 다운로드 가능한 제품 링크가 사라집니다.

<u>필수 구성 요소</u>:
다운로드 링크가 있는 다운로드 가능한 제품.

<u>재현 단계</u>:

1. 다음과 같은 요청을 사용하여 확장 속성을 업데이트합니다.

```JSON
{
    "product": {
        "extension_attributes": {
            "stock_item": {
                "is_in_stock": true,
                "qty": 100
            }
        }
    }
}
```

<u>예상 결과</u>:<br>
제품이 업데이트되고, 모든 다운로드 링크가 제거되지 않습니다.

<u>실제 결과</u>:<br>
제품이 업데이트되었지만 모든 다운로드 링크가 제거되었습니다.


## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html)

## 관련 읽기

지원 기술 자료의 품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 지원 기술 자료에서 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
