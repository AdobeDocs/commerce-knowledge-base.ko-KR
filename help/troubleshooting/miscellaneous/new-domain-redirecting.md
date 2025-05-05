---
title: 새 도메인이 기본 도메인으로 리디렉션됩니다.
description: 이 문서에서는 새 도메인이 기존 또는 다른 환경의 기본 도메인으로 리디렉션되는 문제에 대한 수정 사항을 제공합니다.
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# 새 도메인이 기본 도메인으로 리디렉션됩니다.

이 문서에서는 새 도메인이 기존 또는 다른 환경의 기본 도메인으로 리디렉션되는 문제에 대한 수정 사항을 제공합니다.

## 영향을 받는 제품 및 버전

* cloud pro 인프라의 Adobe Commerce(모든 버전)

## 문제

새 도메인이 현재 환경의 기본 도메인 또는 다른 환경의 기본 도메인으로 리디렉션됩니다.

## 원인

새 도메인을 추가한 후 변수가 업데이트되지 않거나 환경에 잘못된 [!DNL Fastly] 서비스가 구성된 경우 이 문제가 발생합니다.

## 솔루션

1. 도메인이 동일한 환경 내에서 리디렉션되는 경우 [변수](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=ko#modify-variables)을(를) 구성했는지 확인하십시오.
1. 도메인이 다른 환경으로 리디렉션되는 경우 다음 명령을 실행하여 올바른 [!DNL Fastly] 서비스를 구성했는지 확인하십시오. `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>각 환경(스테이징/프로덕션)에 로그인하고 `/mnt/shared/fastly_tokens.txt` 파일을 확인하여 [!DNL Fastly] API 자격 증명을 찾을 수 있습니다. 자세한 내용은 Commerce on Cloud Infrastructure Guide의 [configure [!DNL Fastly] services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=ko)를 참조하십시오.

위의 구성이 모두 올바른 경우 지원 티켓을 제출합니다.

## 관련 읽기

* 지원 기술 자료에서 [새 도메인 설정에 대한 검사 목록](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html?lang=ko).
