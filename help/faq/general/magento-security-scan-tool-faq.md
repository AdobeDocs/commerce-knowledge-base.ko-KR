---
title: Adobe Commerce 보안 검사 도구 FAQ
description: 이 문서는 Adobe Commerce 보안 검색 도구에 대한 몇 가지 FAQ에 대한 답변을 제공합니다.
exl-id: 380ce617-e3d9-491b-b425-8489abd3c541
feature: Compliance
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# Adobe Commerce 보안 검사 도구 FAQ

이 문서는 Adobe Commerce 보안 검색 도구에 대한 몇 가지 FAQ에 대한 답변을 제공합니다.

## Security Scan Tool은 무엇이며 누구에게 작성됩니까? {#what-is-the-magento-security-scan-tool-and-who-is-it-written-for}

Security Scan Tool은 판매자, 개발자 및 담당자로 지정된 담당자가 보안 위험에 대해 사이트를 모니터링할 수 있는 무료 도구입니다. 가맹점의 악성코드를 선제적·효율적으로 탐지하고 보안상 위험이나 악성코드, 위협이 있으면 가맹점에 알릴 수 있다.

## 모든 Adobe Commerce 판매자가 보안 검색 도구를 사용할 수 있습니까? {#is-magento-security-scan-tool-available-to-all-magento-merchants}

예. 보안 검색 도구는 모든 Adobe Commerce 및 Magento Open Source 판매자가 사용할 수 있습니다.

## 보안 검색 도구로 내 사이트를 검색할 수 있는 사람이 있습니까? {#can-anyone-scan-my-site-with-the-magento-security-scan-tool}

아니요. 판매자는 토큰을 통해 검사를 요청할 때 사이트를 Adobe Commerce 계정에 연결합니다. 사이트별로 고유합니다.

## 이 도구는 내 웹 스토어에서 Adobe Commerce이 아닌 페이지를 검사할 수 있습니까? {#can-the-tool-scan-non-magento-pages-on-my-webstore}

Security Scan Tool은 Adobe Commerce 도메인의 취약점을 스캔하도록 설계되었습니다. 보안 검색 도구를 사용하여 Adobe Commerce이 아닌 페이지에서 취약점을 검색하면 신뢰할 수 없는 결과가 나타날 수 있습니다. 판매자는 Security Scan Tool을 사용하여 다른 Adobe Commerce 이외의 플랫폼에서 생성된 페이지를 검사하지 않는 것이 좋습니다.

## 스캔 도구에서 특정 보안 테스트를 제외할 수 있습니까? {#can-i-exclude-specific-security-tests-from-magento-scan-tool}

보안 검색 도구 판매자는 Adobe Commerce에 대한 보안 검색 도구 검사에서 특정 보안 테스트를 제외할 수 없습니다. 각 Security Scan Tool 보안 테스트는 판매자가 보안 위험, 맬웨어 및 위협을 식별하는 데 도움이 되도록 작성됩니다.

## 비용은 얼마입니까? {#what-does-it-cost}

보안 검색 도구는 무료입니다. 판매자는 보안 검색 결과 또는 사이트 구성에 따라 Adobe Commerce의 책임을 면제하는 법적 면책조항에 동의해야 합니다.

## Security Scan Tool은 어떻게 작동합니까? {#how-does-the-magento-security-scan-tool-work}

보안 검색 도구는 웹을 기반으로 하며 판매자의 온라인 Adobe Commerce 계정([account.magento.com](https://account.magento.com/))에서 액세스합니다. 보안 검사는 HTTP와 HTTPS 모두에서 작동합니다. 알려진 보안 문제를 확인하고 누락된 Adobe Commerce 패치 및 업데이트를 식별합니다.

## 보안 검색 도구를 사용하려면 어떻게 등록합니까? {#how-do-i-sign-up-to-use-the-magento-security-scan-tool}

판매자는 보안 검색 도구를 사용하여 Adobe Commerce 계정([account.magento.com](https://account.magento.com))에서 웹 스토어를 검색하도록 등록할 수 있습니다. 보안 검색 도구 [여기](https://account.magento.com/scanner/dashboard/?_ga=2.83981338.267715797.1615821601-2099431409.1611073686)에 등록하려면 링크를 따라가십시오.

## 스캔 보고서에서 양성 오류가 발생하면 어떻게 해야 합니까? {#what-do-i-do-if-i-come-across-a-false-positive-in-the-scan-report}

판매자에게 실패한 모든 검사를 조사하고 이러한 문제를 해결하기 위한 적절한 조치를 취할 것을 권장합니다. 조사 후, 만약 상인들이 거짓 양성으로 보이는 스캔 결과를 발견하게 되면, 우리는 상인이 적절한 조치를 취하도록 Adobe에 통지하도록 요청합니다.

긍정 오류(false positive) 보고서를 제출하려면 Adobe Commerce 판매자 지원 기능이 있는 티켓을 입력하여 긍정 오류(false positive)를 평가하고, 필요한 변경을 수행하고, 향후 이러한 알림이 표시되지 않도록 권장 사항을 제공할 수 있습니다. 가맹점은 [securityscan@magento.com](mailto:securityscan@magento.com)로 전자 메일을 보내 긍정 오류(false positive)를 보고할 수도 있습니다.
