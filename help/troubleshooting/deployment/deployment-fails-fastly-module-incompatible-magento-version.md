---
title: 배포가 실패함 호환되지 않는 Adobe Commerce 버전을 Fastly로 모듈화합니다.
description: '업데이트 날짜: 2019년 2월 29일'
exl-id: aab77407-94e5-42de-92f4-2f0c19e24fa4
feature: Deploy, Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 배포가 실패함 호환되지 않는 Adobe Commerce 버전을 Fastly로 모듈화합니다.

업데이트 날짜: 2019년 2월 29일

이 문서에서는 Fastly 모듈이 현재 Adobe Commerce 버전과 호환되지 않아 배포가 실패하는 경우에 대한 수정 사항을 제공합니다.

**문제:** 새 커밋과 푸시 후 배포가 실패하고 다음과 유사한 오류 메시지가 표시됩니다.

>\[Exception\] 경고: Fastly\\Cdn\\Plugin\\...에 대한 인수 3 누락, /app/vendor/magento/framework/Interception/Interceptor.php에서 호출... 및 /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php에서 정의...

**원인:** Fastly 모듈 v1.2.79에서 이전 버전과 호환되지 않는 변경 내용을 표시합니다.

**솔루션(임시):** Fastly 모듈을 버전 1.2.82 이상으로 업그레이드하고 Commerce 관리자에서 새 VCL을 업로드합니다. 그런 다음 변경 사항을 커밋하고 푸시하여 성공적인 배포를 트리거합니다.

## 영향을 받는 버전

* Adobe Commerce 온-프레미스 2.1.X
* 클라우드 인프라의 Adobe Commerce 2.1.X
* Fastly 모듈 1.2.79

## 문제

통합, 프로덕션 또는 스테이징 환경에 변경 사항을 커밋하고 푸시할 때 일반적으로 다음 단계는 배포 프로세스를 트리거하는 것입니다. 이 작업은 Adobe Commerce on cloud infrastructure edition에서 자동으로 수행되고, Adobe Commerce 온프레미스에서 수동으로 수행됩니다.

배포가 실패하고 다음 오류 메시지가 표시될 수 있습니다.

```
[2019-01-23 00:00:00] INFO: php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US
[2019-01-23 00:00:00] CRITICAL:
  Requested languages: en_GB, en_US
  Requested areas: frontend, adminhtml
  Requested themes: Magento/blank, Magento/backend
  === frontend -> Magento/blank -> en_GB ===

    [Exception]
    Warning: Missing argument 3 for Fastly\Cdn\Plugin\ExcludeFilesFromMinification::afterGetExcludes(), called in /app/vendor/magento/framework/Interception/Interceptor.php on line 152 and defined in /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php on line 38

  setup:static-content:deploy [-d|--dry-run] [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [-t|--theme[="..."]] [--exclude-theme[="..."]] [-l|--language[="..."]] [--exclude-language[="..."]] [-a|--area[="..."]] [--exclude-area[="..."]] [-j|--jobs[="..."]] [--symlink-locale] [languages1] ... [languagesN]

[2019-01-23 000:00:00] INFO: Set flag: var/.deploy_is_failed
[2019-01-23 00:00:00] CRITICAL: Command php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US returned code 1
```

클라우드 인프라 솔루션에서 Adobe Commerce을 사용하는 경우 [배포 로그](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations)에 이 오류 메시지가 표시됩니다. Adobe Commerce 온-프레미스의 경우 명령줄에 오류가 표시됩니다.

## 원인

이 문제는 Fastly 모듈 v1.2.79의 이전 버전과 호환되지 않는 변경 내용으로 인해 발생합니다.

## 솔루션

Fastly 모듈을 버전 1.2.82 이상으로 업그레이드하십시오.

이렇게 하려면 다음 단계를 수행합니다.

1. 다음 명령 중 하나를 실행합니다.
   * Fastly 모듈이 magento-cloud-metapackage에 포함된 경우:    <pre>작성기 업데이트 magento/magento-cloud-metapackage</pre>
   * fastly 모듈이 별도로 설치된 경우(예: cloud edition이 아닌 Adobe Commerce 온프레미스를 사용하는 경우) <pre>작성기 업데이트 fastly/magento2</pre>
1. 변경 사항을 커밋하고 푸시하고, 자동으로 수행되지 않는 경우 배포 프로세스를 트리거합니다.
1. 관리에서 [새 VCL을 Fastly로 업로드](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets)합니다.
