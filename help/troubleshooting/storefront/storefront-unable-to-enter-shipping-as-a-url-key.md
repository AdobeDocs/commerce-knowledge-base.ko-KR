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

# 저장할 수 없음 _배송_ URL 키로

이 문서에서는 배송을 URL 키( )로 저장할 수 없는 문제에 대한 해결 방법을 제공합니다._예: /shipping_)를 참조하십시오. URL 키를 저장하려고 하면 URL 키가 중복 URL임을 나타내는 오류가 표시됩니다.

## 영향을 받는 제품 및 버전

Adobe Commerce(모든 배포 메서드) 2.4.x

## 문제

용어가 있는 CMS 페이지는 저장할 수 없습니다. _배송_ 를 입력합니다.

<u>재현 단계</u>:

만들기 **[!UICONTROL CMS page]** (으)로 URL 키 _배송_.

<u>예상 결과</u>:

페이지가 다음으로 저장됨 _배송_ URL 키로 사용됩니다.

<u>실제 결과</u>:

다음 오류가 발생하여 저장할 수 없습니다.
*URL 키 필드에 지정된 값은 이미 존재하는 URL을 생성합니다.*

## 원인

배송은 다음에 정의된 예약어입니다. `vendor/magento/module-shipping/etc/frontend/routes.xml`.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## 솔루션

이 용어를 사용할 수 없습니다. _배송_ URL 키에서 - 단, 용어를 사용할 수 있습니다. _배송_ 다른 문자 또는 숫자(_예: shipping1 및 shipping2_).

이 용어는 반드시 다음과 같을 필요는 없습니다. _배송_+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> - 길이가 을 초과하지 않는 한 용어는 어떤 문자열이든 될 수 있습니다. *255* 자.

## 다음 단계를 수행하십시오.

1. Adobe Commerce 관리자에 로그인합니다.
1. 다음으로 이동 **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. 클릭 **[!UICONTROL Add URL Rewrite]**.
1. 선택 **[!UICONTROL Custom]** 다음에서 **[!UICONTROL Create URL Rewrite]** 드롭다운.
   1. 을(를) 입력합니다 [!UICONTROL Request Path] 다음으로: **_배송_**.
   1. 다음에서 **[!UICONTROL Target Path]**, 새 URL 키(_예: &quot;shipping1&quot;_).
   1. 선택 **[!UICONTROL No]** 다음에서 **[!UICONTROL Redirect]** 드롭다운.


      (**참고**: 요청 경로는 사용자가 브라우저에 입력하는 것이며 대상 경로는 리디렉션해야 하는 위치입니다.)

또한 로 레이블이 지정된 이러한 키워드를 사용하지 마십시오. *예약됨* 동일한 예외가 표시되는 키워드입니다. 아래에 나열된 이러한 키워드를 URL 키 값으로 사용하면 동일한 오류가 표시됩니다.


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

* [URL 재작성](https://docs.magento.com/user-guide/marketing/url-rewrite.html) ( 머천다이징 및 프로모션 사용 안내서 참조).
* [SEO 우수 사례](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) ( 머천다이징 및 프로모션 사용 안내서 참조).
