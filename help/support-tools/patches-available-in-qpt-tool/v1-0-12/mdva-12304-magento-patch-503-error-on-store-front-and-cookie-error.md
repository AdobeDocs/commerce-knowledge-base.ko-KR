---
title: 'MDVA-12304: 스토어 전면 및 쿠키 오류에 503 오류'
description: 이 MDVA-12304 Adobe Commerce 패치는 *쿠키를 보낼 수 없음*으로 스토어 전면에서 503 오류를 해결합니다. 최대 쿠키 수를 초과했습니다.* 로그에 오류 메시지가 표시됩니다. 이는 알려진 Adobe Commerce 2.2.5 문제입니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12가 설치된 경우 사용할 수 있습니다.
exl-id: b4b1a2f7-f328-488f-86b8-576b908792fb
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# MDVA-12304: 스토어 전면 및 쿠키 오류에 503 오류가 발생했습니다.

이 MDVA-12304 Adobe Commerce 패치는 스토어 전면에서 503 오류를 해결합니다. *쿠키를 보낼 수 없습니다. 최대 쿠키 수를 초과했습니다.로그에 오류 메시지가*&#x200B;개 있습니다. 이는 알려진 Adobe Commerce 2.2.5 문제입니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12가 설치된 경우에 사용할 수 있습니다.

## 영향을 받는 제품 및 버전

* **Adobe Commerce 버전에 대한 패치가 만들어졌습니다.** Adobe Commerce 온-프레미스 2.2.5.
* **Adobe Commerce 버전과 호환:** Adobe Commerce(모든 배포 방법) 2.x.x.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

고객이 상점 전면을 탐색할 때 503 오류가 발생합니다. `var/log/exception.log` 파일에 다음 오류 메시지가 있습니다. *쿠키를 보낼 수 없습니다. 최대 쿠키 수를 초과했습니다.*

이 문제는 Adobe Commerce 기본 쿠키 제한이 50으로 설정되어 있고 클라이언트의 브라우저가 제한에 도달하면 Commerce에서 예외를 throw하기 때문에 발생합니다. 패치에 제공되는 솔루션은 쿠키 제한을 200개로 늘립니다.

<u>재현 단계:</u>

고객이 장바구니에 로그인하여 보려고 하면 언제든지 503 오류가 표시될 수 있습니다.

`var/log/exception.log` 파일에 다음 오류 메시지가 있습니다. *쿠키를 보낼 수 없습니다. 최대 쿠키 수를 초과했습니다.*

<u>실제 결과:</u> 고객이 장바구니를 확인하거나 주문을 완료할 수 없습니다.

<u>예상 결과:</u> 고객은 장바구니를 확인하고 주문을 완료할 수 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).


## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
