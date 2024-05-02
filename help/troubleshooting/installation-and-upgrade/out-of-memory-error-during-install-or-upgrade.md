---
title: 설치 또는 업그레이드 도중 메모리 부족 오류 발생
description: 이 문서에서는 Adobe Commerce 온-프레미스 및 Magento Open Source 온-프레미스 제품 설치/업그레이드 시 메모리 부족 오류에 대한 솔루션에 대해 설명합니다.
exl-id: c0ed8228-9357-4a3b-a102-1119386ea52a
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# 설치 또는 업그레이드 도중 메모리 부족 오류 발생

이 문서에서는 Adobe Commerce 온-프레미스 및 Magento Open Source 온-프레미스 제품 설치/업그레이드 시 메모리 부족 오류에 대한 솔루션에 대해 설명합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.3.x
* Magento Open Source 온-프레미스 2.3.x

## 문제

웹 설치 마법사를 사용하여 Adobe Commerce 또는 Magento Open Source 애플리케이션이나 확장, 테마 또는 언어 패키지와 같은 구성 요소를 설치하거나 업데이트할 때 다음과 유사한 오류가 표시됩니다.

```bash
Could not complete update {"components":[
{"name":"magento/module-bundle-sample-data","version":"100.1.0"}
]} successfully: proc_open(): fork failed - Cannot allocate memory
```

오류

```bash
proc_open(): fork failed - Cannot allocate memory
```

명령줄에도 을 표시할 수 있습니다.

## 솔루션 {#solution}

다음을 추천합니다 [php에 2GB 메모리 할당](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) 개발자 설명서에서 설치 또는 업그레이드가 성공했는지 확인하십시오.

이 작업을 이미 수행한 경우 시스템에 스왑 파일을 만듭니다. Linux 시스템에서는 *교환 공간* 메모리 리소스가 더 필요하고 RAM이 꽉 찬 경우. 스왑 공간은 메모리의 비활성 페이지에 사용됩니다.

다음은 제안에만 해당되며, 다른 옵션을 사용할 수도 있습니다. 계속하기 전에 네트워크 관리자 또는 다른 숙련된 리소스에 문의하십시오. 명령을 실행하여 사용자로 스왑 파일을 만들어야 합니다. `root` 권한.

### Ubuntu에서 파일 교체 {#swap-file-on-ubuntu}

사용 `fallocate` 다음 참조에 설명된 명령:

* [Ubuntu 14.04 (Digitalocean)에서 스왑을 추가하는 방법](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
* [우분투 16.04 (Digitalocean)에서 스왑 공간을 추가하는 방법](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)
* [SwapFaq(help.ubuntu.com)](https://help.ubuntu.com/community/SwapFaq)

### CentOS에서 파일 교체 {#swap-file-on-centos}

사용 `mkswap` 다음 참조에 설명된 명령:

* [CentOS 6에서 스왑을 추가하는 방법(Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-6)
* [CentOS 7에 스왑 추가 방법 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-7)
* [스왑 공간(RedHat 고객 포털)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html)
