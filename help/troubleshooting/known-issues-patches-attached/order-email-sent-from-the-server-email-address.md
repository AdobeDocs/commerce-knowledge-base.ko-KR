---
title: 서버 이메일 주소에서 보낸 주문 이메일
description: 이 문서에서는 서버 이메일 주소에서 전송되는 주문 이메일과 관련된 클라우드 인프라의 알려진 Adobe Commerce 2.2.4 문제에 대한 패치를 제공합니다.
exl-id: f32e0c09-e19e-4269-bbba-0533d74a7f49
feature: Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# 서버 이메일 주소에서 보낸 주문 이메일

이 문서에서는 서버 이메일 주소에서 전송되는 주문 이메일과 관련된 클라우드 인프라의 알려진 Adobe Commerce 2.2.4 문제에 대한 패치를 제공합니다.

## 문제

주문 확인 이메일은 Apache 서버 이메일 주소에서 전송됩니다. 다른 이메일(암호 찾기 등)은 구성된 이메일 주소에서 전송됩니다.

<u>재현 단계</u>:

1. **주문 보내기 확인** 상자를 선택한 상태로 주문합니다.
1. 이메일을 확인합니다.

<u>예상 결과</u>:

Adobe Commerce에서 구성한 전송 주소에서 이메일을 보냈습니다.

<u>실제 결과</u>:

사용 중인 Apache 서버에 구성된 이메일 주소에서 이메일을 보냈습니다.

## 패치

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-10993\_EE\_2.2.4\_v1.composer.patch 다운로드](assets/MDVA-10993_EE_2.2.4_v1.composer.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* 클라우드 인프라의 Adobe Commerce 2.2.4

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* 클라우드 인프라의 Adobe Commerce 2.2.5
* 클라우드 인프라의 Adobe Commerce 2.2.6
* 클라우드 인프라의 Adobe Commerce 2.2.7
* 클라우드 인프라의 Adobe Commerce 2.2.8
* Adobe Commerce 온-프레미스 2.2.4
* Adobe Commerce 온-프레미스 2.2.5
* Adobe Commerce 온-프레미스 2.2.6
* Adobe Commerce 온-프레미스 2.2.7
* Adobe Commerce 온-프레미스 2.2.8
* Adobe Commerce 온-프레미스 2.3.0

## 패치 적용 방법

지침은 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
