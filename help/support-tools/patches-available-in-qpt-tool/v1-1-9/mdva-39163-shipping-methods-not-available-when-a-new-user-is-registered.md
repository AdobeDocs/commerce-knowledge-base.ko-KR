---
title: 'MDVA-39163: 게스트 세션의 제품을 사용하여 새로 등록된 사용자는 배송 방법을 사용할 수 없음'
description: MDVA-39163 패치는 새 사용자가 등록되고 장바구니의 제품이 게스트 세션에서 제공된 경우 배송 방법을 사용할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-39163입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: f8661a4e-5832-41bb-be3d-4ea6c863fdb9
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# MDVA-39163: 게스트 세션의 제품을 사용하여 새로 등록된 사용자는 배송 방법을 사용할 수 없습니다.

MDVA-39163 패치는 새 사용자가 등록되고 장바구니의 제품이 게스트 세션에서 제공된 경우 배송 방법을 사용할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-39163입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

신규 사용자가 등록되고 장바구니의 제품이 게스트 세션의 제품인 경우 배송 방법을 사용할 수 없습니다.

<u>재현 단계</u>:

1. **관리자** > **스토어** > **구성** > **판매** > **게재 방법**&#x200B;으로 이동합니다. **정액 요금** 배송 방법만 사용하도록 설정하고 그 외의 모든 방법은 사용하지 않도록 설정하십시오.
1. **정액 요금** 배송 방법에서 **해당 국가로 배송** 설정에서 사용할 수 있는 **특정** 국가 옵션을 선택하고 목록에서 한 국가(예: 미국)를 선택하십시오.
1. **관리자** > **스토어** > **구성** > **고객** > **고객 구성**(으)로 이동하여 **전자 메일 확인 필요**&#x200B;를 _예_(으)로 설정합니다.
1. **관리자** > **마케팅** > **이메일 템플릿**&#x200B;에서 새 이메일 템플릿을 만들고 `Footer (magento/luma)` 템플릿을 로드하고 템플릿 콘텐츠를 CMS 블록으로 바꿉니다.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. **관리자** > **콘텐츠** > **디자인** > **구성**(으)로 이동하여 프론트엔드 웹 사이트와 관련된 테마를 선택하십시오. &quot;바닥글 템플릿&quot;을 새로 만든 전자 메일 템플릿으로 설정합니다.
1. 프론트엔드로 이동하여 제품을 장바구니에 추가합니다.
1. 고객을 만듭니다. 이메일 주소를 확인하는 이메일을 받게 됩니다. 확인 링크를 클릭합니다. 웹 사이트에 로그인됩니다.
1. **내 계정**(으)로 이동하여 주소를 추가하십시오. 주소 국가를 이전에 관리자 구성에서 설정한 배송 국가로 설정합니다.
1. 체크아웃으로 이동합니다.

<u>예상 결과</u>:

고객이 배송 국가와 호환되는 주소를 가지고 있어 배송 방법을 이용할 수 있습니다.

<u>실제 결과</u>:

배송 방법을 사용할 수 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
