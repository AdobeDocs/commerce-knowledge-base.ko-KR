---
title: '"Updater 응용 프로그램을 사용할 수 없습니다" 오류"'
description: 이 문서에서는 웹 설치 마법사를 사용하여 Adobe Commerce 온프레미스를 업데이트/설치하려고 할 때 발생할 수 있는 "Updater 응용 프로그램을 사용할 수 없음" 문제에 대한 해결 방법에 대해 설명합니다.
exl-id: 85e55ed8-0bc9-4378-b722-46be98ce2638
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# &quot;Updater 응용 프로그램을 사용할 수 없습니다&quot; 오류

이 문서에서는 웹 설치 마법사를 사용하여 Adobe Commerce 온프레미스를 업데이트/설치하려고 할 때 발생할 수 있는 &quot;Updater 응용 프로그램을 사용할 수 없음&quot; 문제에 대한 해결 방법에 대해 설명합니다.

## 문제

준비 확인에는 다음 메시지가 표시됩니다.

![Screen_Shot_2019-08-29_at_1.39.12_PM.png](assets/Screen_Shot_2019-08-29_at_1.39.12_PM.png)

## 영향을 받는 제품/버전

* Adobe Commerce 온-프레미스 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## 솔루션

이 문제를 해결하려면 파일 및 하위 디렉터리가 포함된 `<magento_root>/update` 디렉터리가 있는지 확인합니다. 그렇지 않으면 개발자 설명서에서 [업데이트 프로그램 설정](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/updater-application-is-not-available-error)을 참조하십시오.
