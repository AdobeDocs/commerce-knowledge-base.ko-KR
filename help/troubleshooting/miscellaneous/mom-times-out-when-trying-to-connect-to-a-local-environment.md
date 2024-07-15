---
title: Adobe Commerce에 대한 Magento Order Management 시스템(OMS) 시간 초과
description: 이 문서에서는 MOM이 콜백을 시도할 때 시간 초과되므로 Adobe Commerce용 Magento Order Management 시스템(OMS)이 Grok를 사용하여 MOM에 로컬로 설치된 마이크로 서비스를 등록할 수 없는 문제에 대한 해결 방법을 제공합니다.
exl-id: 19149d8c-ea24-46fb-8815-9f637afe46ca
feature: System
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Adobe Commerce에 대한 Magento Order Management 시스템(OMS) 시간 초과

이 문서에서는 MOM이 콜백을 시도할 때 시간 초과되므로 Adobe Commerce용 Magento Order Management 시스템(OMS)이 Grok를 사용하여 MOM에 로컬로 설치된 마이크로 서비스를 등록할 수 없는 문제에 대한 해결 방법을 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.3.1
* OMS
* 응록

>[!WARNING]
>
>면책조항: Adobe Commerce은 터널을 설정하는 특정 도구를 추천하거나 보증하지 않습니다. 앞의 내용은 제안에만 해당됩니다. 자세한 내용은 [Ngrok 설명서](https://ngrok.com/docs)를 참조하세요.

## 문제

<u>재현 단계</u>

1. 로컬 환경에 Adobe Commerce을 설치합니다.
1. ngrok를 설정하여 로컬 서버를 노출하는 터널을 만듭니다.
1. [OMS에 연결](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/)해 보세요.

<u>예상 결과</u>

연결이 정상적으로 설정되었습니다.

<u>실제 결과</u>

MCOM이 Ngrok URL로 콜백하려고 할 때 시간이 초과된 것 같습니다.

## 원인

시간 초과의 가능한 원인 중 하나는 서버가 지리적으로 너무 멀리 떨어져 있고 연결에 너무 많은 시간이 소요되기 때문입니다.

## 솔루션

ngrok를 시작할 때 지역을 지정하는 매개 변수를 추가합니다. 다음과 같습니다.

```bash
./ngrok http 80 -region eu
```

기본 영역은 US입니다. [가능한 모든 값](https://ngrok.com/docs#config_region)을 참조하세요.
