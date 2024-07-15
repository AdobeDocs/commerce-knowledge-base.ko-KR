---
title: 모듈 비활성화 후 문제 발생
description: 이 문서에서는 Commerce 관리에서 모듈 출력을 비활성화한 후 발생하는 모듈 기능 문제에 대한 해결 방법을 제공합니다.
exl-id: 517f6993-f09e-4a94-8c57-175ecf9a98a8
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# 모듈 비활성화 후 문제 발생

이 문서에서는 Commerce 관리에서 모듈 출력을 비활성화한 후 발생하는 모듈 기능 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* cloud infrastructure 2.1.X 이하 버전의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.1.X 이하

## 문제

Commerce 관리자의 **스토어** > **설정** > **구성** > 고급 > **고급**&#x200B;에서 모듈 출력을 비활성화하면 모듈 기능과 관련된 문제가 표시될 수 있습니다.

## 원인

**스토어** > **설정** > **구성** > 고급 > **고급**&#x200B;에서 모듈 출력을 비활성화하면 출력(HTML, JS)만 비활성화되지만 이 모듈의 기능은 비활성화되지 않습니다.

## 솔루션

모듈 기능을 사용하지 않도록 설정하려면 개발자 설명서의 [모듈 사용 또는 사용 안 함](https://devdocs.magento.com/guides/v2.1/install-gde/install/cli/install-cli-subcommands-enable.html)에 설명된 대로 모듈을 사용하지 않도록 설정하십시오.

버전 2.2.0부터 모듈 출력 비활성화 기능이 제거되었습니다.
