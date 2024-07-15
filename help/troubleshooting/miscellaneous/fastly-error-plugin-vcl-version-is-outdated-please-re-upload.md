---
title: 'Fastly 오류: 플러그인 VCL 버전이 오래되었습니다! 다시 업로드하십시오'
description: 이 문서에서는 "*Plugin VCL 버전이 오래되었습니다!"라는 메시지가 표시되면 이에 대한 솔루션을 제공합니다. 다시 업로드하십시오.최신 Fastly 모듈을 설치하지 않았기 때문에 Commerce 관리자의 Fastly 구성에서 *"을 사용합니다.
exl-id: d7870e9e-ba6b-49c2-a80c-26fb464cbae3
feature: Best Practices, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Fastly 오류: 플러그인 VCL 버전이 오래되었습니다! 다시 업로드하십시오.

이 문서에서는 &quot;*Plugin VCL 버전이 오래되었습니다!&quot;라는 메시지가 표시되면 이에 대한 해결 방법을 제공합니다. 다시 업로드하십시오.최신 Fastly 모듈을 설치하지 않았으므로 Commerce 관리자의 Fastly 구성에서*&quot;을(를) 사용합니다.

## 영향을 받는 제품 및 버전

클라우드 인프라 2.2.x., 2.3.x<br>의 Adobe Commerce
Fastly: 이 오류는 최신 모듈을 제외한 모든 버전의 Fastly 모듈에 영향을 줄 수 있습니다. 최신 릴리스에 대한 자세한 내용은 GitHub에서 [Fastly 릴리스 노트](https://github.com/fastly/fastly-magento2/releases)를 참조하십시오.

## 문제

1. Commerce 관리 패널에 로그인합니다.
1. **스토어** > **구성** > **고급** > **시스템** > **전체 페이지 캐시**&#x200B;로 이동합니다.   **Fastly 캐시.**
1. **자동 업로드 및 서비스 활성화** 섹션에서 &quot;*플러그 인 VCL 버전이 오래되었습니다! 다시 업로드하십시오.*&quot; 알림입니다.
1. &quot;VCL을 Fastly로 업로드&quot; 단추를 클릭하여 VCL 코드 조각을 업로드하려고 하지만 &quot;*Plugin VCL 버전이 오래되었습니다!&quot;라는 경고가 표시됩니다. 다시 업로드하십시오.*&quot;

## 원인

Fastly 확장이 업데이트되었지만(번들 VCL 구성 및 템플릿과 함께) 업데이트된 VCL 구성이 Fastly 서비스에 업로드되지 않았습니다. Adobe Commerce 모듈 `Fastly_Cdn`을(를) 업데이트할 때 업데이트된 VCL 구성을 Fastly에 다시 업로드해야 합니다.

## 솔루션

1. 개발자 설명서에서 최신 ECE-Tools가 설치되어 있고 [현재 버전](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html)에 있는지 확인하십시오. ECE-Tools에는 종속성에 Fastly 패키지 버전이 있습니다.

   이 Fastly 플러그인의 최신 버전이 아닐 수 있지만 현재 설치된 버전보다 최신 버전일 수 있으며 최신 ECE-Tools를 설치하는 것이 좋습니다.

1. 현재 버전의 ECE-Tools를 사용하고 있지 않은 경우 다음 단계에 따라 개발자 설명서에서 [업그레이드](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html)하십시오.
1. ECE-Tools를 업그레이드한 후 현재 버전의 [Fastly 플러그인](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets)이 설치되어 있는지 확인하십시오.
1. Fastly 플러그인이 현재 버전이 아닌 경우 다음 단계에 따라 개발자 설명서에서 [플러그인을 최신 버전으로 업그레이드](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module)하십시오.

## 관련 읽기

* Fastly 설정 및 구성에 대한 자세한 내용은 개발자 설명서에서 [Fastly 서비스 구성](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)을 참조하십시오.
* Fastly에 대한 일반적인 정보는 [fastly.com](https://www.fastly.com/)을 참조하세요.
