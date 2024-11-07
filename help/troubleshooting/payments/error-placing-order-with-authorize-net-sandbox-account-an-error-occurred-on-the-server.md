---
title: Authorize.net Sandbox 계정으로 주문 도중 오류 발생(서버에서 오류 발생)
description: 이 문서에서는 Authorize.Net Direct Post를 사용하여 주문할 때 "*서버*에서 오류가 발생했습니다" 오류 메시지에 대한 수정 사항을 제공합니다.
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Authorize.net Sandbox 계정으로 주문 도중 오류 발생(서버에서 오류 발생)

이 문서에서는 Authorize.Net Direct Post를 사용하여 주문할 때 &quot;*서버에서 오류가 발생했습니다*&quot; 오류 메시지를 수정했습니다.

>[!WARNING]
>
>**사용 중단 알림**
>
>결제 서비스 지시문 [PSD2](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive) 및 많은 API의 지속적인 발전으로 인해 Authorize.Net이 오래되어 향후 더 이상 보안 규정을 준수하지 않을 위험이 있습니다. 따라서 이제 더 이상 사용되지 않으며, Adobe Commerce 구성에서 비활성화하고 해당 [Commerce Marketplace 확장](https://marketplace.magento.com/extensions.html)(으)로 전환하는 것이 좋습니다.
>
>**이 통합은 Adobe Commerce 2.4.0 릴리스에서 제거되었으며 현재 버전의 2.3.**&#x200B;에서 더 이상 사용되지 않습니다.
>
>더 이상 사용되지 않는 결제 통합에서 보안 전환에 대한 자세한 내용은 [DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445)를 참조하십시오.

## 문제

[Authorize.Net Direct Post](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/error-placing-order-with-authorize-net-sandbox-account-an-error-occurred-on-the-server) 샌드박스 계정을 사용하여 주문하면 다음과 같은 오류 메시지가 표시됩니다.

>>
&quot;서버에서 오류가 발생했습니다. 다시 주문해 보십시오.&quot;

## 원인 1: 테스트 모드가 활성화되었습니다.

명확해 보이지 않지만 샌드박스 계정으로 테스트하는 경우에도 Authorize.net의 **테스트 모드** 설정을 **아니요**(으)로 설정해야 합니다.

## 해결 방법 1: 테스트 모드 비활성화

1. **스토어** > **구성** > **판매** > **결제 방법** > **기타 결제 방법** > **Authorize.net 직접 게시**(으)로 이동합니다.
1. **테스트 모드**&#x200B;을(를) &quot;아니요&quot;로 설정합니다. **시스템 값 사용**&#x200B;을 선택 취소하고 메뉴에서 &quot;아니요&quot;를 선택하십시오.
1. **구성 저장**&#x200B;을 클릭합니다.

![authorize-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## 원인 2: 잘못된 URL

Authorize.net 설정에 중요한 Authorize.Net 리소스에 대한 잘못된 URL 주소가 포함될 수 있습니다.

## 해결 방법 2: 올바른 URL 제공

* **게이트웨이 URL:**   `https://test.authorize.net/gateway/transact.dll`
* **거래 세부 정보 URL:**   `https://apitest.authorize.net/xml/v1/request.api`
* **API 참조:**   `https://developer.authorize.net/api/reference/`

## 도움이 되지 않는 경우: 디버그 정보 가져오기

Authorize.net으로 주문하지 못하고 정보가 아닌 *&quot;문제가 발생했습니다&quot;* 오류가 발생하면 Adobe Commerce `debug.log`을(를) 확인하십시오.

### Transact.dll

`debug.log`이(가) 비어 있는 경우 웹 브라우저의 콘솔에서 **transact.dll** 응답을 확인하십시오.

1. 콘솔을 엽니다.
1. 주문하기 전에 **네트워크** 탭으로 이동하여 **로그 유지**&#x200B;를 선택하십시오.    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. **transact.dll**(으)로 응답을 필터링하여 가능한 오류가 있는 응답 메시지를 확인합니다.    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
