---
title: Adobe Commerce 2.4.4로 업그레이드 시 작성기 플러그인 문제
description: 이 문서에서는 Adobe Commerce 2.4.3 및 이전 버전에서 Adobe Commerce 2.4.4 이상으로 업그레이드할 때(이후 버전이 릴리스될 때) 작성기 플러그인의 문제가 발생하지 않도록 하는 솔루션을 제공합니다.
exl-id: 7502ca9e-c307-4e8a-aa1d-4886e7be25da
feature: Upgrade
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Adobe Commerce 2.4.4로 업그레이드 시 작성기 플러그인 문제

이 문서에서는 Adobe Commerce 2.4.3 및 이전 버전에서 Adobe Commerce 2.4.4 이상으로 업그레이드할 때(이후 버전이 릴리스될 때) 작성기 플러그인과 관련된 문제를 방지하는 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온프레미스, 2.4.4 이상으로 업데이트할 때(릴리스할 때) 모든 버전
* 클라우드 인프라의 Adobe Commerce, 2.4.4 이상으로 업데이트할 때의 모든 버전(릴리스 시)
* Magento Open Source, 2.4.4 이상으로 업데이트할 때(릴리스할 때) 모든 버전

## 문제

2022년 7월 이후에 Adobe Commerce 2.4.4 이상으로 업데이트하면 작성기에서 플러그인에 대한 경고를 받을 수 있습니다.

<u>재현 단계</u>:

사전 요구 사항: Adobe Commerce 2.4.3 이하가 설치되었습니다.

1. [업그레이드 수행](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)에 설명된 대로 업그레이드를 시작합니다.
1. `composer update` 명령을 실행하여 Adobe Commerce 응용 프로그램을 업그레이드합니다.

<u>예상 결과</u>:

정상적으로 업그레이드했습니다.

<u>실제 결과</u>:

다음과 유사한 오류가 발생하여 설치에 실패합니다.

```bash
Writing lock file
Installing dependencies from lock file (including require-dev)
Package operations: 591 installs, 0 updates, 0 removals
  - Installing laminas/laminas-dependency-plugin (2.2.0): Extracting archive
laminas/laminas-dependency-plugin contains a Composer plugin which is currently not in your allow-plugins config. See https://getcomposer.org/allow-plugins
Do you trust "laminas/laminas-dependency-plugin" to execute code and wish to enable it now? (writes "allow-plugins" to composer.json) [y,n,d,?] y
Plugin initialization failed (require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory), uninstalling plugin
  - Removing laminas/laminas-dependency-plugin (2.2.0)
    Install of laminas/laminas-dependency-plugin failed


  [ErrorException]
  require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## 원인

2022년 7월 이후 작성기가 [`allow-plugins` 옵션](https://getcomposer.org/doc/06-config.md#allow-plugins)의 기본값을 `{}`(으)로 변경하고, 허용되지 않는 한 플러그인은 더 이상 로드되지 않습니다.

## 솔루션

Adobe Commerce 설치 방법에 따라 `composer.json` 파일에 다음 내용을 추가하십시오.

* 프로젝트가 [`composer create-project` 명령을 사용하여](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html#get-the-metapackage) 만들어진 경우:

  ```json
  "config": {
      "allow-plugins": {
          "dealerdirect/phpcodesniffer-composer-installer": true,
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

* 다른 방법으로 프로젝트를 만들었지만 `"require-dev"` 섹션에 `"dealerdirect/phpcodesniffer-installer"`이(가) 없는 경우:

  ```json
  "config": {
      "allow-plugins": {
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

`composer.json` 파일을 업데이트한 후 `composer update` 명령을 실행하고 업그레이드 프로세스를 다시 시작하십시오.
