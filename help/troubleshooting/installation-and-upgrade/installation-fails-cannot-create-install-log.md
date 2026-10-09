---
title: 설치 실패. install.log를 만들 수 없음
description: 이 문서에서는 설치 중에 설치 마법사가 'install.log'를 만들지 않아 실패한 설치에 대한 수정 사항을 제공합니다.
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%
---
# 설치 실패. install.log를 만들 수 없음

이 문서에서는 설치 중에 설치 마법사가 `install.log`을(를) 만들지 않아 실패한 설치에 대한 수정 사항을 제공합니다.

## 문제

Adobe Commerce 프로세스를 동시에 실행하면 설치 로그를 만드는 데 문제가 발생할 수 있습니다. (예: 별도의 탭 페이지에 두 개의 서로 다른 설치)

## 원인

Installation-fails-create-install.log
`php.ini`의 `open_basedir`에 대한 설정을 검토하십시오. 설치 마법사는 [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) PHP 호출을 사용하여 임시 디렉터리의 값을 가져옵니다. [open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir)이(가) `sys_get_temp_dir`에서 지정한 디렉터리에 대한 연결을 거부하도록 설정되어 있으면 설치가 실패합니다.
`php.ini`의 `open_basedir`에 대한 설정을 검토하십시오. 설치 마법사는 [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) PHP 호출을 사용하여 임시 디렉터리의 값을 가져옵니다. [open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir)이(가) `sys_get_temp_dir`에서 지정한 디렉터리에 대한 연결을 거부하도록 설정되어 있으면 설치가 실패합니다.


## 솔루션

이 문제를 해결하려면 `open_basedir` 값을 변경하고 웹 서버를 다시 시작하십시오.

이 값을 변경하는 방법을 잘 모를 경우 다음 단계를 사용하십시오.

1. 아직 만들지 않은 경우 [phpinfo.php](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/prerequisites/optional-software)을(를) 만듭니다.
1. 브라우저의 주소 또는 위치 필드에 다음 URL을 입력하십시오. `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. `php.ini`의 위치를 찾으십시오. 일반적으로 표시된 결과에서 `php.ini`은(는) **로드된 구성 파일**(으)로 지정됩니다.
1. 루트 권한이 있는 사용자는 텍스트 편집기에서 `php.ini`을(를) 여십시오.
1. `open_basedir`의 값을 찾아 변경합니다.
1. 변경 내용을 `php.ini`에 저장합니다.
1. 웹 서버를 다시 시작합니다.
