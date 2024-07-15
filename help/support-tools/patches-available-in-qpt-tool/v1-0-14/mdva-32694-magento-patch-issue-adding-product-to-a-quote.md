---
title: 'MDVA-32694 패치: 견적에 제품 추가 문제 발생'
description: MDVA-32694 패치를 사용하면 관리자가 아닌 웹 사이트에서 만든 협상 가능 견적에 유효한 제품을 추가할 수 없는 문제가 해결됩니다.
exl-id: 964abbbd-c8b1-4645-a393-7283f52e94ff
feature: Products, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-32694 패치: 견적에 제품 추가 문제 발생

MDVA-32694 패치를 사용하면 관리자가 아닌 웹 사이트에서 만든 협상 가능 견적에 유효한 제품을 추가할 수 없는 문제가 해결됩니다.

이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

B2B 버전 1.2가 있는 클라우드 인프라 2.3.2의 Adobe Commerce

**Adobe Commerce 버전과 호환:**

Adobe Commerce 온 클라우드 인프라 및 Adobe Commerce 온-프레미스 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>필수 구성 요소</u>:

B2B를 사용하여 새 Adobe Commerce 인스턴스를 설치합니다.

<u>재현 단계</u>:

1. **스토어 > 구성 > 일반 > B2B 기능**(으)로 이동하여 **회사** 및 **B2B 견적**&#x200B;을 사용하도록 설정합니다.
1. **스토어** 및 **스토어뷰**&#x200B;을(를) 사용하여 웹 사이트 2개를 더 만듭니다(총 3개: *기본*, *웹 사이트2*, *웹 사이트3*).
1. 간단한 제품을 만들어 *website3*&#x200B;에만 할당합니다.
1. **스토어 > 모든 스토어**(으)로 이동하여 *웹 사이트3*&#x200B;을(를) **기본**(으)로 설정합니다.
1. 프론트엔드로 이동하여 *website3*&#x200B;에서 새 회사를 만드십시오.
1. 이전에 만든 제품을 장바구니에 추가하고 새 협상가능한 견적을 만듭니다.
1. **스토어 > 모든 스토어**(으)로 이동하여 &quot;*기본*&quot; 웹 사이트를 **기본**(으)로 다시 설정합니다.
1. **판매 > 견적 > 이전에 만든 견적 열기**(으)로 이동하여 동일한 제품을 추가해 보십시오.

<u>예상 결과</u>:

관리자는 예상대로 동일한 제품을 견적에 추가할 수 있습니다.

<u>실제 결과</u>:

관리자가 동일한 제품을 견적에 추가할 수 없으며, 다음과 같은 오류 메시지가 표시됩니다.

```php
This product is assigned to another website.
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
