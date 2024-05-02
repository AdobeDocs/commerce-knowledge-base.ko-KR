---
title: Braintree 결제가 활성화된 경우 책임자가 주문/재주문을 만들 수 없음
description: 이 문서에서는 Braintree 결제 방법이 활성화된 경우 관리자가 고객에 대한 주문이나 재주문을 생성할 수 없는 Adobe Commerce 2.4.5 문제에 대한 패치를 제공합니다.
exl-id: 8840aecb-21d9-4965-8c09-395e2d263aaa
feature: Admin Workspace, Native Luma Frontend Development, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Braintree 결제가 활성화된 경우 책임자가 주문/재주문을 만들 수 없음

이 문서에서는 Braintree 결제 방법이 활성화된 경우 관리자가 고객에 대한 주문이나 재주문을 생성할 수 없는 Adobe Commerce 2.4.5 문제에 대한 패치를 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce 2.4.5
* Adobe Commerce 온-프레미스 2.4.5
* Magento Open Source 2.4.5

## 문제

<u>재현 단계</u>:

1. 핵심 Braintree 통합이 사용됩니다(**스토어** > **구성** > **판매** > **결제 방법** > **Braintree**).
1. Luma Storefront를 사용하여 주문합니다.
1. 관리자 UI로 이동 > **판매**.
1. 고객을 위해 새 주문을 만들거나 이전에 주문한 주문으로 이동하여 을(를) 클릭합니다. **순서 바꾸기**.

<u>예상 결과</u>:

Braintree 결제 방법이 활성화된 경우 관리자는 고객에 대한 주문 및 재주문을 성공적으로 생성할 수 있습니다.

<u>실제 결과</u>:

Braintree 결제 방법이 활성화된 경우 관리자는 고객에 대한 주문이나 재주문을 생성할 수 없으며 다음 오류를 반환합니다.

```bash
report.CRITICAL: Error: Call to a member function getMethodInstance() on null in /app/vendor/paypal/module-braintree-core/Block/Form.php:174
```

## 원인

잘못된 클래스 종속성(`vendor/paypal/module-braintree-core/Block/Form.php`)

## 솔루션

이 문서에 제공된 패치를 적용합니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 다음 링크를 클릭하십시오.

[BUNDLE-3137-composer.patch.zip](assets/BUNDLE-3137-composer.patch.zip)

>[!NOTE]
>
>클라우드 인프라 판매자의 Adobe Commerce에 대한 추가 사항: Adobe은 Commerce 버전 1.0.18의 클라우드 패치에 수정 사항을 포함했습니다. 다음을 참조하십시오. [Commerce용 클라우드 패치 릴리스 노트](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html) 개발자 설명서에서 최신 패키지 적용에 대한 지침을 확인하십시오.

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* 클라우드 인프라의 Adobe Commerce 2.4.5
* Adobe Commerce 온-프레미스 2.4.5
* Magento Open Source 2.4.5

>[!NOTE]
>
>이 패치는 다른 Adobe Commerce 및 Magento Open Source 버전 및 버전과 호환되지 않습니다.

## 패치 적용 방법

다음을 참조하십시오 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 지침에 대해서는 지원 기술 자료에서 참조하십시오.
