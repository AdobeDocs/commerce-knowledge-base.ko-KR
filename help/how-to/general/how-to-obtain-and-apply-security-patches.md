---
title: '[!UICONTROL security patch]을(를) 가져오고 적용하는 방법'
description: 이 문서에서는 릴리스된 [!UICONTROL security patch]을(를) 가져오고 적용하는 방법에 대한 지침을 제공하지만 지침을 사용할 수 없습니다.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: 43c8308c6539c53f60fb6457047898a2edd46532
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# [!UICONTROL security patch]을(를) 가져오고 적용하는 방법

>[!NOTE]
>온-프레미스 설치가 있고 [!DNL CVS] 또는 [!DNL GitHub]과(와) 같은 버전 제어 시스템을 사용하여 코드를 관리하지 않는 경우 웹 호스트에서 패치 적용을 지원할 수 있습니다. 언제든지 연락하여 지원을 요청하십시오.

이 문서에서는 릴리스된 [!UICONTROL security patch]을(를) 가져오고 적용하는 방법에 대한 지침을 제공하지만 지침을 사용할 수 없습니다.

## 영향을 받는 제품 및 버전

Adobe Commerce On-Premise 및 Cloud - 모든 버전


## 원인

대부분의 [!UICONTROL Security Patches]은(는) 적용할 격리된 패치 또는 핫픽스 없이 릴리스되었으며 [!UICONTROL Security Patch] 릴리스로 업그레이드해야 합니다.

## 솔루션


### 사례 I:

* 분리된 패치 파일/핫픽스가 [릴리스 정보](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite)에 언급되어 있으면 [https://account.magento.com](https://account.magento.com/downloads/view/)의 다운로드 섹션에서 파일을 다운로드하십시오. 공유 액세스 사용자에게는 먼저 계정 소유자/라이선스 소유자가 다운로드 권한을 부여해야 합니다.

**주의 사항:**

이전 버전의 Adobe Commerce(2.4.4)를 사용하는 경우 자동으로 확장 지원을 받게 됩니다. 사용 가능한 최신 보안 패치를 적용하려면 사용 중인 버전이 다음 지원되지 않는 버전 중 하나여야 합니다.

2.4.4 - 2.4.4-p11

지원되지 않는 버전(2.3.x, 2.4.0 - 2.4.3)은 지원 대상이 아니므로 먼저 지원되는 버전으로 업그레이드해야 최신 보안 수정 사항을 이용할 수 있습니다.

확장 지원이 없는 경우 지원 센터에 패치를 공유하도록 요청할 수 있지만 패치를 적용할 때 발생할 수 있는 문제/오류를 해결할 수는 없습니다.

### 사례 2:

격리된 패치는 예외적인 경우에만 제공되며, 보안 수정 사항을 구현하는 기본 형태는 아닙니다.

격리된 패치 파일/핫픽스가 릴리스 정보에 언급되지 않은 경우:

* **클라우드:**

1. 일부 [!UICONTROL Security Patches]이(가) Commerce용 클라우드 패치 아래의 ECE 도구(Cloud Tools Suite) 최신 버전에 포함/릴리스될 수 있습니다. [릴리스 정보](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)를 확인하고 릴리스에 보안 수정 사항이 언급되면 해당 버전으로 패키지를 업그레이드하십시오.
1. 릴리스 정보에서 보안 수정 사항이 언급되지 않은 경우 계속 읽으십시오.

* **클라우드 또는 온-프레미스:**

* 격리된 패치 파일/핫픽스를 사용할 수 없는 경우 [Cloud의 Adobe Commerce 버전을 업그레이드](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X를 최신 패치 버전 2.4.X-pY로 업그레이드하십시오.
* 격리된 패치 파일/핫픽스를 사용할 수 없는 경우 [Adobe Commerce 버전 On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X를 최신 패치 버전 2.4.X-pY로 업그레이드하십시오.

## 관련 읽기

* *Commerce Cloud on Cloud Infrastructure Guide*&#x200B;의 [Adobe Commerce Tools Suite 릴리스 정보](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)를 참조하십시오.
* *Adobe Commerce on Cloud Infrastructure Guide*&#x200B;의 [Adobe Commerce 버전 업그레이드](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)를 참조하십시오.
