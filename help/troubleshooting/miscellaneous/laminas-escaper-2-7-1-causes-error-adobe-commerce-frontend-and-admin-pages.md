---
title: laminas/laminas-escaper 2.7.1로 인해 Adobe Commerce 프론트엔드 및 관리 페이지 오류 발생
description: 이 문서에서는 laminas/laminas-escaper:2.7.1 릴리스로 인해 제품 관리, 카테고리 및 제품 페이지에서 Adobe Commerce의 기능이 손상되는 문제에 대한 해결 방법을 제공합니다. 이 문제는 Adobe Commerce 2.4.3에서 수정됩니다.
exl-id: 89de6827-7b90-4f08-92fb-56ed31ae2672
feature: Admin Workspace, Categories
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# laminas/laminas-escaper 2.7.1로 인해 Adobe Commerce 프론트엔드 및 관리 페이지 오류 발생


## 영향을 받는 제품 및 버전

* Adobe Commerce on Our Cloud Architecture 2.3.5+
* Adobe Commerce 2.3.5+

## 문제

Laminas/laminas-escaper:2.7.1로 업데이트하면 페이지에 오류 메시지가 표시됩니다.

<u>재현 단계</u>:

Laminas/laminas-escaper를 2.7.1로 업데이트합니다.

<u>예상 결과</u>:

오류 없음.

<u>실제 결과</u>:

Laminas/laminas-escaper:2.7.1로 업데이트하면 제품 편집(또는 제품 관리) 페이지에 오류 메시지가 표시됩니다. *TypeError: rawurlencode() 매개 변수 1은 문자열, int가 /var/www/magento/vendor/laminas/laminas-escaper/src/Escaper.php:246*에 제공됩니다.
이 오류는 프론트엔드 및 관리 페이지에서 발생하여 페이지 콘텐츠가 왜곡됩니다.

## 원인

laminas/laminas-escaper 2.7.1은 Escaper 클래스에 대해 엄격한 유형 유효성 검사를 사용하기 시작했습니다.

## 솔루션

각 프로젝트의 루트 디렉터리에서 `composer require laminas/laminas-escaper:2.7.0` 실행

## 관련 읽기

laminas 설명서: [laminas-escaper](https://docs.laminas.dev/laminas-escaper/)
