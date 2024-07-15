---
title: 배송을 URL 키로 저장할 수 없음
description: 이 문서에서는 제품 또는 CMS 페이지의 URL 키(_e. /shipping_)로 배송을 저장할 수 없는 문제에 대한 해결 방법을 제공합니다. URL 키를 저장하려고 하면 URL 키가 URL과 중복됨을 나타내는 오류가 표시됩니다.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 1ce963142a261a17e2b42f79dd567c8484ec5b3e
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# _shipping_&#x200B;을(를) URL 키로 저장할 수 없습니다.

이 문서에서는 제품 또는 CMS 페이지의 URL 키(_예: /shipping_)로 배송을 저장할 수 없는 문제에 대한 해결 방법을 제공합니다. URL 키를 저장하려고 하면 URL 키가 중복 URL임을 나타내는 오류가 표시됩니다.

## 영향을 받는 제품 및 버전

Adobe Commerce(모든 배포 메서드) 2.4.x

## 문제

URL 키에 _shipping_&#x200B;이라는 용어가 있는 CMS 페이지를 저장할 수 없습니다.

<u>재현 단계</u>:

URL 키를 _shipping_(으)로 사용하여 **[!UICONTROL CMS page]**&#x200B;을(를) 만듭니다.

<u>예상 결과</u>:

페이지가 URL 키로 _shipping_&#x200B;과(와) 함께 저장됩니다.

<u>실제 결과</u>:

다음 오류가 발생하여 저장할 수 없습니다.
*URL 키 필드에 지정된 값이 이미 있는 URL을 생성합니다.*

## 원인

Shipping은 `vendor/magento/module-shipping/etc/frontend/routes.xml`에 정의된 예약어입니다.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## 솔루션

URL 키에는 _shipping_&#x200B;이라는 용어를 사용할 수 없습니다. 그러나 다른 문자나 숫자와 함께 _shipping_&#x200B;이라는 용어(_예: shipping1 및 shipping2_)를 사용할 수 있습니다.

용어는 _shipping_+&lt;다른 숫자 또는 문자>가 아니어도 됩니다. 길이는 *255*&#x200B;자를 초과하지 않는 한 모든 문자열이 될 수 있습니다.

## 다음 단계를 수행하십시오.

1. Adobe Commerce 관리자에 로그인합니다.
1. **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**(으)로 이동합니다.
1. **[!UICONTROL Add URL Rewrite]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Create URL Rewrite]** 드롭다운에서 **[!UICONTROL Custom]** 선택.
   1. [!UICONTROL Request Path]을(를) **_배송_**(으)로 입력하십시오.
   1. **[!UICONTROL Target Path]**&#x200B;에 새 URL 키(_예: &quot;shipping1&quot;_)를 입력합니다.
   1. **[!UICONTROL Redirect]** 드롭다운에서 **[!UICONTROL No]** 선택.


      (**참고**: 요청 경로는 사용자가 브라우저에 입력하는 경로이며 대상 경로는 리디렉션해야 하는 위치입니다.)

또한 *예약된* 키워드로 레이블이 지정된 이러한 키워드를 사용하면 동일한 예외가 나타나지 않습니다. 아래에 나열된 이러한 키워드를 URL 키 값으로 사용하면 동일한 오류가 표시됩니다.


```
"admin"
"adminAnalytics"
"analytics"
"api"
"backup"
"bulk"
"captcha"
"catalog"
"catalogsearch"
"checkout"
"cms"
"contact"
"cookie"
"customer"
"directory"
"downloadable"
"giftmessage"
"groupedProduct"
"indexer"
"instantpurchase"
"loginascustomer"
"marketplace"
"mui"
"multishipping"
"newsletter"
"oauth"
"paypal"
"persistent"
"productalert"
"releaseNotification"
"reports"
"review"
"robots"
"rss"
"sales"
"search"
"security"
"sendfriend"
"shipping"
"stores"
"swagger"
"swatches"
"tax"
"theme"
"translation"
"vault"
"wishlist"
```

## 관련 읽기

* 머천다이징 및 프로모션 사용 안내서의 [URL 재작성](https://docs.magento.com/user-guide/marketing/url-rewrite.html).
* 머천다이징 및 프로모션 사용 안내서의 [SEO 모범 사례](https://docs.magento.com/user-guide/marketing/seo-best-practices.html).
