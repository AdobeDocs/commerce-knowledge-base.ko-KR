---
title: 'MDVA-23426 Magento 패치: Outlook에서 첨부 파일로 전송된 이메일'
description: MDVA-23426 Magento 패치는 MS Outlook의 Magento에 의해 전자 메일이 첨부 파일로 전송되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13이 설치된 경우 사용할 수 있습니다. 이 문제는 Magento 2.3.5에서 해결되었습니다.
exl-id: 0b4c3e33-76c5-48b0-b1a8-a967cea11b98
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# MDVA-23426 Magento 패치: Outlook에서 첨부 파일로 전송된 이메일

MDVA-23426 Magento 패치는 MS Outlook의 Magento에 의해 전자 메일이 첨부 파일로 전송되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13이 설치된 경우에 사용할 수 있습니다. 이 문제는 Magento 2.3.5에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Magento 버전:** Magento Commerce Cloud 2.3.3에 대해 패치가 만들어졌습니다.

**Magento 버전과 호환:** Magento Commerce 및 Magento Commerce Cloud 2.3.3 - 2.3.4-p2.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

이메일은 빈 본문과 함께 수신되며 콘텐츠는 첨부 파일로 포함됩니다.

<u>필수 구성 요소:</u> Outlook/Exchange가 클라이언트/서버 조합으로 사용되고 있습니다.

<u>재현 단계:</u> 1. 주문을 제출하면 주문 통지 또는 선적 통지가 발송됩니다.2. 이메일이 수신되었습니다.

<u>실제 결과:</u> 전자 메일의 본문이 비어 있고 전자 메일에 ATT\* 레이블이 지정된 첨부 파일로 포함된 내용이 표시됩니다. <u>예상 결과:</u>

이메일은 첨부 파일 없이 수신되며 이메일 본문에 콘텐츠가 포함됩니다.

## 패치 적용

QPT 패치를 적용하는 방법에 대한 지침은 Magento 제품에 따라 다음 링크를 사용하십시오.

* Magento Commerce: DevDocs [품질 패치 도구를 사용하여 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud: DevDocs [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) .

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [품질 패치 도구 관련 Magento 문제에 대한 패치 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

QPT 도구에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT 도구에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 섹션을 참조하십시오.
