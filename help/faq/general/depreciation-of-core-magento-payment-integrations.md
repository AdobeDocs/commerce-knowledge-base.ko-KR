---
title: 핵심 Adobe Commerce 결제 통합 사용 중단
description: 결제 서비스 지침 PSD2(사용 안내서의 [결제 서비스 지침](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html)에 대한 세부 사항 참조) 및 많은 API의 지속적인 발전으로 인해 많은 Adobe Commerce 핵심 결제 통합 기능이 오래되고 향후 더 이상 보안을 준수하지 않을 수 있습니다. 이를 위해 많은 핵심 결제 통합이 중단되었거나 곧 중단될 예정이며, 해당 Commerce Marketplace 확장으로 전환하는 것이 좋습니다. 아래 문서의 나머지 부분을 읽어 결제 통합의 최근 사용 중단을 검토하십시오. 각 **상태** 링크는 사용 안내서에 있습니다. **아래 통합은 Adobe Commerce의 2.4.0 릴리스에서 모두 제거되며, 버전 2.3에서는 더 이상 사용되지 않습니다.**
exl-id: c2c4b3b6-409d-466f-a4f3-dfe13ac7f972
feature: Compliance, Integration
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# 핵심 Adobe Commerce 결제 통합 사용 중단

결제 서비스 지침 PSD2(사용 안내서의 [결제 서비스 지침](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html)에 대한 세부 정보 참조)와 많은 API의 지속적인 발전으로 인해 많은 Adobe Commerce 핵심 결제 통합 기능이 오래되고 향후 더 이상 보안을 준수하지 않을 수 있습니다. 이를 위해 많은 핵심 결제 통합이 중단되었거나 곧 중단될 예정이며, 해당 Commerce Marketplace 확장으로 전환하는 것이 좋습니다. 아래 문서의 나머지 부분을 읽어 결제 통합의 최근 사용 중단을 검토하십시오. 각 **상태** 링크는 사용 안내서에 있습니다. **아래 통합은 Adobe Commerce의 2.4.0 릴리스에서 모두 제거되며 버전 2.3에서 더 이상 사용되지 않습니다.**

<table style="height: 243px;" width="712">
<tbody>
<tr>
<td style="width: 225.455px;"><strong>결제 방법 통합</strong></td>
<td style="width: 226.364px;"><strong>상태</strong></td>
<td style="width: 226.364px;"><strong>Adobe Commerce 2.X 권장 사항</strong></td>
</tr>
<tr>
<td style="width: 225.455px;">Worldpay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">2.3.5 이후 사용되지 않음</a><br>2.4.0 - 완전히 제거됩니다.</td>
<td style="width: 226.364px;">PSD2 요구 사항을 준수하도록 권장하는 솔루션을 결제 공급업체에 문의하십시오.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">2.3.4 이후 사용되지 않음</a><br>2.4.0 - 완전히 제거됩니다.</td>
<td style="width: 226.364px;">대신 Commerce Marketplace에서 <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">공식 확장</a>을 사용하십시오.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net (다이렉트 Post)</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">2.3.1 이후 사용되지 않음</a><br>2.4.0 - 완전히 제거됩니다.</td>
<td style="width: 226.364px;">대신 Commerce Marketplace에서 <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">공식 확장</a>을 사용하십시오.</td>
</tr>
<tr>
<td style="width: 225.455px;">사이버 소스</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">2.3.3 이후 사용되지 않음</a><br>2.4.0 - 완전히 제거됩니다.</td>
<td style="width: 226.364px;">대신 Commerce Marketplace에서 <a href="https://marketplace.magento.com/cybersource-global-payment-management.html">공식 확장</a>을 사용하십시오.</td>
</tr>
<tr>
<td style="width: 225.455px;">eWay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">2.3.3 이후 사용되지 않음</a><br>2.4.0 - 완전히 제거됩니다.</td>
<td style="width: 226.364px;">PSD2 요구 사항을 준수하도록 권장하는 솔루션을 결제 공급업체에 문의하십시오.</td>
</tr>
</tbody>
</table>

**PayPal 핵심 결제 방법 통합은 더 이상 사용되지 않거나 제거되지 않으며 모든 2.3.x 및 2.4.x 릴리스에서 계속 지원됩니다.**

## 결제 보안 유지 방법

더 이상 사용되지 않는 결제 통합을 사용하는 모든 Adobe Commerce 및 Magento Open Source 배포의 경우 아래 권장 사항에 따라 고객의 결제가 안전한지, 결제가 거부되지 않았는지 확인하고 Adobe Commerce 2.4.0으로 업그레이드할 준비를 하십시오.

* 위의 표에 언급된 대로 [Commerce Marketplace](https://marketplace.magento.com/extensions/payments-security/payment-integration.html?_ga=2.108129217.2105547619.1564067043-238341041.1564067043)에서 공식 결제 방법 확장을 설치하고 구성합니다.
* 관리자의 더 이상 사용되지 않는 결제 통합을 사용하지 않도록 설정합니다( **사용** 구성 옵션을 *아니요*(으)로 설정). 따라서 더 이상 결제 옵션으로 상점 앞에 표시되지 않습니다. 대신 확장 통합을 통해 모든 새 주문이 지불되었는지 확인합니다.
* Commerce Marketplace의 새 통합은 더 이상 사용되지 않는 결제 통합을 사용하여 수행한 결제 거래를 처리할 수 없으므로 일정 기간 동안 두 결제 방법을 병행하여 사용하는 것이 좋습니다. 단, 이미 게시된 거래가 완료되고 환불이 가능해야 합니다. 이렇게 하려면 더 이상 사용되지 않는 결제 방법을 비활성화하고 모든 구성 필드를 채운 상태로 두십시오.
