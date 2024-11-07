---
title: 설치 또는 업그레이드 도중 메모리 부족 오류 발생
description: 이 문서에서는 Adobe Commerce 온-프레미스 및 Magento Open Source 온-프레미스 제품 설치/업그레이드 시 메모리 부족 오류에 대한 솔루션에 대해 설명합니다.
exl-id: c0ed8228-9357-4a3b-a102-1119386ea52a
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

설치 또는 업그레이드가 성공했는지 확인하려면 개발자 설명서에서 [2GB의 메모리를 PHP에 할당](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings)하는 것이 좋습니다.

이 작업을 이미 수행한 경우 시스템에 스왑 파일을 만듭니다. Linux 컴퓨터에서 메모리 리소스가 더 필요하고 RAM이 꽉 찬 경우 *스왑 공간*&#x200B;을 사용합니다. 스왑 공간은 메모리의 비활성 페이지에 사용됩니다.

다음은 제안에만 해당되며, 다른 옵션을 사용할 수도 있습니다. 계속하기 전에 네트워크 관리자 또는 다른 숙련된 리소스에 문의하십시오. `root` 권한을 가진 사용자로 교체 파일을 만들려면 명령을 실행해야 합니다.

### Ubuntu에서 파일 교체 {#swap-file-on-ubuntu}

다음 참조에 설명된 대로 `fallocate` 명령을 사용합니다.

* [Ubuntu 14.04(Digitalocean)에서 스왑을 추가하는 방법](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
* [Ubuntu 16.04(Digitalocean)에서 스왑 공간을 추가하는 방법](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)
* [SwapFaq(help.ubuntu.com)](https://help.ubuntu.com/community/SwapFaq)

### CentOS에서 파일 교체 {#swap-file-on-centos}

다음 참조에 설명된 대로 `mkswap` 명령을 사용합니다.

* [CentOS 6(Digitalocean)에서 스왑을 추가하는 방법](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-6)
* [CentOS 7(Digitalocean)에서 스왑을 추가하는 방법](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-7)
* [공간 교체(RedHat 고객 포털)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html)
