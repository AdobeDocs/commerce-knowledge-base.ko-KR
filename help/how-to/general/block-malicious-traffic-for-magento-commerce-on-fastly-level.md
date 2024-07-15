---
title: Fastly 수준에서 Adobe Commerce에 대한 악성 트래픽 차단
description: 이 문서에서는 클라우드 인프라 스토어의 Adobe Commerce에서 DDoS 공격이 발생한다고 의심되는 경우 악성 트래픽을 차단하는 데 사용할 수 있는 단계를 제공합니다.
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# Fastly 수준에서 Adobe Commerce에 대한 악성 트래픽 차단

이 문서에서는 클라우드 인프라 스토어의 Adobe Commerce에서 DDoS 공격이 발생한다고 의심되는 경우 악성 트래픽을 차단하는 데 사용할 수 있는 단계를 제공합니다.

## 영향을 받는 제품 및 버전:

* 클라우드 인프라의 Adobe Commerce 2.3.x

이 문서에서는 이미 악성 IP 및/또는 해당 국가 및 사용자 에이전트가 있다고 가정합니다. Adobe Commerce on cloud infrastructure 사용자는 일반적으로 Adobe Commerce 지원에서 이 정보를 가져옵니다. 다음 섹션은 이 정보를 기반으로 트래픽을 차단하는 단계를 제공합니다. 모든 변경 작업은 프로덕션 환경에서 수행해야 합니다.

## 관리 패널 액세스 권한 얻기

웹 사이트가 DDoS에 의해 오버로드되는 경우 Commerce 관리자에 로그인하지 못할 수 있습니다(및 이 문서에 자세히 설명된 모든 단계를 수행).

관리자에 액세스하려면 [유지 관리 모드 활성화 또는 비활성화](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html#instgde-cli-maint)에 설명된 대로 웹 사이트를 유지 관리 모드로 전환하고 IP 주소를 허용 목록에 추가하십시오. 이 작업을 완료한 후 유지 관리 모드를 비활성화합니다.

## IP별 트래픽 차단

Adobe Commerce on cloud infrastructure store의 경우 특정 IP 주소 및 서브넷으로 트래픽을 차단하는 가장 효과적인 방법은 Commerce 관리자에 Fastly용 ACL을 추가하는 것입니다. 다음은 보다 자세한 지침에 대한 링크가 있는 단계입니다.

1. Commerce 관리에서 **스토어** > **구성** > **고급** > **시스템** > **전체 페이지 캐시** > **빠르게 구성**&#x200B;으로 이동합니다.
1. 차단할 IP 주소 또는 서브넷 목록을 사용하여 [새 ACL을 만듭니다](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md).
1. Adobe Commerce용 Fastly\_Cdn 모듈에 대한 [Blocking](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) 가이드에 설명된 대로 ACL 목록에 추가하고 차단합니다.

## 국가별 트래픽 차단

클라우드 인프라 스토어의 Adobe Commerce에서 국가별 트래픽을 차단하는 가장 효과적인 방법은 Commerce 관리자에서 Fastly에 대한 ACL을 추가하는 것입니다.

1. Commerce 관리에서 **스토어** > **구성** > **고급** > **시스템** > **전체 페이지 캐시** > **빠르게 구성**&#x200B;으로 이동합니다.
1. Adobe Commerce용 Fastly\_Cdn 모듈에 대한 [Blocking](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) 가이드에 설명된 대로 국가를 선택하고 ACL을 사용하여 차단을 구성합니다.

## 사용자 에이전트별 트래픽 차단

사용자 에이전트를 기반으로 차단을 설정하려면 Fastly 구성에 사용자 지정 VCL 코드 조각을 추가해야 합니다. 이렇게 하려면 다음 단계를 수행합니다.

1. Commerce 관리에서 **스토어** > **구성** > **고급** > **시스템** > **전체 페이지 캐시**&#x200B;로 이동합니다.
1. 그런 다음 **빠르게 구성** > **사용자 지정 VCL 조각**&#x200B;을 수행합니다.
1. Fastly\_Cdn 모듈에 대한 [사용자 지정 VCL 코드 조각](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md) 안내서에 설명된 대로 새 사용자 지정 코드 조각을 만듭니다. 다음 코드 샘플을 예로 사용할 수 있습니다. 이 샘플은 `AhrefsBot` 및 `SemrushBot` 사용자 에이전트에 대한 트래픽을 허용하지 않습니다.

```php
name: block_bad_useragents
  type: recv
  priority: 5
  VCL:
  if ( req.http.User-Agent ~ "(AhrefsBot|SemrushBot)" ) {
      error 405 "Not allowed";
  }
```

## 속도 제한(실험적 Fastly 기능)

특정 경로 및 크롤러에 대한 속도 제한을 지정할 수 있는 클라우드 인프라의 Adobe Commerce에 대한 실험적인 Fastly 기능이 있습니다. 자세한 내용은 [Fastly 모듈 설명서](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md)를 참조하십시오.

이 기능은 적법한 트래픽을 차단할 수 있으므로 프로덕션에서 사용하기 전에 스테이징에서 광범위하게 테스트되어야 합니다.

## 권장: robots.txt 업데이트를 고려합니다.

`robots.txt` 파일을 업데이트하면 특정 검색 엔진, 크롤러 및 로봇이 특정 페이지를 크롤링하지 않도록 하는 데 도움이 될 수 있습니다. 크롤링해서는 안 되는 페이지의 예로는 검색 결과 페이지, 체크아웃, 고객 정보 등이 있습니다. 로봇이 이러한 페이지를 크롤링하지 않도록 하면 해당 로봇이 생성하는 요청 수를 줄이는 데 도움이 될 수 있습니다.

`robots.txt`을(를) 사용할 때 두 가지 중요한 고려 사항이 있습니다.

* 로봇은 `robots.txt`을(를) 무시할 수 있습니다. 특히 보안 취약점이 있는지 웹을 검색하는 멀웨어 로봇, 스패머가 사용하는 이메일 주소 추수기 등은 주의를 기울이지 않는다.
* `robots.txt` 파일은 공개적으로 사용할 수 있는 파일입니다. 모든 사람이 사용자의 서버에서 로봇이 사용하지 않았으면 하는 섹션을 볼 수 있습니다.

기본 정보 및 기본 Adobe Commerce `robots.txt` 구성은 개발자 설명서의 [검색 엔진 로봇](https://docs.magento.com/m2/ee/user_guide/marketing/search-engine-robots.html) 문서에서 확인할 수 있습니다.

`robots.txt`에 대한 일반 정보 및 권장 사항에 대해서는 다음을 참조하십시오.

* Google 지원에서 [robots.txt 만들기](https://developers.google.com/search/docs/advanced/robots/create-robots-txt) 파일
* /robots.txtrobotstxt.org 의 [정보](https://www.robotstxt.org/robotstxt.html)

개발자 및/또는 SEO 전문가와 협력하여 허용하거나 허용하지 않을 사용자 에이전트를 결정합니다.

## 관련 읽기

[Cloud의 Adobe Commerce에 대한 제품별 라이선스 약관](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
