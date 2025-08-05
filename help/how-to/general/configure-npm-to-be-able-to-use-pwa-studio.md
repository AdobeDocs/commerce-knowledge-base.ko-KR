---
title: PWA Studio을 사용할 수 있도록 NPM 구성
description: '[Progressive Web Apps(PWA) Studio](https://magento.github.io/pwa-studio/)는 Adobe Commerce on cloud infrastructure 2.3.x 이상에서 사용할 수 있는 새 프로젝트입니다. PWA Studio을 사용하고 설치하려면 NPM 패키지 관리자 버전을 5.x 이상으로 설정하여 Node.js 8.x에 대한 지원을 받아야 합니다. 이 작업은 ".magento.app.yaml" 구성 파일의 "hooks:build" 섹션에서 수행됩니다.'
exl-id: 3854fc94-e8ad-45d8-bf3e-73462364220d
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# PWA Studio을 사용할 수 있도록 NPM 구성

[점진적 웹 앱(PWA) Studio](https://magento.github.io/pwa-studio/)은(는) 클라우드 인프라 2.3.x 이상의 Adobe Commerce에서 사용할 수 있는 새로운 프로젝트입니다. PWA Studio을 사용하고 설치하려면 NPM 패키지 관리자 버전을 5.x 이상으로 설정하여 Node.js 8.x에 대한 지원을 받아야 합니다. 이 작업은 `hooks:build` 구성 파일의 `.magento.app.yaml` 섹션에서 수행됩니다.

## 환경 및 기술

* 클라우드 인프라의 Adobe Commerce 2.3.X
* Adobe Commerce용 PWA

## NPM 버전 설정: 단계

필요한 NPM 버전을 설정하려면 `.magento.app.yaml` 구성 파일에 지정하십시오. 다음 단계를 수행합니다.

1. 로컬 개발 환경에서 `.magento.app.yaml` 구성 파일을 찾습니다.
1. 일반 텍스트 편집기 또는 IDE를 사용하여 편집할 파일을 엽니다.
1. `hooks:build` 섹션에서 필요한 버전을 설정합니다. 다음 예에서 구성은 현재(2019년 2월 4일) 사용 가능한 가장 높은 NPM v9.5.0을 설치하도록 설정됩니다.

   ```yaml
   hooks:
       build: |
           unset NPM_CONFIG_PREFIX
           curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
           export NVM_DIR="$HOME/.nvm"
           [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
           nvm install 9.5.0
   ```

   >[!NOTE]
   >
   >빌드뿐만 아니라 응용 프로그램에서도 Node.JS를 실행하려면 다음 명령을 추가하여 빌드 후크를 변경하십시오.
   > 
   ```
   > echo 'unset NPM_CONFIG_PREFIX' >> .environment
   > echo 'export NO_UPDATE_NOTIFIER=1' >> .environment
   > echo 'export NVM_DIR="$MAGENTO_CLOUD_DIR/.nvm"' >> .environment
   > echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> .environment
   > ```

1. 파일에 변경 사항을 저장합니다.
1. 편집된 파일을 [통합 환경](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242)에 Git 푸시합니다.

Git에서 업데이트된 YAML 파일을 환경에 푸시하면 변경 사항이 적용됩니다.

## 관련 설명서

* Adobe Commerce on Cloud Infrastructure 안내서의 [응용 프로그램 구성: 후크](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/hooks-property.html).
