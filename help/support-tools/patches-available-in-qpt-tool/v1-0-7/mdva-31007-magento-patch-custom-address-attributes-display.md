---
title: 'MDVA-31007: 사용자 지정 주소 특성 표시'
description: MDVA-31007 패치는 내 계정 영역 및 백엔드(**Sales &gt; Orders** 위치)의 주문 세부 사항 페이지에 사용자 정의 주소 속성이 올바르게 표시되지 않는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.
exl-id: 43c82b66-395f-4e33-8312-9a1994862f5f
feature: Attributes, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# MDVA-31007: 사용자 지정 주소 특성 표시

MDVA-31007 패치는 내 계정 영역 및 백 엔드(**판매 > 주문** 위치)의 주문 세부 사항 페이지에 사용자 지정 주소 특성이 올바르게 표시되지 않는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7이 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.2에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* 클라우드 인프라의 Adobe Commerce 2.4.0

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. 관리 백엔드에 로그인합니다.
1. **스토어** > **특성** > **고객 주소**&#x200B;로 이동합니다.
1. 다음 두 가지 속성을 만듭니다.

   * 입력 유형 설정: *드롭다운*.
   * 입력 유형 설정: *텍스트*.

1. **스토어** > **구성** > **고객** > **고객 구성**&#x200B;으로 이동합니다.
1. *범위*&#x200B;을(를) **기본 스토어** 보기로 선택하십시오.
1. **주소 템플릿** 섹션을 확장합니다. 위의 두 사용자 지정 특성을 포함하도록 *Text*, *Text One Line* 및 *HTML*&#x200B;을(를) 업데이트합니다.

   ```php
   {{depend testdropdown}}Dropdown: {{var testdropdown}}{{/depend}}    {{depend testtext}}Text: {{var testtext}}{{/depend}}
   ```

1. 상점을 엽니다.
1. 사용자를 만든 후 로그인.
1. **내 계정** > **주소록**(으)로 이동하여 새 주소를 추가합니다(두 개의 사용자 지정 특성을 입력하세요).
1. 장바구니에 제품을 추가하고 주문합니다.
1. 주문 성공 페이지에서 **주문 번호** 링크를 클릭합니다.
1. 주문 세부 사항 페이지에서 **주문 정보** 섹션을 확인하십시오.
1. **백엔드** > **판매** > **주문**(으)로 이동하여 위의 주문을 클릭하고 **주소 정보** 섹션을 확인하십시오.

<u>예상 결과</u>:

프론트엔드와 백엔드에 청구 및 배송 주소가 예상대로 표시됩니다.

<u>실제 결과</u>:

프론트엔드와 백엔드에서 청구 주소가 올바르게 표시되지 않습니다. 드롭다운 속성의 선택한 옵션이 누락되고 입력 속성 값에 속성 코드가 포함되어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
