---
title: ' [!DNL Fastly] 자격 증명의 유효성을 검사하는 동안 오류가 발생했습니다.'
description: 이 문서에서는  [!DNL Fastly] 자격 증명의 유효성을 검사할 때 사용자에게 오류가 발생하는 문제에 대한 해결 방법을 제공합니다.
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 838f0c5d55c29d026dc37a8f7e5214b9880a4353
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# [!DNL Fastly] 자격 증명의 유효성을 검사하는 동안 오류 발생

이 문서에서는 [!DNL Fastly] 자격 증명의 유효성을 검사할 때 발생한 *토큰 만료* 오류를 해결하는 방법에 대해 설명합니다.

이 문서에 설명된 단계는 보안상의 이유로 [!DNL Fastly] API 토큰을 회전(순환)해야 하는 경우에도 적용됩니다. 이러한 경우 새 [!DNL Fastly] API 토큰을 요청하려면 Adobe Commerce 지원 티켓을 제출해야 합니다.

## 문제

* [!DNL Fastly] 자격 증명의 유효성을 검사하는 동안 오류가 발생했습니다.
* [!DNL Fastly] 토큰이 지원 티켓에서 의도치 않게 공유되었거나 공개 포럼에 게시된 경우와 같이 손상되었을 수 있습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 메서드): 모든 버전
* 확장 또는 기술([!DNL Fastly], [!DNL New Relic] 등) 버전 [!DNL Fastly]

## 솔루션

1. 올바른 [!DNL Fastly] 서비스 ID 및 API 토큰이 있는지 확인하고 다시 유효성 검사를 시도하십시오. 자세한 지침은 개발자 설명서에서 [자격 증명 테스트 [!DNL Fastly] 를 참조하십시오.](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials)
1. 자격 증명 확인에 실패하면 다음 curl 명령을 실행하여 서비스 상태를 확인합니다.

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. 위의 명령이 `{"msg":"Token $TOKEN expired at 2021-09-28T02:03:37Z"}`과(와) 유사한 오류를 반환하는 경우 지원 티켓을 제출하여 새 API 토큰을 요청하십시오. 새 토큰을 받은 후 환경에서 구성을 업데이트합니다.

   지원 티켓을 제출하는 방법에 대해 알아보려면 지원 기술 자료에서 [Adobe Commerce 도움말 센터 사용 안내서 > 지원 티켓](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets)을 참조하세요.

   >[!NOTE]
   >
   >보안상의 이유로 현재 토큰을 취소하고 새 토큰을 생성해야 하므로 절대로 어떤 암호나 유효한/활성 API 토큰을 티켓에서 직접 공유하지 마십시오.
   >
   >Adobe Commerce 지원에서는 토큰에 액세스할 수 있으므로 티켓에 이 정보를 포함할 필요가 없습니다.

1. 명령이 오류를 반환하지 않으면 최신 버전의 [!DNL Fastly] 확장을 실행 중인지 확인하십시오. 1.2.203 이전 버전을 사용하는 경우 자격 증명을 테스트하려면 먼저 **[!UICONTROL Save Config]**&#x200B;을(를) 클릭해야 합니다.

## 개발자 설명서의 관련 내용:

* [Adobe Commerce용 클라우드 > [!DNL Fastly] > [!DNL Fastly] 서비스 계정 및 자격 증명](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly?lang=en#fastly-service-account-and-credentials)

* [Adobe Commerce용 클라우드 > 설정 [!DNL Fastly] > [!DNL Fastly] 자격 증명 테스트](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials)
