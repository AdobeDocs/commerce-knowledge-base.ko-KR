---
title: '*contact*를 URL 키로 저장할 수 없음'
description: '이 문서에서는 *contact*를 제품 또는 CMS 페이지의 URL 키(예: "/contact")로 저장할 수 없는 문제에 대한 해결 방법을 제공합니다. URL 키를 저장하려고 하면 URL 키가 중복 URL임을 나타내는 오류가 표시됩니다.'
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# *연락처*&#x200B;을(를) URL 키로 저장할 수 없음

이 문서에서는 *연락처*&#x200B;을(를) 제품 또는 CMS 페이지의 URL 키(예: &quot;/contact&quot;)로 저장할 수 없는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

Adobe Commerce(모든 배포 메서드) 2.4.x

## 문제

*연락처* 용어를 URL 키로 사용하여 제품 또는 CMS 페이지를 저장할 수 없습니다. URL 키를 저장하려고 하면 URL 키가 중복 URL임을 나타내는 오류가 표시됩니다.

<u>재현 단계</u>:

URL 키로 *연락처*&#x200B;를 사용하는 CMS 페이지를 만드십시오.

<u>예상 결과</u>:

URL 키로 *연락처*&#x200B;와 함께 페이지가 저장됩니다.

<u>실제 결과</u>:

페이지를 저장할 수 없습니다. 오류가 발생했습니다. *URL 키 필드에 지정된 값이 이미 존재하는 URL을 생성합니다.*

## 원인

*연락처*&#x200B;은(는) `vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml`에 정의된 예약어입니다.

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## 솔루션

*연락처*&#x200B;라는 용어를 URL 키로 사용할 수 없지만 *연락처*&#x200B;라는 용어를 다른 문자나 숫자와 함께 사용할 수 있습니다(예: *연락처1* 및 *연락처2*). 용어가 *contact+\&lt;다른 숫자 또는 문자\>*&#x200B;일 필요는 없지만 길이가 255자를 초과하지 않는 한 용어는 임의의 문자열일 수 있습니다.

다음 단계를 수행하십시오.

1. Commerce 관리자에 로그인합니다.
1. **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**(으)로 이동합니다.
1. **[!UICONTROL Add URL Rewrite]**&#x200B;을(를) 클릭합니다.
1. [!UICONTROL Create URL Rewrite] 드롭다운에서 *[!UICONTROL Custom]* 선택.
   1. [!UICONTROL Request Path]에 &quot;contact&quot;를 입력합니다. [!UICONTROL Request Path]은(는) 사용자가 브라우저에 입력하는 것이고 [!UICONTROL Target Path]은(는) 리디렉션해야 하는 위치입니다.
   1. [!UICONTROL Target Path]에서 새 URL 키를 입력합니다(예: &quot;contact1&quot;).
   1. [!UICONTROL Redirect] 드롭다운에서 *[!UICONTROL No]* 선택.

## 관련 읽기

* 사용 안내서에서 [URL 재작성](https://docs.magento.com/user-guide/marketing/url-rewrite.html).
* 사용 안내서의 [SEO 모범 사례](https://docs.magento.com/user-guide/marketing/seo-best-practices.html).
