---
title: "파일을 삭제할 수 없습니다. 경고! 연결 해제:  [!DNL Admin]에서 해당 파일 또는 디렉터리 오류가 없습니다."
description: 이 문서에서는 *파일을 삭제할 수 없는 문제에 대한 해결 방법을 제공합니다. 경고!연결 해제 [!DNL Javascript/CSS] 플러시를 수행할 때  [!DNL Admin] 에서 해당 파일 또는 디렉터리 오류* 없음.
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *파일을 삭제할 수 없습니다. 경고!연결 해제: [!DNL Admin]에서 해당 파일 또는 디렉터리 오류*&#x200B;이(가) 없습니다.

이 문서에서는 오류 *이(가) 표시되는 문제를 해결할 수 있습니다. 파일을 삭제할 수 없습니다. Warning!unlink: [!DNL JavaScript/CSS] 플러시를 수행할 때 [!DNL Commerce Admin]에서 해당 파일 또는 디렉터리 오류*&#x200B;이(가) 없습니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce 2.4.0 - 2.4.6, 모든 배포 방법

## 문제

[!DNL JS/CSS] 플러시를 수행하면 오류가 발생합니다.

*&quot;/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b&quot; 파일을 삭제할 수 없습니다. 경고!unlink(/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b): 해당 파일 또는 디렉터리가 없습니다*

또는: [!DNL Admin]에 위의 오류가 표시되고, [!DNL New Relic] 또는 배포 로그에 유사한 오류가 표시됩니다.

또는: 고급 보고에 액세스할 수 없으며 analytics_collect_data cron 작업이 다음 오류로 실패합니다.

*&quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0&quot; 파일을 삭제할 수 없습니다. 경고!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0): 해당 파일 또는 디렉터리가 없습니다*

<u>재현 단계:</u>

방법 1:

1. [!DNL Admin]에 로그인합니다.
1. **[!UICONTROL System]** > **[!UICONTROL Cache Management]**(으)로 이동합니다.
1. **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**&#x200B;을(를) 클릭합니다.

방법 2:

1. [!DNL Admin]에 로그인합니다.
1. **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**(으)로 이동합니다.
1. [!UICONTROL Base URL] 또는 [!UICONTROL Base URL (Secure)]을(를) 변경합니다.
1. **[!UICONTROL Save Config]**&#x200B;을(를) 클릭합니다.

## 솔루션

Adobe Commerce on Cloud infrastructure에 패치를 포함하는 [!DNL magento/magento-cloud-patches] 1.0.22가 설치되어 있는 경우 ACSD-50165을 별도로 설치할 필요가 없습니다.

클라우드 인프라의 Adobe Commerce: Commerce용 클라우드 패치를 이 수정 사항이 포함된 1.0.22(**이상**)로 업그레이드: [Commerce용 클라우드 패치](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Adobe Commerce 온-프레미스: [품질 패치 도구 > 사용량](/docs/commerce-operations/tools/quality-patches-tool/usage.html)을(를) 사용하여 ACSD-50165을 적용합니다. ACSD-50165 패치에는 [!DNL QPT] [v1.1.30.](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)이(가) 포함되어 있습니다.

## 관련 읽기

* Commerce 도구 안내서의 [[!DNL Quality Patches Tool] > 릴리스 정보](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html).
* [[!DNL Quality Patches Tool]: Commerce Tools 안내서에서 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko) 패치를 검색합니다.
