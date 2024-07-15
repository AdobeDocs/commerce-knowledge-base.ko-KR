---
title: '[!UICONTROL CSP] 제한 모드에서 주문 만들기 페이지 문제 해결'
description: 이 문서에서는 CSP 제한 모드가 활성화되면 관리자 측에서 주문을 생성하는 오류에 대해 설명하고 이러한 오류를 수정하는 솔루션을 제공합니다.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# [!UICONTROL CSP] 제한 모드에서 주문 만들기 페이지 문제 해결

이 문서에서는 **[!UICONTROL CSP restricted mode]**&#x200B;이(가) 있는 관리자 측에서 주문을 만드는 동안 Adobe Commerce 2.4.7 문제에 대한 설명과 수정 사항을 제공합니다. *사용*, &quot;*다음 콘텐츠 보안 정책 지시문을 위반하기 때문에 인라인 스크립트 실행을 거부함: &quot;script-src ...*&quot; 오류 메시지가 브라우저 콘솔 로그에 표시됩니다.

## 영향을 받는 제품 및 버전

Adobe Commerce on cloud infrastructure, Adobe Commerce 온프레미스 및 Magento Open Source:

* 2.4.7
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## 문제 - 관리자 **주문 만들기** 페이지가 손상되었거나 로드할 수 없습니다.

관리자 **주문 만들기** 페이지가 손상되었거나 로드할 수 없습니다. &quot;*다음 콘텐츠 보안 정책 지시문 &quot;script-src ...*&quot; 오류 메시지를 위반하므로 인라인 스크립트 실행을 거부했습니다. 브라우저 콘솔 로그에 오류 메시지가 표시됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Sales]** > **[!UICONTROL Orders]**(으)로 이동합니다.
1. 새 주문을 만듭니다.

<u>예상 결과</u>:

관리자 **주문 만들기** 페이지가 정상적으로 완전히 로드됩니다.

<u>실제 결과</u>:

관리자 **순서 만들기** 페이지가 비어 있거나 구성 요소가 없습니다. 다음 [!DNL JS] 오류가 브라우저 콘솔 로그에 표시됩니다. &quot;*다음 콘텐츠 보안 정책 지시문 &quot;script-src ...*&quot;을 위반하므로 인라인 스크립트 실행을 거부했습니다.&quot;

### 원인

Adobe Commerce 및 Magento Open Source 버전 2.4.7 이상에서는 기본적으로 상점 및 관리 영역의 결제 페이지에 대해 `restrict-mode`에 **[!UICONTROL CSP]**&#x200B;이(가) 구성되어 있고 다른 모든 페이지에 대해서는 `report-only` 모드에 이(가) 구성되어 있습니다.
해당 **[!UICONTROL CSP]** 헤더에 결제 페이지의 `script-src` 지시문 내에 `unsafe-inline` 키워드가 없습니다. 또한 [!DNL whitelisted]개의 인라인 스크립트만 허용됩니다.

### 솔루션

[!UICONTROL CSP](으)로 인해 특정 스크립트가 차단되어 사용자에게 브라우저 오류가 표시될 수 있습니다.

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>이 문제를 해결하려면 다음 중 하나를 수행해야 합니다</u>:

