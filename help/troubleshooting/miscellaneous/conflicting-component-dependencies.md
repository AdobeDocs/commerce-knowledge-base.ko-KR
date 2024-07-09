---
title: 충돌하는 구성 요소 종속성
description: 이 문서에서는 충돌하는 구성 요소 종속성에 대한 솔루션을 제공합니다. 웹 설정 마법사를 사용하여 Adobe Commerce을 설정하거나 업데이트하려고 하면 *"충돌하는 구성 요소 종속성을 발견했습니다"* 작성기 오류 메시지가 표시됩니다.
exl-id: 782049c4-b6e1-4ead-a00f-80d2aa8475c9
feature: Configuration
role: Developer
source-git-commit: 8f0f7412e75e07a22e66236b88c095c698dbf23e
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# 충돌하는 구성 요소 종속성

이 문서에서는 충돌하는 구성 요소 종속성에 대한 솔루션을 제공합니다. 웹 설치 마법사를 사용하여 Adobe Commerce을 설정하거나 업데이트하려고 하면 *&quot;충돌하는 구성 요소 종속성을 찾았습니다.&quot;* 작성기 오류 메시지입니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 온-프레미스 2.2.x, 2.3.x
* 클라우드 인프라의 Adobe Commerce 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## 문제 {#issue}

다음과 유사한 구성 요소 종속성 충돌 오류 메시지가 표시됩니다(실제 패키지 이름과 버전은 다를 수 있음).

```bash
We found conflicting component dependencies.
You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
We have detected conflicts with the following packages:
- magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

## 원인

이 메시지는 Composer에서 설치 또는 업데이트할 구성 요소를 결정할 수 없는 경우 표시됩니다.

## 솔루션

두 가지 주요 시나리오로 인해 구성 요소 종속성이 충돌할 수 있습니다. 시나리오를 클릭하여 문제 해결 단계를 수행합니다.

* [Adobe Commerce 업그레이드](#upgrading-magento)
* [타사 모듈과의 비호환성:](#incompatibility-third-party-modules)
   * [Adobe Commerce(모든 배포 유형)](#magento-commerce-magento-commerce-cloud)
   * [Magento Open Source](#opensource)

## Adobe Commerce 업그레이드 {#upgrading-magento}

클라우드 인프라에서 Adobe Commerce을 업그레이드하는 경우 충돌하는 구성 요소 종속성을 해결하려면 다음을 시도하십시오.

* 업그레이드하는 데 사용 중인 키를 확인합니다. 올바른 이메일 계정에서 키가 생성됩니까?
* 사용 권한을 확인하고 Magento 업그레이드 요구 사항과 일치하는지 확인하십시오. 리뷰 [Magento 업그레이드 개요 > 업데이트 및 업그레이드 검사 목록 > 파일 시스템 권한](https://devdocs.magento.com/guides/v2.3/comp-mgr/prereq/prereq_compman-checklist.html#perms) 개발자 설명서에서 확인할 수 있습니다.

## 타사 모듈과의 비호환성: {#incompatibility-third-party-modules}

설치된 구성 요소보다 이전 Commerce 구성 요소에 의존하는 서드파티 모듈로 인해 구성 요소 종속성이 충돌할 수도 있습니다. 다음을 시도해 보십시오.

1. 앞에 [예](#issue)설치된 패키지 magento/sample-data 버전 0.74.0-beta15를 1.0.0-베타로 업그레이드할 수 없습니다. 그러나 0.74.0-Beta15는 0.74.0-Beta16(또는 기타)으로 업그레이드할 수 있습니다. 편집 `composer.json` 을 클릭하여 이러한 변경 작업을 수행합니다. 일반적으로 프로젝트에서 요청하는 버전은 `require` 또는 `require-dev` 해당 JSON 파일에 있는 개체의 속성입니다. 제공된 패키지 버전 옵션에 따라 특정 버전 또는 제한을 지정할 수 있습니다. 작성기 사용 방법에 대한 일반적인 지침은 클라우드 인프라를 사용하는 경우 다음을 참조하십시오. [Cloud for Adobe Commerce > 기술 및 요구 사항 > 작성기](https://devdocs.magento.com/cloud/reference/cloud-composer.html#files) 개발자 설명서에서 확인할 수 있습니다. Adobe Commerce 온프레미스에 있는 경우 다음을 참조하십시오. [Adobe Commerce > 설치 안내서 > Composer를 사용하여 Adobe Commerce 설치](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) .
1. 이제 준비 상태를 확인해 보십시오. 리뷰 [Adobe Commerce 업그레이드 개요 > 모듈 관리자 실행 > 1단계 준비 확인](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-readiness.html) 개발자 설명서에서 확인할 수 있습니다.
1. 준비 검사가 다른 구성 요소 종속성 검사 실패 메시지와 함께 실패하는 경우 사용 중인지 여부에 따라 다음 링크를 클릭합니다 [Adobe Commerce](#magento-commerce-magento-commerce-cloud) 또는 [Magento Open Source](#opensource) 추가 문제 해결 단계 보기

## Adobe Commerce {#magento-commerce-magento-commerce-cloud}

1. 확장 개발자에게 연락하여 도움을 받으십시오. 확장을 구입한 페이지에서 Commerce Marketplace의 연락처 정보를 찾을 수 있습니다. 다음 항목을 찾습니다. **판매자 연락처** 오른쪽 패널에 단추가 표시됩니다. 모든 Commerce 개발자는 Marketplace에 확장을 게시할 때 사용자 및 설치 안내서를 제공해야 합니다. 두 기능은 모두 랜딩 페이지의 오른쪽에서 찾을 수 있습니다.
1. 적절한 시간 내에 판매자로부터 회신을 받지 못한 경우, [마켓플레이스 지원에 문의](mailto:commercemarketplacesupport@adobe.com) 이를 통해 고객 지원 약속을 상기시킬 수 있습니다.

## Magento Open Source {#opensource}

에 지원 요청 [주요 포럼](https://community.magento.com/) 또는 [Adobe Commerce 파트너에게 문의](https://magento.com/find-a-partner) 이는 Source 열기 문제에 도움이 됩니다.
