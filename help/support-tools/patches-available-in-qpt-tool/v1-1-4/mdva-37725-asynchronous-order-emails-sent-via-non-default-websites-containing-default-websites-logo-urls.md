---
title: "MDVA-37725: 기본이 아닌 사이트를 통해 전송된 이메일에는 기본 사이트의 로고 URL이 포함되어 있습니다."
description: MDVA-37725 패치는 기본 웹 사이트의 로고 URL이 포함된 비기본 웹 사이트를 통해 비동기 주문 이메일이 전송되는 문제를 해결합니다.
exl-id: c0d1b9a3-01bb-445b-b7da-f9be6952eaeb
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-37725: 기본이 아닌 사이트를 통해 전송된 이메일에는 기본 사이트의 로고 URL이 포함되어 있습니다

>[!WARNING]
>
> MDVA-37725 패치는 더 이상 사용되지 않습니다.

MDVA-37725 패치는 기본 웹 사이트의 로고 URL이 포함된 비기본 웹 사이트를 통해 비동기 주문 이메일이 전송되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4가 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-37725입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.0 - 2.4.3

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

비동기 주문 이메일은 기본 웹 사이트의 로고 URL이 포함된 기본이 아닌 웹 사이트를 통해 전송됩니다.

<u>필수 구성 요소</u>:

1. 두 번째 웹 사이트/스토어/스토어-뷰가 생성되어야 합니다.
1. **비동기 전송** 구성은 **스토어** > **설정** > **구성** > **판매** > **판매 전자 메일** > **일반 설정**&#x200B;에서 사용하도록 설정해야 합니다.
1. **URL에 스토어 코드 추가** 구성이 설정되어 있으므로 **스토어** > **설정** > **구성** > **URL 옵션**&#x200B;에서 보조 웹 사이트에 쉽게 액세스할 수 있습니다.

<u>재현 단계</u>:

1. 첫 번째 상점과 두 번째 상점에서 모두 주문합니다.
1. cron 을 실행하여 영업 이메일을 전송합니다.
1. 두 번째 웹 사이트에서 보낸 이메일을 확인합니다.

<u>예상 결과</u>:

이메일의 로고 URL에는 두 번째 웹 사이트의 URL이 포함되어 있습니다.

<u>실제 결과</u>:

이메일의 로고 URL에는 기본 웹 사이트의 URL이 포함되어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
