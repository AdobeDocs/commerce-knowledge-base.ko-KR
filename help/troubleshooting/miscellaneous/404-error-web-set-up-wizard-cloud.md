---
title: 관리 패널을 통해 웹 설치 마법사에 액세스할 때 404 찾을 수 없음 오류
description: 이 문서에서는 관리 패널을 통해 웹 설치 마법사에 액세스하려고 할 때 404 찾을 수 없음 오류가 발생하는 경우에 대한 해결 방법을 제공합니다.
exl-id: 1b89da58-c872-481b-b2a0-aa48db8223db
feature: Admin Workspace, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# 관리 패널을 통해 웹 설치 마법사에 액세스할 때 404 찾을 수 없음 오류

이 문서에서는 관리 패널을 통해 웹 설치 마법사에 액세스하려고 할 때 404 찾을 수 없음 오류가 발생하는 경우에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* 웹 설치 마법사 기능은 Adobe Commerce(모든 배포 메서드) 2.3.6에서 더 이상 사용되지 않으며 2.4.0에서 제거되었습니다.

## 문제

웹 설치 마법사를 사용하여 확장을 설치하면 404 페이지가 표시됩니다.

<u>재현 단계</u>:

판매자가 웹 설치 마법사를 클릭하여 새 모듈/통합을 설치합니다.

<u>예상 결과</u>:

모듈/통합 설치

<u>실제 결과</u>:

404 오류가 표시됩니다.

## 원인

클라우드 인프라 인스턴스의 모든 Adobe Commerce에 대해 웹 설치 마법사가 비활성화되었습니다. 웹 설치 마법사를 활성화할 수 없습니다. Composer를 통해 확장을 설치해야 합니다.

## 솔루션

이 기능은 클라우드 인프라의 Adobe Commerce에서 비활성화됩니다.

업데이트를 수행하거나 클라우드 인프라에 Adobe Commerce용 외부 모듈을 설치하는 방법에 대한 자세한 내용은 개발자 설명서에서 [확장 설치, 관리 및 업그레이드](https://devdocs.magento.com/cloud/howtos/install-components.html)를 참조하십시오.
Adobe Commerce 온-프레미스에 대한 업데이트를 수행하거나 외부 모듈을 설치하는 방법에 대한 자세한 내용은 개발자 설명서에서 [빠른 시작 설치](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html)를 참조하십시오.

## 관련 읽기

* 개발자 설명서에서 [확장 설치](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension)를 참조하십시오.
