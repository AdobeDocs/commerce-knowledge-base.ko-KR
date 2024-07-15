---
title: 광고 차단기가 활성화된 경우 체크아웃 페이지가 로드되지 않음
description: 이 문서에서는 uBlock 또는 기타 광고 차단기로 인한 체크아웃 페이지 로드 실패와 관련된 클라우드 인프라의 알려진 Adobe Commerce 2.2.2 문제에 대한 패치를 제공합니다.
exl-id: fe718f21-df23-4ab1-a6b0-03bad4d7095d
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# 광고 차단기가 활성화된 경우 체크아웃 페이지가 로드되지 않음

이 문서에서는 uBlock 또는 기타 광고 차단기로 인한 체크아웃 페이지 로드 실패와 관련된 클라우드 인프라의 알려진 Adobe Commerce 2.2.2 문제에 대한 패치를 제공합니다.

## 문제

저장소에 대해 Google Analytics을 사용할 수 있는 경우 설치된 uBlock 또는 다른 광고 차단기가 있는 고객이 체크아웃을 진행할 때 `trackingCode.js` 파일이 로드되지 않도록 차단되고 RequireJS가 JS 실행 흐름을 중단합니다. 이로 인해 체크아웃 페이지를 로드하는 데 문제가 발생합니다.

<u>재현 단계</u>:

사전 요구 사항: 광고 차단기가 설치되어 있고 브라우저에 활성화되어 있어야 합니다.

1. Commerce 관리에서 Google Analytics 기능을 활성화하고 구성합니다.
1. 상점 첫 화면에서 제품 페이지를 엽니다.
1. 장바구니에 제품을 추가합니다.
1. **체크아웃으로 이동** 링크를 클릭합니다.

<u>예상 결과</u>: 체크아웃 페이지가 로드되고 고객이 체크아웃을 완료할 수 있습니다.

<u>실제 결과</u>: 체크아웃 페이지가 로드되지 않습니다. 로드하는 회전자가 사라지지 않습니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-9353\_EE\_2.2.2\_v1.composer.patch 다운로드](assets/MDVA-9353_EE_2.2.2_v1.composer.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* 클라우드 인프라의 Adobe Commerce 2.2.2

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* 2.1.0에서 2.1.14로 클라우드 인프라의 Adobe Commerce
* 2.2.0에서 2.2.1로, 2.2.3에서 2.2.5로 클라우드 인프라의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.1.0 ~ 2.1.14
* Adobe Commerce 온-프레미스 2.2.0 - 2.2.5

## 패치 적용 방법

지침은 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 유용한 링크

* [GitHub에서 논의된 문제](https://github.com/magento/magento2/pull/13061)

## 첨부 파일
