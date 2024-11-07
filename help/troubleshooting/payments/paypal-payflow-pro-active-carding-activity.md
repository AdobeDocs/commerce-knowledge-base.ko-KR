---
title: PayPal Payflow Pro 액티브 카딩 활동
description: '업데이트 날짜: 2019년 4월 2일'
exl-id: 9fe73788-5b67-445a-9b0d-86489125d271
feature: Cache, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# PayPal Payflow Pro 액티브 카딩 활동

업데이트 날짜: 2019년 4월 2일

Adobe Commerce의 PayPal Payflow Pro 통합은 공격자가 카드의 유효성을 확인하기 위해 도난된 신용카드로 수백 달러 규모의 거래를 시도하는 카드 활동을 통해 적극적으로 타깃팅되고 있습니다.

이 활동은 현재 Magento Open Source 및 Commerce(온-프레미스 및 클라우드)용 Adobe Commerce 2.1.x, 2.2.x, 2.3.x에 포함된 이 Payflow Pro 통합 버전을 타깃팅합니다. 카딩 활동은 Payflow Pro를 장바구니에 통합하는 방식에 내재되어 있습니다.

>[!NOTE]
>
>이러한 문제를 해결하기 위해 Google reCAPTCHA 또는 CAPTCHA를 Payflow Pro 체크아웃 양식에 추가하는 새로운 작성기 패키지를 제공했습니다. 모든 Adobe Commerce 버전 및 버전에 이러한 패키지를 설치하는 것이 좋습니다.

이 문제는 다음 Adobe Commerce 버전에 영향을 줍니다.

* Adobe Commerce 온-프레미스 v2.1.x, 2.2.x, 2.3.x
* 클라우드 인프라의 Adobe Commerce v2.1.x, 2.2.x, 2.3.x

## 문제

이러한 발작의 증상은 다음과 같습니다.

* PayPal Payflow Pro 계정에 식별된 수백 개의 사기성 거래가 표시됩니다.
* PayPal은 들어오는 사기 거래로 인해 Payflow Pro 계정을 일시 중지하고 상당한 수수료를 부과할 수 있습니다

## 솔루션

이러한 공격으로부터 보호하려면 Payflow Pro 체크아웃 양식에 Google reCAPTCHA(권장) 또는 CAPTCHA를 추가하는 것이 좋습니다. 여기에는 Composer 패키지 설치 및 Commerce 관리에서 Google reCAPTCHA 또는 CAPTCHA 구성이 포함됩니다.

### 패키지 설치

Adobe은 Google reCAPTCHA 및/또는 CAPTCHA를 Payflow Pro 체크아웃 양식에 추가하는 두 가지 패키지 옵션을 만들었습니다. 이러한 패키지 중 하나를 설치하면 현재 설치가 업데이트되고 Payflow Pro 체크아웃 양식에 이 보안을 강화하는 데 도움이 되는 옵션이 추가됩니다.

이러한 패키지는 다음 Adobe Commerce 배포 및 버전과 호환됩니다.

Adobe Commerce(모든 배포 방법) 및 Magento Open Source 2.1.x, 2.2.x, 2.3.x

설치하려면 Adobe Commerce 인스턴스에 CLI 명령이 필요합니다. 개발자 지원이 필요할 수 있습니다.

>[!NOTE]
>
>관련 Payflow Pro 체크아웃 양식 업데이트를 설치하는 것 외에도 Google reCAPTCHA를 설치 및 구성하는 것이 좋습니다. 이 옵션은 보이지 않는 확인 및 여러 구성 옵션을 제공합니다.

#### Google reCAPTCHA 및 체크아웃 양식 업데이트 설치

`magento/module-paypal-recaptcha` 패키지에는 Google reCAPTCHA 및 Payflow Pro 결제 양식 업데이트와의 통합이 포함되어 있습니다. reCAPTCHA 모듈이 설치 및 구성되어 있더라도 이 패키지를 설치하는 것이 좋습니다.

다음 명령을 실행하여 설치합니다.

**Adobe Commerce 온-프레미스용:**

```bash
composer require magento/module-paypal-recaptcha
bin/magento module:enable Magento_PaypalReCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**클라우드 인프라의 Adobe Commerce용:**

1. 다음 명령을 실행합니다.

   ```bash
   composer require magento/module-paypal-recaptcha
   ```

1. 변경 내용 커밋 및 푸시:

   ```bash
   git add -A && git commit -m "Install Google reCAPTCHA"    git push origin %branch_name%
   ```

1. 배포가 완료될 때까지 기다립니다.

#### CAPTCHA용 체크아웃 양식 업데이트 설치

`magento/module-paypal-captcha` 패키지에는 기본 Adobe Commerce CAPTCHA 모듈과의 통합이 포함되어 있습니다.

다음 명령을 실행하여 설치합니다.

**Adobe Commerce 온-프레미스용:**

```bash
composer require magento/module-paypal-captcha
bin/magento module:enable Magento_PaypalCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**클라우드 인프라의 Adobe Commerce용:**

1. 다음 명령을 실행합니다.

   ```bash
   composer require magento/module-paypal-captcha
   ```

1. 변경 내용 커밋 및 푸시:

   ```bash
   git add -A && git commit -m "Install CAPTCHA"    git push origin %branch_name%
   ```

1. 배포가 완료될 때까지 기다립니다.

### Google reCAPTCHA 또는 CAPTCHA 구성

패키지를 설치한 후 다음 문서에 설명된 대로 Google reCAPTCHA(권장) 또는 CAPTCHA를 구성합니다.

* 사용 안내서의 [Google reCAPTCHA](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-google-recaptcha).
* 사용 안내서의 [CAPTCHA](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-captcha).

새로운 체크아웃 양식 옵션은 다음과 같습니다.

* Google reCAPTCHA: PayPal Payflow Pro 결제 양식에서 사용
* CAPTCHA: Payflow Pro

## PayPal 지원 및 연락처

사기 방지 서비스에 대한 자세한 내용은 PayPal Payflow 판매자 지원 센터에 문의하십시오. PayPal 지원 팀에 [기본 사기 방지 서비스](https://developer.paypal.com/api/nvp-soap/payflow/fraud-protection/) 필터를 사용하여 결제를 최대한 제어할 수 있도록 요청하면, 사기성 거래를 일으킬 가능성이 있는 결제를 자동으로 거부하고 일반적으로 문제가 아닌 결제를 수락할 수 있습니다. PayPal Fraud Protection Services 필터를 켜면 거래가 정산되는 데 최대 2시간이 걸릴 수 있습니다.

>[!NOTE]
>
>자세한 내용은 PayPal의 KB [&quot;Adobe이 내 Payflow Pro 통합에 대해 내게 연락했습니다. 어떻게 해야 합니까?&quot;](https://www.paypal.com/us/smarthelp/article/ts2242).

**PayPal Payflow 판매자 지원 세부 정보**

Payflow Merchant Support의 업무 시간은 월요일부터 금요일까지 오전 7:00 - 오후 8:00(CST)입니다. 전화 또는 이메일을 통해 Payflow 판매자 지원 팀에 연락하여 계정 지원을 받을 수 있습니다.

* 전화: 1-888-883-9770(프롬프트 2 선택)
* 국제 고객: 1-408-967-0191
* 이메일: [payflow-support@paypal.com](mailto:payflow-support@paypal.com)

오스트레일리아 지원

* 월요일~금요일 오전 8:00 - 오후 7:00(AU 시간)
* 전화: +61 2 8288 0198
* 이메일: [gateway-ausupport@paypal.com](mailto:gateway-ausupport@paypal.com)
