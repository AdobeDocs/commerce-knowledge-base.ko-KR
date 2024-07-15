---
title: 다른 도메인의 책임자 및 프론트로부터 사이버소스 결제가 처리되지 않음
description: 이 문서에서는 서로 다른 도메인에 있는 경우 상점 및 Commerce 관리자 모두에서 사이버소스 결제를 처리할 수 없는 것과 관련된 알려진 Adobe Commerce 2.3.0 제한에 대한 패치를 제공합니다.
exl-id: 948d5907-70bd-4890-bc8a-23e04b116018
feature: Admin Workspace, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# 다른 도메인의 책임자 및 프론트로부터 사이버소스 결제가 처리되지 않음

이 문서에서는 서로 다른 도메인에 있는 경우 상점 및 Commerce 관리자 모두에서 사이버소스 결제를 처리할 수 없는 것과 관련된 알려진 Adobe Commerce 2.3.0 제한에 대한 패치를 제공합니다.

>[!NOTE]
>
>핵심 Adobe Commerce Cybersource 결제 통합은 2.3.3부터 더 이상 사용되지 않으며 2.4.0에서 완전히 제거됩니다. 대신 마켓플레이스에서 [공식 확장](https://marketplace.magento.com/cybersource-global-payment-management.html)을 사용하십시오.

## 문제

이전의 Cybersource 통합 구현에서는 한 도메인에서만 결제를 처리할 수 있었습니다. 따라서 Adobe Commerce 상점 전면이 Commerce 관리자와 다른 도메인에 있는 경우, 관리자에서 Cybersource를 사용하여 주문하려고 할 때 다음 오류가 발생합니다. &quot; *X-Frame-Options에서 로드 거부됨: https://%your\_domain%/cybersource/SilentOrder/TokenResponse/ 은 원본 간 프레이밍을 허용하지 않습니다.* .&quot;

<u>재현 단계</u>:

1. 다른 하위 도메인에서 관리자를 설정합니다.
1. **스토어** > 설정 > **구성** > **판매** > **결제 방법** > **CyberSource**&#x200B;에서 스토어에 대한 Cybersource를 구성하십시오.
1. **판매** > **주문**(으)로 이동합니다.
1. 새 주문을 만듭니다.
1. 새 고객을 만듭니다.
1. 고객 세부 정보를 입력합니다.
1. 주문 상세내역(제품, 운송 방법)을 입력합니다.
1. 결제 방법으로 Cybersource를 선택합니다.
1. 주문을 제출합니다.

<u>예상 결과</u>: 주문이 문제 없이 완료되었습니다.

<u>실제 결과</u>: 순서 페이지에 로딩 아이콘이 표시되지만 순서는 변경되지 않습니다. 콘솔에 오류가 표시됩니다.

## 솔루션

첨부된 패치를 통해 Cybersource와의 통합 기능이 향상되었습니다. 패치를 적용한 후 관리자에서 결제를 처리하기 위해 Cybersource를 사용하여 프로필을 한 개 더 만들고 **Stores** > Settings > **Configuration** > **Sales** > **결제 방법** > **CyberSource**&#x200B;에서 Commerce 관리자의 Cybersource 구성에 필요한 자격 증명을 추가해야 합니다.

>[!NOTE]
>
>개선 사항은 Adobe Commerce 온프레미스 및 클라우드 인프라 2.2.9와 2.3.1에 포함되어 있습니다.

## 패치

이 문서에 여러 패치가 첨부되어 있으며 다른 버전에 대해 서로 다른 패치가 있습니다. 패치를 다운로드하려면 문서 끝까지 아래로 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

* [MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch 다운로드](assets/MDVA-5914_EE_2.1.9_COMPOSER_v3.patch.zip)
* [MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch 다운로드](assets/MDVA-8609_EE_2.2.2_COMPOSER_v2.patch.zip)
* [MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch 다운로드](assets/MDVA-12964_EE_2.2.5_COMPOSER_v1.patch.zip)
* [MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch 다운로드](assets/MDVA-16643_EE_2.3.0_COMPOSER_v1.patch.zip)

## 호환 가능한 Adobe Commerce 버전

패치는 패치 파일 이름에 언급된 특정 버전에 대해 생성되었습니다. 예를 들어, MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch는 Adobe Commerce 2.1.9용으로 만들어졌으며 이 버전에 사용할 수 있는 가장 좋은 패치입니다.

패치는 다음 버전과도 호환됩니다.

* Adobe Commerce 온-프레미스 2.1.3-2.1.17, Adobe Commerce on cloud infrastructure 2.1.5-2.12(MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch)
* Adobe Commerce 온-프레미스 2.2.0-2.2.3, Adobe Commerce 온 클라우드 인프라 2.2.0-2.2.3(MDVA-8609\_EE\_2.2\_COMPOSER\_v2.patch)
* Adobe Commerce 온-프레미스 2.2.4-2.2.7, Adobe Commerce on cloud infrastructure 2.2.4-2.2.7(MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch)
* Adobe Commerce 온-프레미스 2.2.8, 2.3.0, Adobe Commerce on cloud infrastructure 2.3.0(MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch)

## 패치 적용 방법

지침은 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
