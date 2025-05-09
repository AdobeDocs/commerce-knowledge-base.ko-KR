---
title: Adobe Commerce 소프트웨어 지원 종료 FAQ
description: 다음 FAQ는 판매자, 개발자 및 파트너가 Adobe Commerce에서 게시한 EOS(지원 종료) 날짜가 영향을 받는 Adobe Commerce 버전에 미치는 영향을 이해하는 데 도움이 되도록 작성되었습니다.
exl-id: ec147307-46eb-4a3a-8572-a014b091c58a
feature: Best Practices, Compliance, Console
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1733'
ht-degree: 0%

---

# Adobe Commerce 소프트웨어 지원 종료 FAQ

다음 FAQ는 판매자, 개발자 및 파트너가 Adobe Commerce에서 게시한 EOS(지원 종료) 날짜가 영향을 받는 Adobe Commerce 버전에 미치는 영향을 이해하는 데 도움이 되도록 작성되었습니다.

## 일반 규정

### 모든 버전의 Adobe Commerce에 대한 소프트웨어 지원 날짜는 어디에서 찾을 수 있습니까?

[Adobe Commerce 소프트웨어 수명 주기 정책](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)에서 Adobe Commerce 소프트웨어 수명 주기 정책 및 소프트웨어 지원 날짜를 확인할 수 있습니다. [개발자 설명서 페이지](https://experienceleague.adobe.com/ko/docs/commerce-operations/release/versions)에 지원 종료(EOS) 날짜도 게시합니다.

### Adobe이 Adobe Commerce 소프트웨어 버전에 대한 지원을 종료하면 무엇을 의미합니까?

Adobe에서 Adobe Commerce 소프트웨어 버전에 대한 지원을 종료하면 다음과 같은 결과를 기대할 수 있습니다.

* Adobe Commerce은 해당 버전에 대해 더 이상 제품 변경 사항(기능, 품질, 보안 및 PCI 규정 준수 변경 사항 포함)을 만들지 않습니다.
* 커뮤니티 가져오기 요청은 더 이상 EOS 버전에 대해 수락되거나 병합되지 않습니다. 지원되지 않는 버전의 Adobe Commerce과만 호환되는 Commerce Marketplace의 확장은 제거됩니다.
* 지원되지 않는 버전에 대한 온라인 설명서는 제거됩니다(예: 개발자 설명서 자료).
* Adobe Commerce 버전의 지원 종료 후 제출된 지원 티켓은 해결되지 않습니다(자세한 기술 지원 세부 정보는 아래 참조).

### 지원되지 않는 Adobe Commerce 소프트웨어를 사용하는 판매자에게 주는 의미는 무엇입니까?

지원되는 소프트웨어만 사용하는 것이 좋습니다.

지원이 종료된 소프트웨어를 계속 사용하기로 결정한 경우 중요한 제품 업데이트나 기술 지원을 받지 않게 됩니다. 여기에는 종종 최신 보안 업데이트가 포함됩니다. 지원되지 않는 소프트웨어를 사용하면 다음 영역에 영향을 줄 수 있습니다.

**보안 쇼핑 환경 제공:**

* 보안 지원, 수정 사항 및 업데이트를 제공하려면 리소스를 사용하여 타사 공급업체를 평가하고 활용해야 합니다.
* Adobe Commerce 소프트웨어 버전이 더 이상 지원되지 않으면 해당 버전은 더 이상 [PCI 규격](https://www.pcisecuritystandards.org/pci_security/maintaining_payment_security)이 아닙니다. 이 경우 벌금, 신용카드 처리 능력 제거 또는 기타 벌금이 부과될 수 있습니다.
* 대부분의 악용은 최신 보안 업데이트가 없는 설치를 대상으로 하므로 판매자는 항상 소프트웨어를 최신 상태로 유지하고 가능한 즉시 보안 업데이트를 설치하는 것이 좋습니다. 판매자가 웹 사이트 및 고객의 개인 데이터를 보호하기 위해 적절한 보호 장치와 보안 제어로 온라인 스토어를 안전하게 유지하는 것은 상인의 책임입니다. 이를 수행하는 가장 좋은 방법 중 하나는 최신 패치, 수정 사항 및 소프트웨어 업데이트를 설치하고 사이트 및 Admin Console에서 비정상적인 활동이 발생하는지 지속적으로 모니터링하는 것입니다.

**효율적으로 작동**

* 지원되지 않는 버전의 Adobe Commerce 소프트웨어 환경에서는 개발자와 파트너의 축소 풀을 사용할 수 있으며, 최신 기술에 대한 작업을 수행할 때 오래된 버전을 지원할 수 있습니다. 일반적으로 그 결과는 소프트웨어 유지 관리를 위한 인재의 양과 질은 감소하는 반면, 소프트웨어를 유지 관리하는 비용은 증가한다는 것이다.
* 지원되지 않는 Adobe Commerce 소프트웨어의 경우 주변 기술 및 종속성도 수명 주기(예: PHP, MYSQL, REDIS, SOLR)의 끝에 도달할 수 있습니다. 따라서 보안 및 규정 준수 사이트를 관리하고 유지하는 것이 점점 더 어려워지고 있습니다.
* 확장 개발업체들도 최신 기술과 호환 가능한 플랫폼에 대한 집중도를 높이고 있다. 따라서 지원되지 않는 버전의 Adobe Commerce에 대한 확장을 계속 유지 관리하지 않을 수 있습니다.
* 지원되지 않는 버전의 Adobe Commerce 소프트웨어를 사용하면 지속적인 비즈니스 혁신 및 성장에 이러한 리소스를 적용하는 대신 오래된 플랫폼을 유지하는 데 더 많은 비용과 리소스를 사용할 수 있습니다.

**적극적으로 성장**

* Adobe은 새로운 기술과 기능에 대한 투자를 계속하고 있다. 소프트웨어를 최신 상태로 유지하면 비즈니스를 보다 전략적으로 운영하고 더욱 빠르게 성장하는 데 도움이 되는 최신 기술과 기능을 활용할 수 있습니다.

### 상인이 Adobe Commerce 소프트웨어를 최신 상태로 유지함으로써 새로운 기술을 통해 어떤 혜택을 얻을 수 있는지에 대한 몇 가지 예는 무엇입니까?

Adobe Commerce 소프트웨어를 최신 상태로 유지함으로써 많은 이점을 얻을 수 있는 몇 가지 방법이 있습니다.

* PCI 규정 준수를 포함한 최신 보안 보호 기능을 통해 플랫폼을 최신 상태로 유지할 수 있을 뿐만 아니라 지원되는 버전으로 업그레이드하면 성능과 확장성이 향상되어 혁신적인 최신 기능을 이용할 수 있습니다.
* 2022년 4월 12일에 출시되는 Adobe Commerce 2.4.4는 상거래 기능, 성능 및 보호 분야에서 새로운 진전을 보여줍니다. 향후 몇 년간의 Adobe 혁신이 상거래 비즈니스 복원력에 도움이 될 수 있는 기반을 마련합니다. PHP 8.1의 최신 버전을 기반으로 구축된 최신 버전을 통해 상인은 디지털 상거래 비즈니스에 미래를 대비할 수 있습니다.
   * Product Recommendations, Pay Services, Live Search 등 SaaS 서비스로 제공되는 혁신적인 기능에 보다 빠르게 액세스
   * 보다 간편하고 경제적인 유지 관리 및 업그레이드
   * 고유한 비즈니스 요구 사항을 맞춤화하고 충족하는 지속적인 유연성
   * 성능 및 확장성 대폭 향상
   * 플랫폼 상태를 모니터링하는 개발자 경험 및 도구 개선

### 소프트웨어 지원 종료 문제를 방지하려면 어떻게 해야 합니까?

상거래 플랫폼은 귀사에 중요한 비즈니스 시스템이며 최신 상태를 유지하고 비즈니스에 대한 중요한 지속적인 투자입니다. 디지털 스토어에 대한 최신 기술 및 보안 업데이트는 여러 수준에서 중요하며 혁신 및 성장을 향상시키는 데 도움이 될 수 있습니다.

최신 버전의 Adobe Commerce 소프트웨어로 이동하면 시간과 리소스가 많이 소요될 수 있습니다. 가장 좋은 방법은 지원 종료 날짜 이전에 계획을 수립하여 일정과 예산 내에서 전략적 목표를 달성하는 데 적절한 시간과 리소스를 확보할 수 있도록 하는 것입니다. 다음 업그레이드를 돕기 위해 Adobe은 따라야 할 모범 사례 및 기술 단계뿐만 아니라 업그레이드를 수행할 때 사용할 도구 및 리소스가 포함된 [2.4 업그레이드 안내서](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf?lang=ko)를 게시했습니다.

또 다른 중요한 고려 사항은 개발자 및 파트너 리소스를 가능한 한 빨리 예약하는 것입니다. 파트너 시간과 리소스는 지원 종료 날짜 이전에 자주 예약되므로 마이그레이션 프로젝트를 지원할 리소스가 크게 줄어듭니다. 매년 최소한으로 논의하고 다음 연도가 계획되고 예산이 책정되도록 하는 3년 순환 계획이 있는 것이 좋습니다. [Adobe의 릴리스 일정](https://experienceleague.adobe.com/ko/docs/commerce-operations/release/planning/schedule)을 사용하여 릴리스 날짜를 추적하세요.

### Adobe Commerce 지원이 중단되면 소프트웨어 지원을 위해 서드파티 서비스 공급자를 사용할 수 있습니까?

예. 지원되지 않는 버전의 Adobe Commerce을 지원하는 보안 회사, 개발자 또는 파트너를 찾을 수 있습니다. 이러한 제공업체를 평가하고, 필요에 따라 규정 준수를 재인증하고, 비즈니스 및 고객에게 영향을 미칠 수 있는 지속적인 보안 위협을 식별하고 해결하는 것은 귀사의 책임입니다.

### 명시된 지원 종료 날짜 또는 해당 버전을 초과하는 Adobe Commerce 라이선스가 있습니다. 지원되는 버전으로 이동하지 않기로 선택한 경우 Adobe은 라이선스의 사용 기간 동안 지원되지 않는 버전에 대한 소프트웨어 지원을 계속 제공합니까?

Adobe Commerce 라이선스는 지원되지 않는 버전에 액세스 및 사용을 포함하여 Adobe Commerce의 일반적으로 사용 가능한 버전에 액세스하고 사용할 수 있는 권한을 제공합니다. 사용 중인 소프트웨어 버전이 지원되는지 여부에 관계없이 Adobe Commerce 소프트웨어에 계속 액세스하고 사용하려면 현재 라이선스 요금을 사용하여 최신 상태를 유지해야 합니다. Adobe Commerce 계약이 종료되면 이 작업이 종료됩니다.

Adobe Commerce 라이선스는 지원 종료 날짜가 경과된 버전에 대한 소프트웨어 지원을 제공하지 않습니다. 중요한 것은 지원되지 않는 소프트웨어를 계속 사용하는 경우 자체 보안 패치 및 PCI 규정 준수 재인증을 관리하고 비용을 지불해야 하며 추가 보안 위험 및 책임을 감수해야 한다는 것입니다.

### 소프트웨어 버전이 지원 종료 날짜에 도달하고 이를 지나면 &quot;종료&quot;됩니까?

아니요. Adobe Commerce 소프트웨어는 지원 종료 날짜에 도달하거나 해당 날짜가 지나면 &quot;종료&quot;되지 않습니다. 계정이 양호한 상태이면 지원되지 않는 Adobe Commerce 소프트웨어에 대해서도 라이선스가 유효하지만, PCI 규정 준수 재인증에 대한 책임이 있으며 더 이상 지원 티켓을 제출할 수 없습니다. 가장 중요한 것은 디지털 상점 보호에 도움이 되는 보안 패치를 더 이상 받지 않는다는 것입니다.

### 라이센스가 만료된 후에도 Adobe Commerce 소프트웨어를 계속 사용할 수 있습니까?

Adobe Commerce 라이선스가 만료되면 Adobe Commerce 소프트웨어 사용을 중단해야 하며 해당 소프트웨어의 모든 버전을 삭제해야 합니다. 계정이 정상적으로 작동하는 한 Adobe Commerce 라이선스는 일반적으로 사용 가능한 Adobe Commerce 버전에 액세스하고 사용할 수 있는 권한을 제공합니다.

## 기술 규정

### 소프트웨어 버전의 지원 종료 날짜 이전에 열린 지원 티켓은 지원 종료 날짜가 지나도 계속 문제 해결을 위해 작업됩니까?

예. 소프트웨어 버전의 지원 종료 날짜 이전에 열린 지원 티켓은 해당 소프트웨어 버전에 대한 지원 종료 날짜가 지나도 계속 작동되고 해결됩니다. 그러나 지원 티켓을 해결하는 것은 해상도가 만료되었거나 지원 종료에 도달한 Adobe Commerce의 제어 외부의 구성 요소(즉, PHP, jQuery 등)에 의존하는지 여부에 따라 달라질 수 있습니다. 이러한 경우 지원 티켓은 최신 릴리스로 업그레이드하는 지침을 통해 해결할 수 있습니다.

### 소프트웨어 지원이 곧 종료되는 소프트웨어 버전에 대한 티켓을 열면 Adobe이 지원 종료 날짜 이전에 해당 티켓이 해결되도록 해당 티켓의 우선 순위를 정합니까?

아니요. Adobe은 해당 소프트웨어 버전의 지원 종료 날짜에 따라 지원 티켓의 우선 순위를 다시 정하지 않습니다. 지원 티켓은 티켓의 연락처 사유, 환경 및 비즈니스 영향에 의해 파생된 내부 알고리즘을 기반으로 처리됩니다.

### 지원 종료 날짜 이전에 개설된 지원 티켓의 경우, 판매자에게 지원 종료를 알리는 경고가 있습니까?

아니요. 지원 티켓 사용자에게 지원 종료 날짜가 다가오고 있음을 알리는 알림 알림이 없습니다. 티켓 오프너가 현재 사용 중인 Adobe Commerce 버전의 지원 종료 날짜를 알 수 있습니다. 해당 날짜는 [Adobe Commerce 소프트웨어 수명 주기 정책](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)에서 확인할 수 있습니다.

### 소프트웨어 버전에 대한 지원 티켓이 해당 버전에 대한 지원 종료 날짜 이후에 열리면 여전히 문제 해결에 도움이 됩니까?

아니요. Adobe Commerce은 해당 소프트웨어 버전에 대한 지원 종료 날짜 이후에 열린 지원 티켓을 해결하기 위해 작동하지 않습니다.
