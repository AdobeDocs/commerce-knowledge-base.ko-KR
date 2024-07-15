---
title: "[!DNL Fastly] 원본 차단 사용 FAQ"
description: 이 FAQ에서는 Adobe Commerce(2021년부터 완전히 구현됨)의  [!DNL Fastly] 원본 차단 활성화에 대한 일반적인 질문에 대해 설명합니다.
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 1021a1ab81481f92e850bd49330f1742fe9a21f2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# [!DNL Fastly] 원본 차단 사용 FAQ

이 FAQ에서는 Adobe Commerce(2021년부터 완전히 구현됨)의 [!DNL Fastly] 원본 차단 사용에 대한 일반적인 질문에 대해 설명합니다.

## [!DNL Fastly] 원본 클로킹은 무엇입니까?

원본 클로킹은 클라우드 인프라의 Adobe Commerce에서 [!DNL non-Fastly] 트래픽을 차단할 수 있는 보안 기능입니다(DDoS 공격을 방지하기 위해 클라우드 인프라(원본)로 이동).

## Origin Cloaking의 이점은 무엇입니까?

원본 클로킹은 트래픽이 [!DNL Fastly Web Application Firewall](WAF)을 건너뛰고 엄격하게 정의된 흐름(**[!DNL Fastly]** > **로드 밸런서** > **인스턴스**)을 통해 라우팅되는 것을 방지하기 위해 설계되었습니다. 이 구현에서는 모든 트래픽이 [!DNL Fastly] WAF와 부하 분산 장치에 내장된 내부 WAF를 통과하도록 보장됩니다.

## 이 원본 차단 활성화가 발생하는 이유는 무엇입니까?

이 기능은 원래 클라우드 인프라에서 Adobe Commerce의 이점을 활용하기 위해 만들어졌습니다.

## 내 프로젝트에 대해 원본 차단 활성화를 요청해야 합니까?

아니. 이 기능은 모든 클라우드 프로젝트에서 이미 구현했어야 하며, 2021년 이후 프로비저닝된 모든 프로젝트는 기본적으로 이를 활성화했을 것입니다.

## 원본 클로킹이 보내는 IP 주소를 변경합니까?

아니, 그렇지 않아

## 원본 클로킹이 REST API에 영향을 줍니까?

[!DNL Fastly]은(는) API 호출을 캐시하지 않으므로 클라이언트는 변경하지 않아도 됩니다. 원본 클로킹은 다음과 같이 원본으로 직접 이동하는 요청만 차단합니다.

* 프로덕션

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

* 스테이징

```php
mcstaging2.mywebsite.com.c.abcdefghijkl.dev.ent.magento.cloud
```

* StagingX

```php
mcstagingX.mywebsite.com.c.abcdefghijkl.X.dev.ent.magento.cloud
```

이 예제에서 클라이언트는 URL을 ``mywebsite.com``(으)로 변경하는 경우에도 API를 히트할 수 있습니다.

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## 이러한 변경 사항이 배포 및 다운타임에 영향을 미칩니까?

아니요. 이 변경 사항은 배포 및 가동 중지에 영향을 **NOT**&#x200B;합니다.

## 프로젝트에 여러 스테이징 환경이 있는 경우 원본 클로킹이 모든 스테이징 환경에 적용됩니까?

예. 프로젝트에 여러 스테이징 환경이 있는 경우 변경 사항이 모든 스테이징 환경에 적용됩니다.
