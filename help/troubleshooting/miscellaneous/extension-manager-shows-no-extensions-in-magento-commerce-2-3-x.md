---
title: Extension Manager에 Adobe Commerce 2.3.x에 확장이 표시되지 않음
description: 이 문서에서는 Commerce Marketplace을 통해 확장을 구매한 후 Adobe Commerce 2.3.x의 관리 Extension Manager에서 확장이 누락되는 해결 방법을 제공합니다.
exl-id: bed8506d-39b9-449a-891b-466d214a0fe8
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Extension Manager에 Adobe Commerce 2.3.x에 확장이 표시되지 않음

이 문서에서는 Commerce Marketplace을 통해 확장을 구매한 후 Adobe Commerce 2.3.x의 관리 Extension Manager에서 확장이 누락되는 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 버전(모든 배포 방법) 2.3.x

## 문제

Commerce Marketplace을 통해 확장을 구입할 때 핵심 Adobe Commerce Extension Manager을 사용하여 확장을 설치할 수 없습니다. 액세스 키를 추가하고 Marketplace에 동기화하면 Extension Manager에 확장이 표시되지 않습니다.

이 문제에 대한 **해결 방법**&#x200B;은(는) 개발자 설명서에서 [일반 CLI 설치](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions)와(과) 같이 명령줄 Adobe Commerce 설치를 사용하는 것입니다.

<u>재현 단계</u>:

1. Commerce Marketplace을 통해 확장을 구매합니다.
1. 확장의 액세스 키를 추가하고 Marketplace에 동기화합니다.
1. 관리자의 Extension Manager 섹션으로 이동합니다.

<u>예상 결과</u>:

확장은 Commerce 관리자의 Extension Manager 섹션에 표시됩니다.

<u>실제 결과</u>:

**아래 이미지와 유사한 확장이 Commerce 관리자의 Extension Manager 섹션에 표시되지 않습니다.**


![KB-607_Image_1.png](assets/KB-607_Image_1.png)

## 해결 방법

개발자 설명서에서 [일반 CLI 설치](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions)와 같이 명령줄 Adobe Commerce 설치를 사용합니다.
