---
title: Adobe Commerce 2.3.6, 2.4.1 체크아웃 CAPTCHA가 작동하지 않음
description: 이 문서에서는 Adobe Commerce에서 Paypal Express, Payflow Pro 또는 CyberSource와 같은 서드파티 결제 공급자를 사용할 때 체크아웃을 위한 CAPTCHA 기능이 주문 페이지에서 예상대로 작동하지 않는 문제에 대한 패치를 제공합니다.
exl-id: 46ab7f4d-ee0a-4cc1-96cc-6eb408319e9c
feature: Checkout, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Adobe Commerce 2.3.6, 2.4.1 체크아웃 CAPTCHA가 작동하지 않음

이 문서에서는 Adobe Commerce에서 Paypal Express, Payflow Pro 또는 CyberSource와 같은 서드파티 결제 공급자를 사용할 때 체크아웃을 위한 CAPTCHA 기능이 주문 페이지에서 예상대로 작동하지 않는 문제에 대한 패치를 제공합니다.

이 알려진 문제는 개발자 설명서에 나와 있습니다.

<u>Adobe Commerce 2.3.6</u>의 경우:

* [Adobe Commerce 2.3.6 릴리스 노트: 알려진 문제](https://devdocs.magento.com/guides/v2.3/release-notes/commerce-2-3-6.html#known-issues)
* [Magento Open Source 2.3.6 릴리스 정보: 알려진 문제](https://devdocs.magento.com/guides/v2.3/release-notes/open-source-2-3-6.html#known-issues)

<u>Adobe Commerce 2.4.1의 경우</u>:

* [Adobe Commerce 2.4.1 릴리스 정보: 알려진 문제](https://devdocs.magento.com/guides/v2.4/release-notes/commerce-2-4-1.html#known-issues)
* [Magento Open Source 2.4.1 릴리스 정보: 알려진 문제](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-1.html#known-issues)

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 방법) 2.3.6 및 2.4.1
* Magento Open Source 2.3.6 및 2.4.1

## 문제

<u>재현 단계</u>

1. Commerce에서 Paypal Express, Payflow Pro 또는 CyberSource와 같은 결제 방법 중 적어도 하나를 설정합니다.
1. **관리자 > 스토어 > 구성 > 고객 > 고객 구성 > CAPTCHA** 로 이동합니다.
   * **Storefront에서 CAPTCHA를 사용하도록 설정** = *예* .
   * **Forms**&#x200B;에서 선택: *체크아웃/주문 중* , *로그인* 및 *암호 찾기* .
   * **표시 모드** = *로그인 시도 횟수*(로그인 시도 실패 횟수&#x200B;**설정 표시)를 설정합니다.**
   * **로그인을 시도하지 못한 횟수** = *0*&#x200B;을(를) 설정합니다(항상 captcha가 작동하도록 설정).
1. 프론트엔드에서 장바구니에 제품을 추가하고 체크아웃을 시도하십시오.
1. 결제 정보 페이지에서 captcha를 입력하고 Paypal Express, Payflow Pro 또는 CyberSource를 사용하여 체크아웃을 시도합니다.

<u>예상 결과:</u>

CAPTCHA 기능은 예상대로 작동합니다.

<u>실제 결과:</u>

오류 메시지가 표시됩니다. *CAPTCHA 코드를 입력하고 다시 시도하십시오.*

## 솔루션

Adobe Commerce 온-프레미스/Adobe Commerce 온 클라우드 인프라/Magento Open Source 2.3.6 또는 2.4.1에 있는지에 따라 아래 패치 중 하나를 적용합니다.

## 패치

패치는 이 문서에 첨부되어 있으며 `.composer` 및 `.git` 형식으로 모두 다운로드할 수 있습니다.

패치를 다운로드하려면 문서 끝까지 아래로 스크롤하여 파일 이름을 클릭하거나 다음 링크 중 하나를 클릭합니다.

<u>클라우드 인프라/Magento Open Source 2.3.6</u>의 Adobe Commerce 온-프레미스/Adobe Commerce:

* [Composer 패치 MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git 패치 MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_GIT.patch.zip)

<u>클라우드 인프라/Magento Open Source 2.4.1의 Adobe Commerce 온-프레미스/Adobe Commerce의 경우</u>:

* [Composer 패치 MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git 패치 MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_GIT.patch.zip)

이러한 패치는 다른 Adobe Commerce 또는 Magento Open Source 버전 및 버전과 호환되지 않습니다.

## 패치 적용 방법

<u>작성기 패치</u>

작성기 패치 지침은 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

<u>Git 패치</u>

Adobe Commerce/Magento Open Source에 대한 git 패치 지침은 개발자 설명서 [패치 적용: 사용자 지정 패치](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#custom-patches)를 참조하십시오.
