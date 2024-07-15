---
title: 'MDVA-34695: 제품 및 범주가 표시되지 않음'
description: MDVA-34695 패치는 관리자의 카테고리 그리드에 제품 및 카테고리가 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-34695입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.
exl-id: 0c2e50c1-648b-480a-a768-72af721950d8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-34695: 제품 및 범주가 표시되지 않음

MDVA-34695 패치는 관리자의 카테고리 그리드에 제품 및 카테고리가 표시되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-34695입니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.4

**Adobe Commerce 버전과 호환:**

Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.0-2.4.0-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

범주를 삭제한 후 `children_count`의 음수 값이 데이터베이스에 나타납니다.

<u>재현 단계</u>:

1. 관리 백엔드에 로그인합니다.
1. **카탈로그 > 범주**(으)로 이동합니다.
1. **하위 범주 추가**&#x200B;를 클릭합니다.
1. **범주 이름** = *상위 1*&#x200B;을 설정한 다음 저장합니다.
1. **하위 범주 추가**&#x200B;를 클릭합니다.
1. **범주 이름** = *자식 1*&#x200B;을 설정한 다음 저장합니다.
1. **하위 범주 추가**&#x200B;를 클릭합니다.
1. **범주 이름** = *자식 2*&#x200B;을 설정한 다음 저장합니다.
1. **하위 범주 추가**&#x200B;를 클릭합니다.
1. **범주 이름** = *자식 3*&#x200B;을 설정한 다음 저장합니다. 이때 이 범주의 수준은 *5*&#x200B;이어야 합니다.
1. **자식 1** 범주를 클릭합니다.
1. 범주를 삭제합니다.

<u>예상 결과</u>:

카테고리 그리드는 예상대로 제품 및 카테고리를 표시합니다.

<u>실제 결과</u>:

카테고리 그리드가 비어 있습니다. 데이터베이스에서 `catalog_category_entity` 테이블을 확인합니다. `children_count`이(가) 음수가 되었습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
