---
title: '[!UICONTROL security patch]을(를) 가져오고 적용하는 방법'
description: 이 문서에서는 릴리스된 [!UICONTROL security patch]을(를) 가져오고 적용하는 방법에 대한 지침을 제공하지만 지침을 사용할 수 없습니다.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: 06bc239cb5b1a894d2a60236a9b32b2b0c4eba80
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# [!UICONTROL security patch]을(를) 가져오고 적용하는 방법

이 문서에서는 릴리스된 [!UICONTROL security patch]을(를) 가져오고 적용하는 방법에 대한 지침을 제공하지만 지침을 사용할 수 없습니다.

## 영향을 받는 제품 및 버전

Adobe Commerce On-Premise 및 Cloud - 모든 버전

## 원인

대부분의 [!UICONTROL Security Patches]은(는) 적용할 실제 파일이나 핫픽스 없이 릴리스됩니다.

## 솔루션


### 사례 I:

릴리스 정보에서 물리적 패치 파일/핫픽스를 언급한 경우:

* [https://account.magento.com](https://account.magento.com/downloads/view/)의 다운로드 섹션에서 파일을 다운로드합니다. (공유 액세스 사용자에게는 먼저 계정 소유자/라이선스 소유자가 다운로드 권한을 부여해야 합니다.)

**주의 사항:**

이전 버전의 Adobe Commerce(2.4.4)를 사용하는 경우 자동으로 확장 지원을 받게 됩니다. 사용 가능한 최신 보안 패치를 적용하려면 사용 중인 버전이 다음 지원되지 않는 버전 중 하나여야 합니다.

2.4.4 - 2.4.4-p11

지원되지 않는 버전(2.3.x, 2.4.0 - 2.4.3)은 지원 대상이 아니므로 먼저 지원되는 버전으로 업그레이드해야 최신 보안 수정 사항을 이용할 수 있습니다.

확장 지원이 없는 경우 지원 센터에 패치를 공유하도록 요청할 수 있지만 패치를 적용할 때 발생할 수 있는 문제/오류를 해결할 수는 없습니다.

### 사례 2:

릴리스 노트에 물리적 패치 파일/핫픽스가 언급되어 있지 않은 경우:

* **클라우드:**

1. 일부 [!UICONTROL Security Patches]이(가) Commerce용 클라우드 패치 아래의 ECE 도구(Cloud Tools Suite) 최신 버전에 포함/릴리스될 수 있습니다. [릴리스 정보](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)를 확인하고 릴리스에 보안 수정 사항이 언급되면 해당 버전으로 패키지를 업그레이드하십시오.
1. 릴리스 정보에서 보안 수정 사항이 언급되지 않은 경우 계속 읽으십시오.

* **클라우드 또는 온-프레미스:**

* 실제 패치 파일/핫픽스를 사용할 수 없는 경우 [Cloud의 Adobe Commerce 버전을 업그레이드](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X를 최신 패치 버전 2.4.X-pY로 업그레이드하십시오.
* 실제 패치 파일/핫픽스를 사용할 수 없는 경우 [Adobe Commerce 버전 On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X를 최신 패치 버전 2.4.X-pY로 업그레이드하십시오.

## 관련 읽기

* *Commerce Cloud on Cloud Infrastructure Guide*&#x200B;의 [Adobe Commerce Tools Suite 릴리스 정보](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)를 참조하십시오.
* *Adobe Commerce on Cloud Infrastructure Guide*&#x200B;의 [Adobe Commerce 버전 업그레이드](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)를 참조하십시오.
