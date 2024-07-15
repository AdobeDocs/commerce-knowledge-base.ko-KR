---
title: '[!UICONTROL CSP] 제한 모드에서 storefront 체크아웃 페이지 문제 해결'
description: 이 문서에서는 CSP 제한 모드에서 체크아웃 페이지를 보는 동안 발생할 수 있는 오류에 대해 설명하고 이러한 오류를 해결하는 솔루션을 제공합니다.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# [!UICONTROL CSP] 제한 모드에서 storefront 체크아웃 페이지 문제 해결

이 문서에서는 **[!UICONTROL CSP restricted mode]**&#x200B;에서 체크아웃 페이지를 보는 동안 브라우저 콘솔 로그에 있는 &quot;script-src ...*&quot; 오류 메시지를 위반하기 때문에 &quot;*&#x200B;인라인 스크립트 실행을 거부함&quot; 오류 메시지와 함께 Adobe Commerce 2.4.7 문제에 대한 설명 및 수정 사항을 제공합니다.

## 영향을 받는 제품 및 버전

Adobe Commerce on cloud infrastructure, Adobe Commerce 온프레미스 및 Magento Open Source:

* 2.4.7
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## 문제 - Storefront 체크아웃 페이지가 손상되었거나 로드할 수 없음

**Storefront 체크아웃** 페이지가 손상되었거나 로드할 수 없습니다. &quot;*다음 콘텐츠 보안 정책 지시문을 위반하므로 인라인 스크립트 실행이 거부됨: 브라우저 콘솔 로그에 &quot;script-src ...*&quot; 오류 메시지가 표시됩니다.

<u>재현 단계</u>:

1. 가게 앞쪽으로 가보세요
1. 장바구니에 제품을 추가하고 체크아웃을 진행합니다.

<u>예상 결과</u>:

체크아웃 페이지가 정상적으로 완전히 로드됩니다.

<u>실제 결과</u>:

체크아웃 페이지가 비어 있거나 구성 요소가 없습니다. 다음 [!DNL JS] 오류가 브라우저 콘솔 로그에 표시됩니다. &quot;*다음 콘텐츠 보안 정책 지시문 &quot;script-src ...*&quot;을 위반하므로 인라인 스크립트 실행을 거부했습니다.&quot;

### 원인

Adobe Commerce 및 Magento Open Source 버전 2.4.7 이상에서는 기본적으로 상점 및 관리 영역의 결제 페이지에 대해 `restrict-mode`에 **[!UICONTROL CSP]**&#x200B;이(가) 구성되어 있고 다른 모든 페이지에 대해서는 `report-only` 모드에 이(가) 구성되어 있습니다.
해당 **[!UICONTROL CSP]** 헤더에 결제 페이지의 `script-src` 지시문 내에 `unsafe-inline` 키워드가 없습니다. 또한 [!DNL whitelisted]개의 인라인 스크립트만 허용됩니다.

### 솔루션

**[!UICONTROL CSP]**(으)로 인해 특정 스크립트가 차단되어 사용자에게 브라우저 오류가 표시될 수 있습니다.

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

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

결제 방법이 없거나 **storefront 체크아웃** 페이지에서 작동하지 않습니다. &quot;*다음 콘텐츠 보안 정책 지시문 &quot;script-src ...*&quot; 오류 메시지를 위반하므로 인라인 스크립트 실행이 거부됨.

<u>재현 단계</u>:

1. 가게 앞쪽으로 가보세요
2. 장바구니에 제품을 추가하고 체크아웃을 진행합니다.
3. 결제 방법을 선택합니다.

<u>예상 결과</u>:

결제 방법을 선택하고 주문을 진행할 수 있습니다.

<u>실제 결과</u>:

결제 방법이 없거나 작동하지 않습니다. 다음 [!DNL JS] 오류가 브라우저 콘솔 로그에 표시됩니다. &quot;*다음 콘텐츠 보안 정책 지시문 &quot;script-src ...*&quot;을 위반하므로 인라인 스크립트 실행을 거부했습니다.&quot;

### 원인

Adobe Commerce 및 Magento Open Source 버전 2.4.7 이상에서는 기본적으로 상점 및 관리 영역의 결제 페이지에 대해 `restrict-mode`에 **[!UICONTROL CSP]**&#x200B;이(가) 구성되어 있고 다른 모든 페이지에 대해서는 `report-only` 모드에 이(가) 구성되어 있습니다.
해당 **[!UICONTROL CSP]** 헤더에 결제 페이지의 `script-src` 지시문 내에 `unsafe-inline` 키워드가 없습니다. 또한 [!DNL whitelisted]개의 인라인 스크립트만 허용됩니다.

### 솔루션

**[!UICONTROL CSP]**(으)로 인해 특정 스크립트가 차단되어 사용자에게 브라우저 오류가 표시될 수 있습니다.

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

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

## 문제 - 고객이 주문할 수 없음

고객은 브라우저 콘솔 로그에 &quot;script-src ...*&quot; 오류 메시지를 위반하기 때문에 &quot;*&#x200B;인라인 스크립트 실행을 거부함&quot;을 사용하여 주문을 할 수 없습니다.

<u>재현 단계</u>:

1. 가게 앞쪽으로 가보세요
2. 장바구니에 제품을 추가하고 체크아웃을 진행합니다.
3. 결제 방법을 선택합니다.
4. **주문**&#x200B;을 클릭하세요.

<u>예상 결과</u>:

정상적으로 주문할 수 있습니다.

<u>실제 결과</u>:

주문을 할 수 없습니다. 다음 [!DNL JS] 오류가 브라우저 콘솔 로그에 표시됩니다. &quot;*다음 콘텐츠 보안 정책 지시문 &quot;script-src ...*&quot;을 위반하므로 인라인 스크립트 실행을 거부했습니다.&quot;

### 원인

Adobe Commerce 및 Magento Open Source 버전 2.4.7 이상에서는 기본적으로 상점 및 관리 영역의 결제 페이지에 대해 `restrict-mode`에 **[!UICONTROL CSP]**&#x200B;이(가) 구성되어 있고 다른 모든 페이지에 대해서는 `report-only` 모드에 이(가) 구성되어 있습니다.
해당 **[!UICONTROL CSP]** 헤더에 결제 페이지의 `script-src` 지시문 내에 `unsafe-inline` 키워드가 없습니다. 또한 [!DNL whitelisted]개의 인라인 스크립트만 허용됩니다.

### 솔루션

**[!UICONTROL CSP]**(으)로 인해 특정 스크립트가 차단되어 사용자에게 브라우저 오류가 표시될 수 있습니다.

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

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
