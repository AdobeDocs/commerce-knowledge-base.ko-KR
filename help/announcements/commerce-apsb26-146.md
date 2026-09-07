---
title: 긴급 작업 필요 Adobe Commerce에 사용할 수 있는 중요 보안 업데이트(APSB26-146)
description: Adobe은 Adobe Commerce의 0일 취약점인 CVE-2026-75650을 해결하는 보안 게시판 APSB26-146을 발표했습니다. 핫픽스를 적용하고 자격 증명을 회전하는 방법을 알아봅니다.
autotag-review: '2026-09-07T17:27:44.037Z'
TQID: 'https://experienceleague.adobe.com/ADVRRn85--ZgWtPdi4qA49fsDPVW976N4MYWp26taho'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c32adafa-ed01-4b31-997e-2413013911b0
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: d0e075aabc24a1719098754b456b71a0025e47bf
workflow-type: tm+mt
source-wordcount: 842
ht-degree: 0%

---


# 긴급 조치 필요: Adobe Commerce에 사용할 수 있는 중요 보안 업데이트(APSB26-146)

>[!IMPORTANT]
>
>CVE-2026-75650 와 관련된 긴급 업데이트입니다. Adobe은 Adobe Commerce 판매자를 대상으로 CVE-2026-75650 이 야생에서 악용되었음을 인지하고 있습니다.

9월 07일, Adobe은 Adobe Commerce 및 Magento Open Source에 영향을 주는 중요한 보안 업데이트를 발표했습니다. Adobe은 Adobe Commerce의 제로데이 취약점을 인지하고 이를 해결하기 위한 보안 업데이트(APSB26-146)를 발표했다. 이 취약성으로 인해 인증되지 않은 공격자가 영향을 받는 설치에서 임의 코드를 실행할 수 있습니다(CVE-2026-75650).

Adobe은 보안 게시판 APSB26-146을 발표했습니다. 해당 게시판은 이 취약점을 해결합니다. 이 게시판은 여기에서 볼 수 있습니다.

