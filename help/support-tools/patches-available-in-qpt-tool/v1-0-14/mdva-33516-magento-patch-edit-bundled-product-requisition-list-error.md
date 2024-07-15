---
title: 'MDVA-33516 패치: 번들 제품 구매요청 목록 오류 편집'
description: MDVA-33516 패치는 구매요청 목록에서 번들 제품 유형을 편집할 때 구매요청 목록 품목 오류 페이지로 리디렉션되는 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14가 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: 76a16982-f977-4674-b05e-23f4ac355d52
feature: B2B, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-33516 패치: 번들 제품 구매요청 목록 편집 오류

MDVA-33516 패치는 구매요청 목록에서 번들 제품 유형을 편집할 때 구매요청 목록 품목 오류 페이지로 리디렉션되는 문제를 수정합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.4

**Adobe Commerce 버전과 호환:**

클라우드 인프라의 Adobe Commerce 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

구매요청 목록에서 번들 제품을 편집하는 동안 오류가 발생했습니다.

<u>필수 구성 요소</u>:

* B2B가 설치되었습니다.
* 구매요청 목록을 사용할 수 있습니다.

<u>재현 단계</u>:

1. 간단한 두 가지 제품으로 묶음 제품을 만듭니다.
1. 번들 제품 페이지로 이동하여 **사용자 지정 및 장바구니에 추가** 단추를 클릭합니다.
1. 드롭다운에서 옵션 중 하나를 선택하고 **구매요청 목록에 추가**&#x200B;를 클릭하여 새 구매요청 목록을 만듭니다. 자세한 단계는 사용 안내서의 [Magento 사용 안내서 > 내 구매요청 목록 > 구매요청 목록 만들기](https://docs.magento.com/user-guide/customers/account-dashboard-requisition-lists.html#create-a-requisition-list)를 참조하십시오.
1. 새로 만든 구매요청 목록(내 계정 > **내 구매요청 목록**)으로 이동합니다.
1. *작업* 열에서 **보기** 단추를 클릭합니다.
1. **편집** 단추를 클릭합니다.

<u>예상 결과</u>:<br>

오류 없음.

<u>실제 결과</u>:

번들 제품의 그림, 가격 및 다음 오류 메시지가 포함된 &quot;사용자 지정&quot; 페이지:

```
Fatal error: Uncaught Error: Call to a member function isAvailableForCompare() on null in /var/www/html/var/view_preprocessed/pub/static/vendor/magento/module-catalog/view/frontend/templates/product/view/addto/compare.phtml:1 Stack trace: #0 /var/www/html/vendor/magento/framework/View/TemplateEngine/Php.php(59): include() #1 /var/www/html/vendor/magento/framework/View/Element/Template.php(271): Magento\Framework\View\TemplateEngine\Php->render(Object(Magento\Catalog\Block\Product\View\AddTo\Compare), '/var/www/html/v...', Array) #2 /var/www/html/vendor/magento/framework/View/Element/Template.php(301): Magento\Framework\View\Element\Template->fetchView('/var/www/html/v...') #3 /var/www/html/vendor/magento/framework/View/Element/AbstractBlock.php(1099): Magento\Framework\View\Element\Template->_toHtml() #4 /var/www/html/vendor/magento/framework/View/Element/AbstractBlock.php(1103): Magento\Framework\View\Element\AbstractBlock->Magento\Framework\View\Element   {closure} () #5 /var/www/html/vendor/magento/framework/View/Element/ in /var/www/html/var/view_preprocessed/pub/static/vendor/magento/module-catalog/view/frontend/templates/product/view/addto/compare.phtml
  on line 1
```

## 패치 적용

개별 패치를 적용하려면 Adobe Commerce 제품에 따라 다음 링크를 사용하십시오.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
