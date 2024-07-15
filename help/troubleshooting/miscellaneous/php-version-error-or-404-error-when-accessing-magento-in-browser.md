---
title: 브라우저에서 Adobe Commerce에 액세스할 때 PHP 버전 오류 또는 404 오류 발생
description: 이 문서에서는 웹 브라우저에서 Adobe Commerce 인스턴스에 액세스할 수 없고 404 오류 또는 "지원되지 않는 PHP 버전" 오류가 발생하는 문제에 대한 해결 방법을 제공합니다.
exl-id: 6cfdeaae-5e52-411c-9006-5af8a467873a
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# 브라우저에서 Adobe Commerce에 액세스할 때 PHP 버전 오류 또는 404 오류 발생

이 문서에서는 웹 브라우저에서 Adobe Commerce 인스턴스에 액세스할 수 없고 404 오류 또는 &quot;지원되지 않는 PHP 버전&quot; 오류가 발생하는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전:

* Adobe Commerce 2.3.x

## 문제: 지원되지 않는 PHP 버전

Adobe Commerce 상점 또는 Commerce 관리자에 액세스하려고 하면 다음 메시지가 표시됩니다.

`Magento supports PHP 7.1.3 or later. Please read Magento System Requirements.`

### 솔루션

다음을 시도해 보십시오.

* PHP를 버전 7.3으로 업그레이드하십시오. 자세한 내용은 개발자 설명서에서 [Adobe Commerce 2.3 기술 스택 요구 사항](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html#php)을 참조하십시오.
* 파일 시스템과 동일한 PHP 버전을 사용하지 않을 수 있으므로 Apache를 다시 시작합니다. Apache를 다시 시작하려면 다음 명령을 사용하십시오.
   * 우분투: `service apache2 restart`
   * CentOS: `service httpd restart`

## 문제: 오류 404

Adobe Commerce 상점 또는 Commerce 관리자에 액세스하려고 하면 404(찾을 수 없음) 오류가 표시됩니다.

### 솔루션

다음을 시도해 보십시오.

* [Apache 서버 다시 쓰기](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html)가 활성화되어 있는지 확인하십시오. Apache 서버 재쓰기가 잘못 설정된 경우 정적 파일이 올바른 위치에서 제공되지 않습니다.
* 설치 중에 입력한 기본 URL에 문제가 있을 수 있습니다. 명령줄에서 Adobe Commerce을 설치할 때 기본 URL을 `--base-url=` 값으로 지정하거나 웹 설치 관리자의 [웹 구성] 페이지에 있는 **저장소 주소** 필드의 값으로 지정합니다. 기본 URL *must*&#x200B;은(는) 스키마(예: `http://`)로 시작하고 뒤쪽 슬래시(/)로 끝납니다. 유효한 값으로 설치 관리자를 다시 실행하고 나중에 Adobe Commerce에 액세스해 보십시오.