[Adobe Commerce 보안 업데이트 사용 가능 | APSB26-146](https://helpx.adobe.com/security/products/magento/apsb26-146.html)

이 문서에서는 현재 및 이전 버전의 Adobe Commerce 및 Magento Open Source에 핫픽스를 적용하는 방법에 대해 설명합니다.

## 설명

영향을 받는 제품 및 버전:

Adobe Commerce 버전:

* 2.4.9-2026년 8월 및 이전
* 2.4.8-2026년 8월 및 이전
* 2.4.7-2026년 8월 및 이전
* 2.4.6-2026년 8월 및 이전
* 2.4.5-2026년 8월 및 이전
* 2.4.4-2026년 8월 및 이전

Adobe Commerce B2B 버전:

* 1.5.3-2026년 8월 및 이전
* 1.5.2-2026년 8월 및 이전
* 1.4.2-2026년 8월 및 이전
* 1.3.4-2026년 8월 및 이전
* 1.3.3-2026년 8월 및 이전

Magento Open Source 버전:

* 2.4.9-2026년 8월 및 이전
* 2.4.8-2026년 8월 및 이전
* 2.4.7-2026년 8월 및 이전
* 2.4.6-2026년 8월 및 이전

## 해결 방법

### Adobe Commerce on Cloud, Adobe Commerce 온프레미스 및 Magento Open Source용 솔루션

영향을 받는 제품 및 버전에 대한 취약성을 해결하려면 VULN-39341 패치(버전에 따라)를 적용하고 암호화 키를 회전해야 합니다.

호환성 참고: 이 핫픽스는 아래 나열된 버전에 대해서만 테스트되었습니다. 지원되는 다른 버전에서 작동할 수 있지만 공식적으로 확인되지 않았습니다.

Adobe Commerce 버전:

* 2.4.9-2026-8월
* 2.4.8-2026-8월
* 2.4.7-2026-8월
* 2.4.6-2026-8월
* 2.4.5-2026-8월
* 2.4.4-2026-8월

Adobe Commerce B2B 버전:

* 1.5.3-2026-8월
* 1.5.2-2026-8월
* 1.4.2-2026-8월
* 1.3.4-2026-8월
* 1.3.3-2026년 8월

Magento Open Source 버전:

* 2.4.9-2026-8월
* 2.4.8-2026-8월
* 2.4.7-2026-8월
* 2.4.6-2026-8월

### 핫픽스 링크

영향을 받는 제품 버전에 다음 핫픽스를 적용합니다.

* [VULN-39341-composer-patches.zip 핫픽스 다운로드](https://repo.magento.com/patch/VULN-39341-composer-patches.zip)

### 핫픽스 적용 방법

파일의 압축을 풀고 지침이 필요하면 지원 기술 자료에서 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](https://experienceleague.adobe.com/ko/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)을 참조하십시오.

### 핫픽스가 적용되었는지 확인(Adobe Commerce on Cloud 판매자만 해당)

문제가 패치되었는지 쉽게 확인할 수 없으므로 CVE-2026-75650 핫픽스가 성공적으로 적용되었는지 확인하는 것이 좋습니다.

파일 `VULN-39341_Hotfix_COMPOSER.patch`을(를) 예로 사용하여 다음 단계를 수행하여 이 작업을 수행할 수 있습니다.

1. [품질 패치 도구 설치](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage#install).
1. `vendor/bin/magento-patches -n status | grep "39341\|Status"` 명령을 실행합니다.
1. 다음과 유사한 출력이 표시되어야 합니다. 여기서 VULN-39341 예는 적용됨 상태를 반환합니다.

| ID | 제목 | 카테고리 | 원본 | 상태 | 세부 사항 |
|---|---|---|---|---|---|
| 해당 사항 없음 | .../m2-hotfixes/VULN-39341_Hotfix_COMPOSER.patch | 기타 | 로컬 | 적용됨 | 패치 유형: 사용자 정의 |

### 패치를 적용한 후 자격 증명을 회전합니다

이 문제를 완전히 해결하려면 암호화 키뿐만 아니라 서버, API 및 통합 자격 증명을 포함하여 암호화되었거나 이를 사용하여 노출되었을 수 있는 모든 자격 증명을 회전합니다.

>[!NOTE]
>
>암호화 키는 통합 토큰, 결제 게이트웨이 자격 증명 및 시스템 권한 자동화 토큰을 암호화하는 데 사용됩니다. 암호화 키를 회전해도 이미 노출되었을 수 있는 자격 증명이 무효화되지 않습니다. Commerce 내뿐만 아니라 연결된 모든 자격 증명을 소스(예: 결제 게이트웨이 또는 서드파티 서비스)에서 회전합니다.

자격 증명을 회전하려면 다음 단계를 수행합니다.

1. 핫픽스 적용.
1. 유지 관리 모드를 활성화합니다.
1. 크론 실행을 사용하지 않도록 설정합니다(클라우드 명령: `vendor/bin/ece-tools cron:disable`의 Commerce).
1. [암호화 키를 회전합니다](https://experienceleague.adobe.com/ko/docs/commerce-admin/systems/security/encryption-key?lang=en).
1. 모든 관리자 패널 사용자 암호를 회전합니다.
1. 모든 REST/SOAP/GraphQL 통합 토큰을 비활성화하고 다시 생성합니다(**[!UICONTROL System]** > **[!UICONTROL Extensions]** > **[!UICONTROL Integrations]**).
1. 연결된 타사 애플리케이션에 대한 OAuth 클라이언트 보안을 회전합니다.
1. 공급자 수준에서 결제 게이트웨이 API 자격 증명을 회전(Stripe, Braintree, Adyen, PayPal 등)합니다.
1. 데이터베이스 자격 증명을 회전합니다.
1. SSH/배포 키와 cron 또는 시스템 권한 서비스 계정 자격 증명을 회전합니다.
1. 배송, 세금 및 기타 통합 타사 확장에 대한 API 키를 회전합니다.
1. 캐시를 플러시합니다.
1. 크론 실행을 사용하도록 설정합니다(클라우드 명령: `vendor/bin/ece-tools cron:enable`의 Commerce).
1. 유지 관리 모드를 비활성화합니다.

### 보안 업데이트

Adobe Commerce에서 사용할 수 있는 보안 업데이트:

* [Adobe 보안 게시판 (APSB26-146)](https://helpx.adobe.com/security/products/magento/apsb26-146.html)
* [Adobe Commerce에서 사용할 수 있는 최신 보안 업데이트](https://helpx.adobe.com/security/products/magento.html)

### 관련 읽기

Adobe Commerce 설치 가이드의 [유지 관리 모드 활성화 또는 비활성화](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/tutorials/maintenance-mode?lang=en)
