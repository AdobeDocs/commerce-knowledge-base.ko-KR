---
title: 'MDVA-28511: 액센트 문자로 인해 Payflow 결제가 중단됨'
description: MDVA-28511 패치는 **Payflow Pro**를 통한 지불이 악센트 부호가 있는 고객 이름에 대해 완료되지 않을 때 문제를 해결합니다.
exl-id: ecc827e3-2a1c-4f32-a0e2-9c5792483e7d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-28511: 액센트 문자가 Payflow 결제를 중단함

MDVA-28511 패치는 **Payflow Pro**&#x200B;을(를) 통한 결제가 액센트 문자가 있는 고객 이름에 대해 완료되지 않을 때 문제를 해결합니다.

이 패치는 [품질 패치 도구(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14가 설치된 경우에 사용할 수 있습니다. 이 문제는 Adobe Commerce 버전 2.3.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce Adobe Commerce 버전에 대한 패치가 만들어졌습니다.** 클라우드 인프라 2.3.5-p1

**Adobe Commerce 버전과 호환:** Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>필수 구성 요소</u>:

**Payflow Pro** 신용 카드 결제 방법을 사용합니다.

<u>재현 단계</u>:

1. 장바구니에 제품을 추가하고 체크아웃 페이지로 이동합니다.
1. 악센트 부호가 있는 문자로 고객 이름을 설정합니다. (예: **Ãenne Ãillin**)
1. 결제 단계를 계속 진행합니다.
1. **Payflow Pro**&#x200B;을(를) **신용 카드**(으)로 선택하고 신용 카드 세부 정보를 입력하십시오.
1. **주문** 단추를 클릭합니다.

<u>예상 결과</u>:

예상대로 주문은 문제 없이 완료됩니다.

<u>실제 결과</u>:

주문이 완료되지 않고 로그에 이 예제와 유사한 오류가 표시됩니다.

```php
[2020-06-12 07:50:23] report.CRITICAL: String to be escaped was not valid UTF-8 or could not be converted: �?tienne �?illini [] []
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [QPT에서 사용할 수 있는 패치](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 섹션을 참조하십시오.
