---
title: Adobe Commerce 2.4.0 Braintree 가상 터미널 페이지가 손상됨
description: 이 문서에서는 Braintree 가상 터미널 페이지가 적절한 UI 요소를 로드하지 않거나 Braintree이 구성되지 않은 경우 적절한 오류 메시지가 표시되는 알려진 Adobe Commerce 2.4.0 문제에 대한 패치를 제공합니다.
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 Braintree 가상 터미널 페이지가 손상됨

이 문서에서는 Braintree 가상 터미널 페이지가 적절한 UI 요소를 로드하지 않거나 Braintree이 구성되지 않은 경우 적절한 오류 메시지가 표시되는 알려진 Adobe Commerce 2.4.0 문제에 대한 패치를 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.0
* 클라우드 인프라의 Adobe Commerce 2.4.0

## 문제

### 시나리오 1: Braintree 결제 방법이 구성됨

<u>재현 단계:</u>

Commerce 관리에서 **판매** > **가상 터미널 Braintree**(으)로 이동합니다 **&#x200B; **

<u>예상 결과:</u>

**Braintree 가상 터미널** 페이지가 적절한 UI를 사용하여 로드됩니다.

<u>실제 결과:</u>

**가상 터미널 Braintree** 페이지의 UI가 손상되었습니다.

### 시나리오 2: Braintree 결제 방법이 구성됨

<u>재현 단계:</u>

Commerce 관리에서 **판매** > **가상 터미널 Braintree**(으)로 이동합니다 **&#x200B; **

<u>예상 결과:</u>

**Braintree 가상 터미널** 페이지가 적절한 UI와 함께 로드되고 Braintree이 아직 구성되지 않았음을 알리는 경고가 표시됩니다.

<u>실제 결과:</u>

**Braintree 가상 터미널** 페이지의 UI가 손상되어 경고가 표시되지 않습니다.

## 솔루션

이 문서에 제공된 패치를 적용합니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[BUNDLE-2670-composer.patch](assets/BUNDLE-2670-composer.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* 클라우드 인프라의 Adobe Commerce 2.4.0
* Adobe Commerce 온-프레미스 2.4.0

## 패치 적용 방법

지침은 [Adobe에서 제공한 작성기 패치 적용 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
