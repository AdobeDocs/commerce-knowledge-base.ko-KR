---
title: Amazon용 패치 Adobe Commerce 2.3.5-p1 의 결제 체크아웃 문제
description: 이 패치는 Adobe Commerce에서 Amazon Pay로 체크아웃하는 동안 결제 위젯에서 "검토 및 결제" 체크아웃 단계에서 결제 방법을 변경할 수 없는 문제를 해결합니다.
exl-id: a241f67f-019c-4ff2-a5ad-e7dc71639768
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Amazon용 패치 Adobe Commerce 2.3.5-p1 의 결제 체크아웃 문제

이 패치는 Adobe Commerce에서 Amazon Pay로 체크아웃하는 동안 결제 위젯에서 &quot;검토 및 결제&quot; 체크아웃 단계에서 결제 방법을 변경할 수 없는 문제를 해결합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce on cloud infrastructure 버전 2.3.5-p1
* Adobe Commerce 온-프레미스 버전 2.3.5-p1

## 문제

쇼핑객이 Amazon 페이로 체크아웃하고 로그인하여 결제 단계로 진행한 후 결제 위젯에서 결제 신용카드를 변경하려고 하면 오류 메시지가 나타납니다. 쇼핑객이 오류를 무시하고 체크아웃을 진행하면 체크아웃을 완료할 수 없습니다.

이 문제를 해결하고 오류를 제거하기 위해 [패치](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)를 만들었습니다.

<u>재현 단계</u>:

1. Amazon Pay로 체크아웃을 시작합니다.
1. Amazon Pay 고객으로 로그인합니다.
1. 배송 방법을 선택하고 결제 단계로 진행합니다.
1. 신용카드를 다른 카드로 바꿔보세요

<u>예상 결과</u>: 다른 신용 카드가 오류 없이 결제 방법으로 선택됩니다.

<u>실제 결과</u>: 오류 메시지가 나타납니다. *&quot;이 판매자에게 문의하여 주문을 완료하십시오.&quot;*

## 솔루션

아래의 [패치를 적용](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)합니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[BUNDLE-2554\_EE\_2.3.5-p1.composer.patch 다운로드](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* Adobe Commerce on cloud infrastructure 버전 2.3.5-p1
* Adobe Commerce 온-프레미스 버전 2.3.5-p1

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* Adobe Commerce on cloud infrastructure 버전 2.3.5
* Adobe Commerce 온-프레미스 버전 2.3.5

## 패치 적용 방법

자세한 내용은 지원 기술 자료에서 [Adobe Commerce에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
