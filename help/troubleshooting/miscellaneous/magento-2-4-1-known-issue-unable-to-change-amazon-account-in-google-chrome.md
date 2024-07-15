---
title: 'Adobe Commerce 2.4.1 문제: Chrome에서 Amazon 계정을 변경할 수 없음'
description: 이 문서에서는 체크아웃 중에 Adobe Commerce Pay를 사용할 때 고객이 로그인 제안 대신 이전에 사용한 Amazon 계정에 로그인하는 알려진 Amazon 2.4.1 문제에 대해 설명합니다.
exl-id: 8acffe99-b3ec-4b45-9434-61b66e963838
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 문제: Chrome에서 Amazon 계정을 변경할 수 없음

이 문서에서는 체크아웃 중에 Adobe Commerce Pay를 사용할 때 고객이 로그인 제안 대신 이전에 사용한 Amazon 계정에 로그인하는 알려진 Amazon 2.4.1 문제에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.4.1
* 클라우드 인프라의 Adobe Commerce 2.4.1

## 문제

체크아웃 중에 Amazon Pay를 사용하면 고객에게 로그인하라는 메시지가 표시되지 않고 이전에 사용한 Amazon 계정에 로그인하게 됩니다.

<u>재현 단계:</u>

1. 상점 첫 화면에서 장바구니에 항목을 추가하고 게스트 체크아웃을 진행합니다.
1. **Amazon 결제** 단추를 클릭합니다. Amazon.com 로그인 팝업이 나타납니다.
1. Amazon 계정에 로그인합니다.
1. 주소를 선택하고 **다음**&#x200B;을 클릭하세요.
1. 결제 방법을 선택합니다.
1. **주문**&#x200B;을 클릭하세요.
1. 홈 페이지로 돌아가서 스토어 계정에 로그인합니다.
1. 장바구니에 항목을 다시 추가하고 체크아웃을 진행합니다.
1. **Amazon 결제** 단추를 클릭합니다.

<u>실제 결과:</u>

이전에 사용한 (3단계) Amazon 계정에 다시 자동으로 로그인됩니다.

<u>예상 결과:</u>

Amazon.com 로그인 팝업이 나타나고 Amazon 페이에 로그인하거나 새 계정을 만들 수 있습니다.

## 원인

이 문제는 다음 중 한 상황에서 발생할 수 있습니다.

* `SameSite` 쿠키 값이 `LAX`인 경우 쿠키는 타사 호출의 일부로 전송되지 않습니다.
* Mozilla Firefox 콘텐츠 차단 기능은 스크립트와 클라이언트측 스토리지 메커니즘의 사용을 차단하여 타사에서 브라우저 사용자의 활동을 추적하는 것을 방지합니다. Firefox는 외부 공급업체인 Disconnect.me를 사용하여 차단할 추적 사이트 목록을 제공합니다. Amazon Pay는 로그인 및 렌더링 주소 및 지갑 위젯 후에 액세스 토큰을 반환하기 위해 서드파티 웹 사이트의 iframe을 사용합니다. 콘텐츠 차단 기능을 사용하면 Amazon Pay iframe 로드 요청이 서드파티 추적 요청으로 간주되어 차단되므로 구매자가 체크아웃을 진행할 수 없습니다.
* 서드파티 쿠키 또는 JS가 브라우저에 의해 명시적으로 차단되는 모든 상황.

## 솔루션

Amazon Pay iframe 요청이 브라우저에 의해 차단되지 않았는지 확인하십시오.
