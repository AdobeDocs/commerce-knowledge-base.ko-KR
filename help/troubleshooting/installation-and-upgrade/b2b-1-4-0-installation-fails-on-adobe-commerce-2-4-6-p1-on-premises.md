---
title: Adobe Commerce 2.4.6-p1 온-프레미스에서 [!DNL B2B] 1.4.0 설치에 실패했습니다.
description: 이 문서에서는  [!DNL B2B] 버전 1.4.0 설치에 실패하는 Adobe Commerce 2.4.6-p1 온-프레미스 문제에 대한 해결 방법을 제공합니다.
feature: Install, Upgrade, B2B
role: Developer
exl-id: 4a557c13-7ec2-4cfe-b86e-bb0d1a441658
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Adobe Commerce 2.4.6-p1 온-프레미스에서 [!DNL B2B] 1.4.0 설치에 실패했습니다.

이 문서에서는 [!DNL B2B] 버전 1.4.0을 설치하지 못하는 Adobe Commerce 2.4.6-p1 온-프레미스 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.4.6-p1 **온-프레미스**
* [!DNL B2B] 버전 1.4.0

>[!NOTE]
>
>[!DNL B2B] 버전 1.4.0이 **Adobe Commerce Cloud 2.4.6-p1**&#x200B;에 설치되었습니다.

## 문제

<u>재현 단계</u>:

1. Adobe Commerce 2.4.6-p1을 설치합니다.

   ```bash
   m2install.sh -s composer --ee -v 2.4.6-p1
   ```

1. [!DNL B2B] 버전 1.4.0을 설치하십시오.

   ```bash
   composer require magento/extension-b2b:1.4.0
   ```

<u>예상 결과</u>:

Adobe Commerce 2.4.6-p1에 [!DNL B2B] 버전 1.4.0이 설치되었습니다.

<u>실제 결과</u>:

다음 오류가 발생하여 설치가 실패합니다.

```bash
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
    - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.


Installation failed, reverting ./composer.json and ./composer.lock to their original content.
```

## 해결 방법

[안정성 태그](https://getcomposer.org/doc/04-schema.md#package-links)가 있는 [!DNL B2B] 보안 패키지에 대한 수동 종속성을 추가하여 Adobe Commerce 2.4.6-p1에서 [!DNL B2B] 버전 1.4.0을 설치하거나 업그레이드했습니다.

1. Adobe Commerce 설치 디렉터리에서 필요한 종속으로 `composer.json`을(를) 업데이트합니다.

   ```bash
   composer require magento/module-re-captcha-company=1.0.3-beta1@beta magento/security-package-b2b=1.0.4-beta1@beta
   ```

   **명령 출력:**

   ```bash
   Running composer update magento/module-re-captcha-company magento/security-package-b2b
   Loading composer repositories with package information
   Updating dependencies
   Lock file operations: 2 installs, 0 updates, 0 removals
     - Locking magento/module-re-captcha-company (1.0.3-beta1)
     - Locking magento/security-package-b2b (1.0.4-beta1)
   Writing lock file
   Installing dependencies from lock file (including require-dev)
   Package operations: 2 installs, 0 updates, 0 removals
     - Downloading magento/module-re-captcha-company (1.0.3-beta1)
     - Installing magento/module-re-captcha-company (1.0.3-beta1): Extracting archive
     - Installing magento/security-package-b2b (1.0.4-beta1)
   1 package suggestions were added by new dependencies, use `composer suggest` to see details.
   Package sebastian/phpcpd is abandoned, you should avoid using it. No replacement was suggested.
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. `composer.json`을(를) 업데이트하여 [!DNL B2B] 버전 1.4.0을 추가하십시오.

   ```bash
   composer require magento/extension-b2b=1.4.0
   ```

   **명령 출력:**

   ```bash
   ./composer.json has been updated
   Running composer update magento/extension-b2b
   Loading composer repositories with package information
   Updating dependencies
   ...
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. 설치 또는 업그레이드 프로세스를 완료합니다.

   * [클라우드 인프라에 설치 [!DNL B2B] 설치](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/b2b-module.html)
   * [온-프레미스 설치](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html)
