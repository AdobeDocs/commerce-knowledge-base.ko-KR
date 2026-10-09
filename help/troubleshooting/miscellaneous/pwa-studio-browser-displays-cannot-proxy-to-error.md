---
title: 'PWA Studio: 브라우저에 "프록시 대상 불가" 오류 표시'
description: 이 항목에서는 웹 브라우저에 "*프록시 대상*"이 표시되고 콘솔에
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%
---
# PWA Studio: 브라우저에 &quot;프록시 대상 불가&quot; 오류 표시

이 항목에서는 웹 브라우저에 &quot;*에 대해*&#x200B;프록시를 사용할 수 없음&quot;이 표시되고 콘솔에

```
ENOTFOUND
```

Adobe Commerce용 점진적 웹 앱(PWA) Studio를 사용할 때 오류가 발생했습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce용 PWA Studio

## 문제

<u>재현할 단계</u>:

* 브라우저에 Adobe Commerce 스토어를 로드합니다.

<u>예상 결과</u>:

* Adobe Commerce 저장소는 정상적으로 브라우저에 로드됩니다.

<u>실제 결과</u>:

* 웹 브라우저에 &quot;*프록시를*&#x200B;에 사용할 수 없음&quot; 오류가 표시되고 콘솔에 다음과 같은 오류가 표시됩니다.

```
    ENOTFOUND
```


## 원인

NodeJS가 Adobe Commerce 저장소의 호스트 이름을 확인할 수 없습니다.

## 솔루션

1. Adobe Commerce 스토어가 둘 이상의 웹 브라우저에 로드되는지 확인하십시오.
1. 로컬 DNS 서버나 VPN을 실행 중인 경우 `/etc/hosts`에 있는 호스트 파일에 항목을 추가하고 이 도메인([호스트 파일 편집에 대한 일반 지침](https://linuxize.com/post/how-to-edit-your-hosts-file/))을 수동으로 매핑하여 NodeJS가 확인할 수 있도록 합니다.

## 관련 읽기

* [PWA Studio for Adobe Commerce 설명서](https://developer.adobe.com/commerce/pwa-studio/)
* [도구 및 라이브러리](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/)