1. `SecureHtmlRenderer` 클래스를 사용하여 차단된 스크립트를 [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style)합니다.
1. 스크립트를 실행하려면 `CSPNonceProvider` 클래스를 사용합니다.
Adobe Commerce 및 Magento Open Source 2.4.7 이상에는 각 요청에 대해 고유한 [!DNL nonce] 문자열을 쉽게 생성할 수 있도록 **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] 공급자가 포함됩니다. 그런 다음 이 [!DNL nonce] 문자열이 [!UICONTROL CSP] 헤더에 연결됩니다.

   `Magento\Csp\Helper\CspNonceProvider`에서 `generateNonce` 함수를 사용하여 [!DNL nonce] 문자열을 가져옵니다.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [모듈의 `csp_whitelist.xml` 파일에  [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes)을(를) 추가합니다.

## 문제 - 결제 방법이 없거나 작동하지 않음

결제 방법이 없거나 관리 **주문 만들기 페이지**&#x200B;에서 작동하지 않습니다. 이 페이지에서 &quot;*인라인 스크립트 실행이 거부됨. 이는 브라우저 콘솔 로그에 있는 다음 콘텐츠 보안 정책 지시문 &quot;script-src ...*&quot; 오류 메시지를 위반하기 때문입니다.

<u>재현 단계</u>:

1. **[!UICONTROL Sales]** > **[!UICONTROL Orders]**(으)로 이동합니다.
1. 새 주문을 만듭니다.
1. 새 고객을 만듭니다.
1. 고객 세부 정보를 입력합니다.
1. 주문 상세내역(제품, 운송 방법)을 입력합니다.
1. 결제 방법을 선택합니다.

<u>예상 결과</u>:

결제 방법을 선택하고 주문을 진행할 수 있습니다.

<u>실제 결과</u>:

결제 방법이 없거나 작동하지 않습니다. 다음 [!DNL JS] 오류가 브라우저 콘솔 로그에 표시됩니다. &quot;*다음 콘텐츠 보안 정책 지시문 &quot;script-src ...*&quot;을 위반하므로 인라인 스크립트 실행을 거부했습니다.

### 원인

Adobe Commerce 및 Magento Open Source 버전 2.4.7 이상에서는 기본적으로 상점 및 관리 영역의 결제 페이지에 대해 `restrict-mode`에 **[!UICONTROL CSP]**&#x200B;이(가) 구성되어 있고 다른 모든 페이지에 대해서는 `report-only` 모드에 이(가) 구성되어 있습니다.
해당 **[!UICONTROL CSP]** 헤더에 결제 페이지의 `script-src` 지시문 내에 `unsafe-inline` 키워드가 없습니다. 또한 [!DNL whitelisted]개의 인라인 스크립트만 허용됩니다.

### 솔루션

**[!UICONTROL CSP]**(으)로 인해 특정 스크립트가 차단되어 사용자에게 브라우저 오류가 표시될 수 있습니다.

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>이 문제를 해결하려면 다음 중 하나를 수행해야 합니다</u>:

1. `SecureHtmlRenderer` 클래스를 사용하여 차단된 스크립트를 [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style)합니다.
1. 스크립트를 실행하려면 `CSPNonceProvider` 클래스를 사용합니다.
Adobe Commerce 및 Magento Open Source 2.4.7 이상에는 각 요청에 대해 고유한 [!DNL nonce] 문자열을 쉽게 생성할 수 있도록 **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] 공급자가 포함됩니다. 그런 다음 이 [!DNL nonce] 문자열이 [!UICONTROL CSP] 헤더에 연결됩니다.

   `Magento\Csp\Helper\CspNonceProvider`에서 `generateNonce` 함수를 사용하여 [!DNL nonce] 문자열을 가져옵니다.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [모듈의 `csp_whitelist.xml` 파일에  [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes)을(를) 추가합니다.

## 문제 - 관리자가 주문할 수 없음

관리자가 관리자 **주문 만들기 페이지**&#x200B;에서 주문을 제출할 수 없습니다. 이 페이지에서 &quot;*다음 콘텐츠 보안 정책 지시문을 위반하므로 인라인 스크립트 실행을 거부함: 브라우저 콘솔 로그에 &quot;script-src ...*&quot; 오류 메시지가 표시됩니다.

<u>재현 단계</u>:

1. **[!UICONTROL Sales]** > **[!UICONTROL Orders]**(으)로 이동합니다.
1. 새 주문을 만듭니다.
1. 새 고객을 만듭니다.
1. 고객 세부 정보를 입력합니다.
1. 주문 상세내역(제품, 운송 방법)을 입력합니다.
1. 결제 방법을 선택합니다.
1. 주문을 제출합니다.

<u>예상 결과</u>:

주문을 정상적으로 제출할 수 있습니다.

<u>실제 결과</u>:

주문을 제출할 수 없습니다. 다음 [!DNL JS] 오류가 브라우저 콘솔 로그에 표시됩니다. &quot;*다음 콘텐츠 보안 정책 지시문 &quot;script-src ...*&quot;을 위반하므로 인라인 스크립트 실행을 거부했습니다.&quot;

### 원인

Adobe Commerce 및 Magento Open Source 버전 2.4.7 이상에서는 기본적으로 상점 및 관리 영역의 결제 페이지에 대해 `restrict-mode`에 **[!UICONTROL CSP]**&#x200B;이(가) 구성되어 있고 다른 모든 페이지에 대해서는 `report-only` 모드에 이(가) 구성되어 있습니다.
해당 **[!UICONTROL CSP]** 헤더에 결제 페이지의 `script-src` 지시문 내에 `unsafe-inline` 키워드가 없습니다. 또한 [!DNL whitelisted]개의 인라인 스크립트만 허용됩니다.

### 솔루션

**[!UICONTROL CSP]**(으)로 인해 특정 스크립트가 차단되어 사용자에게 브라우저 오류가 표시될 수 있습니다.

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>이 문제를 해결하려면 다음 중 하나를 수행해야 합니다</u>:

1. `SecureHtmlRenderer` 클래스를 사용하여 차단된 스크립트를 [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style)합니다.
1. 스크립트를 실행하려면 `CSPNonceProvider` 클래스를 사용합니다.
Adobe Commerce 및 Magento Open Source 2.4.7 이상에는 각 요청에 대해 고유한 [!DNL nonce] 문자열을 쉽게 생성할 수 있도록 **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] 공급자가 포함됩니다. 그런 다음 이 [!DNL nonce] 문자열이 [!UICONTROL CSP] 헤더에 연결됩니다.

   `Magento\Csp\Helper\CspNonceProvider`에서 `generateNonce` 함수를 사용하여 [!DNL nonce] 문자열을 가져옵니다.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [모듈의 `csp_whitelist.xml` 파일에  [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes)을(를) 추가합니다.
