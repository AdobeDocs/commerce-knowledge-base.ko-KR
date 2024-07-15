---
title: 'MDVA-32012 패치: S. 한국어 및 아르헨티나 우편 번호 유효성 검사'
description: MDVA-32012 패치는 국가 우편 번호 형식이 변경되거나 변경되어 아르헨티나 우편 번호와 대한민국 우편 번호가 확인되지 않는 문제를 해결합니다. 한국의 우편 번호는 이제 5자리여야 하지만, 이전에는 6자리였습니다. 아르헨티나 우편 번호는 숫자와 영숫자를 모두 사용할 수 있습니다. MDVA-32012 패치는 우편 번호 값에 대한 이러한 형식이 이러한 국가에 대해 유효함을 의미합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9가 설치된 경우 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 수정됩니다.
exl-id: 9602f50d-6acd-4724-9734-6aeb65393a25
feature: Communications
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# MDVA-32012 패치: 한국어 및 아르헨티나 우편 번호 유효성 검사

MDVA-32012 패치는 국가 우편 번호 형식이 변경되거나 변경되어 아르헨티나 우편 번호와 대한민국 우편 번호가 확인되지 않는 문제를 해결합니다. 한국의 우편 번호는 이제 5자리여야 하지만, 이전에는 6자리였습니다. 아르헨티나 우편 번호는 숫자와 영숫자를 모두 사용할 수 있습니다. MDVA-32012 패치는 우편 번호 값에 대한 이러한 형식이 이러한 국가에 대해 유효함을 의미합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.4.2에서 수정됩니다.

## 영향을 받는 제품 및 버전

* 이 패치는 클라우드 인프라 2.3.5의 Adobe Commerce용으로 설계되었습니다.
* 이 패치는 Adobe Commerce 버전인 Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.0 - 2.4.1과도 호환됩니다.

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

5자리 한국 또는 영숫자 아르헨티나의 우편번호를 입력하면 경고가 표시됩니다.

*입력한 우편 번호가 잘못된 것 같습니다. 예: [1234(영숫자 아르헨티나 주소를 입력한 경우)] 또는 [123-456(5자리 한국 주소를 입력한 경우)]. 올바른 알림이라고 생각되면 이 알림을 무시할 수 있습니다.*

<u>재현 단계</u>:

1. 가게 문 열어
1. 장바구니에 항목 추가.
1. 체크아웃을 처리합니다.
1. 한국에 해당 국가에 대한 새 주소를 추가하고 5자리 우편번호를 입력하거나 아르헨티나에 해당 국가에 대한 새 주소를 추가하고 영숫자 우편번호를 입력합니다.
1. 저장해 보십시오.

<u>예상 결과</u>:

주소는 경고 없이 저장해야 합니다.

<u>실제 결과</u>:

주소를 저장하면 경고가 반환됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
