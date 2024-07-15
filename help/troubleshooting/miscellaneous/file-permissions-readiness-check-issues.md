---
title: 파일 권한 준비 확인 문제
description: '''이 문서에서는 파일 권한 준비 검사 문제에 대한 수정 사항을 제공합니다. Adobe Commerce 파일 시스템의 디렉토리는 웹 서버 사용자와 Adobe Commerce 파일 시스템 소유자가 쓸 수 있어야 합니다(해당하는 경우). 사용 권한이 제대로 설정되지 않은 경우 웹 설치 마법사에 다음과 유사한 오류가 표시됩니다.'
exl-id: 252e6e7d-5269-44ce-b3ce-6fc2ea6a1c5c
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# 파일 권한 준비 확인 문제

이 문서에서는 파일 권한 준비 검사 문제에 대한 수정 사항을 제공합니다. Adobe Commerce 파일 시스템의 디렉토리는 웹 서버 사용자와 Adobe Commerce 파일 시스템 소유자가 쓸 수 있어야 합니다(해당하는 경우). 사용 권한이 제대로 설정되지 않은 경우 웹 설치 마법사에 다음과 유사한 오류가 표시됩니다.

![install_rc_file-perms.png](assets/install_rc_file-perms.png)

이 문제를 해결하는 방법은 사용자 1명 또는 사용자 2명 설정 여부에 따라 다릅니다.

* *사용자 한 명*&#x200B;은(는) 웹 서버를 실행하는 사용자와 동일한 사용자로 Adobe Commerce 서버에 로그인함을 의미합니다. 이러한 유형의 설정은 공유 호스팅 환경에서 일반적입니다.
* *두 명의 사용자*&#x200B;는 일반적으로 *웹 서버 사용자로 로그인하거나 웹 서버 사용자로 전환할 수 없음을 의미합니다*. 일반적으로 한 명의 사용자로 로그인하고 웹 서버를 다른 사용자로 실행합니다. 이는 개인 호스팅 또는 자체 서버가 있는 경우에 일반적입니다.

## 1명의 사용자 해상도

명령줄 액세스 권한이 있는 경우 `/var/www/html/magento2`에 Adobe Commerce이 설치되어 있다고 가정하고 다음 명령을 입력하십시오.

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+w {} + && chmod u+x bin/magento
```

명령줄 액세스 권한이 없는 경우 호스팅 공급자에서 제공한 FTP 클라이언트 또는 파일 관리자 응용 프로그램을 사용하여 권한을 설정합니다.

## 두 사용자 해상도

선택적으로 한 줄에 모든 명령을 입력하려면 다음을 입력하십시오. Adobe Commerce이 `/var/www/html/magento2`에 설치되어 있고 웹 서버 그룹 이름이 `apache`이라고 가정합니다.

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

이벤트 파일 시스템 권한이 잘못 설정되어 Adobe Commerce 파일 시스템 소유자가 변경할 수 없는 경우 `root` 권한을 가진 사용자로 명령을 입력할 수 있습니다.

```bash
$ cd /var/www/html/magento2 && sudo find var vendor
  pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find
  var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + &&
  sudo chown -R :apache . && sudo chmod u+x bin/magento
```
