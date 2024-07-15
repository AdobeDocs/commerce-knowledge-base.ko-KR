---
title: 엔티티 Adobe Commerce 백엔드를 저장할 수 없음
description: 이 문서에서는 Adobe Commerce 백엔드에서 엔티티를 저장할 수 없는 경우에 대한 솔루션을 제공합니다. 예를 들어 특정 'cart_price' 규칙을 편집하고 저장할 수 없는 경우입니다.
exl-id: e45dc88a-2da0-4524-bd61-6634cfebb169
feature: Admin Workspace, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# 엔티티 Adobe Commerce 백엔드를 저장할 수 없음

이 문서에서는 Adobe Commerce 백엔드에서 엔티티를 저장할 수 없는 경우에 대한 솔루션을 제공합니다. 예를들어, 특정 `cart_price` 규칙을 편집하고 저장할 수 없는 경우

## 영향을 받는 제품 및 버전

이 문제는 최대 세션 크기가 구성된 모든 Adobe Commerce 버전에 영향을 줄 수 있습니다. 이 기능은 Magento Open Source 2.3.7-p1 및 Adobe 상거래(모든 배포 방법) 2.4.3부터 추가되었습니다.


## 문제

저장소를 다시 구성하려고 하면 페이지가 다시 로드되고 변경 사항이 저장되지 않습니다. `var/log/system.log`에서 메시지를 볼 수 있습니다.

*[2021-11-27 00:30:52] 보고서입니다.경고: 세션 크기418056 허용된 세션 최대 크기(256000)를 초과했습니다. [][]*

<u>재현 단계</u>:

저장소 구성의 예가 저장되지 않음:

1. 프로덕션 > **마케팅** > **장바구니 가격 규칙**&#x200B;의 Adobe Commerce 스토어에서 규칙을 선택합니다.
1. 규칙을 선택하고 *비활성*(으)로 설정한 후 변경 내용을 저장합니다.

<u>예상 결과</u>:

규칙이 비활성 상태로 설정되어 있습니다.

<u>실제 결과</u>:

* 아무 메시지 없이 페이지가 다시 로드됩니다.
* 규칙이 여전히 활성으로 설정되어 있습니다.

## 원인

이 문제는 최대 세션 크기에 영향을 준 새로운 기능이 최근에 도입된 것과 관련이 있습니다. 개발자 설명서에서 [세션 관리](https://docs.magento.com/user-guide/stores/security-session-management.html)를 참조하십시오.

## 솔루션

(**스토어** > **구성** > **고급** > **시스템** > **보안** > 최대 세션 크기)에서 &quot;최대 세션 크기&quot; 값을 늘립니다.

## 관련 읽기

* 사용 안내서의 [마케팅 메뉴](https://docs.magento.com/user-guide/marketing/marketing-menu.html).
