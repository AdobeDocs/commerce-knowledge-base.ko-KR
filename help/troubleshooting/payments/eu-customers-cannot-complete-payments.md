---
title: EU 고객이 지불을 완료할 수 없음
description: 이 문서에서는 유럽 연합의 고객이 결제를 완료할 수 없는 문제를 해결할 수 있는 방법을 제공합니다.
exl-id: 8309d96b-47a3-4d27-b538-e6e3bcdfb7d4
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# EU 고객이 지불을 완료할 수 없음

이 문서에서는 유럽 연합의 고객이 결제를 완료할 수 없는 문제를 해결할 수 있는 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* 클라우드 인프라의 Adobe Commerce, 모든 버전
* Adobe Commerce 온-프레미스 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## 문제

EU의 고객들은 그들의 신용카드 거래가 거절되고 있다고 불평한다.

## 원인

유럽 연합은 결제 서비스 지침(PSD)이라는 규정을 업데이트된 버전 [PSD2](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32015L2366&amp;from=EN)(으)로 수정했습니다. 이는 EU 및 EEA(유럽 경제 지역) 전체에서 결제 서비스 및 결제 서비스 제공업체를 규제하기 위해 시행된 유럽 연합(EU) 지침입니다. SCA(Strong Customer Authentication)는 결제 데이터 보안 및 인증을 강화하기 위해 PSD2에서 요구하는 요구 사항입니다. 결제 솔루션이 지시 요구 사항을 준수하지 않으면 고객이 결제를 완료하지 못할 수 있습니다. 자세한 내용은 [관련 Adobe Commerce 개발자 블로그 게시물](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460)을 참조하세요.

## 솔루션

DevBlog의 [Adobe Commerce 결제 공급자 Recommendations 섹션에서 권장 사항을 따르십시오](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460#recommendations).
