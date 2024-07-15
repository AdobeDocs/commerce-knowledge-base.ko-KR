---
title: Composer install 명령은 .gitigore 파일, Adobe Commerce을 감독합니다.
description: 이 문서에서는 추적된 '.gitignore' 파일이 클라우드 인프라 2.4.2-p1 및 2.3.7의 Adobe Commerce에서 작성기에 의해 재정의되는 경우에 대한 솔루션을 제공합니다.
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Composer install 명령은 .gitigore 파일, Adobe Commerce을 감독합니다.

이 문서에서는 추적된 `.gitignore` 파일이 클라우드 인프라 2.4.2-p1 및 2.3.7의 Adobe Commerce에서 작성기에 의해 재정의되는 경우에 대한 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라 2.4.2-p1 및 2.3.7의 Adobe Commerce.

## 문제

composer install 명령을 실행할 때 `.gitignore` 파일을 덮어쓰는 중입니다.

<u>재현 단계</u>:


1. 작업 공간에 대한 빈 디렉토리를 만듭니다.
1. 루트 디렉터리에서 이 명령을 실행합니다.

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition:2.4.2-p1.
   ```

   \# 또는 2.3.7

1. 그런 다음 다음 다음 명령을 실행합니다.
   1. `echo "/this/line/should/stay" >> .gitignore`
   1. `git init`
   1. `git add * && git add .*`
   1. 저장소에 커밋된 파일 `git commit -m "Init"`개
   1. `rm -rf vendor/*`
   1. `composer install`
   1. `git diff`

      ```git
      diff --git a/.gitignore b/.gitignore
      index c144521..7092a56 100644
      --- a/.gitignore
      +++ b/.gitignore
      @@ -70,4 +70,3 @@ atlassian*
      /generated/*
      !/generated/.htaccess
      .DS_Store
      -/this/line/should/stay
      ```

<u>예상 결과</u>:

`.gitignore`은(는) 작성기에 의해 재정의되지 않았습니다.

<u>실제 결과</u>:

`.gitignore`은(는) 모든 작성기 설치 실행에서 재정의됩니다.

## 솔루션

사용자 지정 `.gitignore file`을(를) 유지하려면 `magento-deploy-ignore` 섹션에서 무시해야 합니다.

```git
{
...
"extra": {
    "magento-deploy-ignore": {
        "*": [
            "/.gitignore"
        ]
    }
    ...
}
```


## 관련 읽기

* [추적된 .gitigore 파일이 작성기에 의해 재정의됩니다.Magento2 GitHub의 ](https://github.com/magento/magento2/issues/32888).
