---
title: 'ACSD-48634: [!DNL Google Analytics Content Experiments] 사용 시  [!DNL JS] 오류 발생'
description: ' [!DNL Google Analytics Content Experiments] 이(가) 활성화된 경우  [!DNL staging] 업데이트 페이지에서  [!DNL JS] 오류를 수정하려면 ACSD-48634 패치를 적용하십시오.'
exl-id: 4a9f201d-eaf0-4e43-a1a1-0a9ffb0a2ead
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-48634: [!DNL Google Analytics Content Experiments]을(를) 사용할 때 [!DNL JS]개의 오류 발생

ACSD-48634 패치는 [!DNL Google Analytics Content Experiments]을(를) 사용하도록 설정할 때 [!DNL staging] 업데이트 페이지에서 [!DNL JS] 오류를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-48634입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL Google Analytics Content Experiments]을(를) 사용하도록 설정한 경우 [!DNL staging] 업데이트 페이지에서 [!DNL JS] 오류가 발생합니다.

<u>재현 단계</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**&#x200B;에서 추가 웹 사이트, 스토어 및 **[!UICONTROL Store View]**&#x200B;을(를) 만듭니다. **[!UICONTROL Store View]**&#x200B;이(가) *[!UICONTROL Enabled]*&#x200B;인지 확인하십시오.
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**(으)로 이동하여 **[!DNL Configure Google Analytics]**&#x200B;을(를) 구성합니다.
   * **[!DNL Main]** 및 추가 웹 사이트 [!DNL scope]의 경우:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
      * 다른 필드의 경우 **[!DNL Uncheck]** *[!UICONTROL Use Default]*&#x200B;을(를) 사용하지만 변경하지 마십시오.
   * **[!DNL Default Config]** [!DNL scope]의 경우:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. **[!UICONTROL Enable]**&#x200B;을(를) *[!UICONTROL Yes]*&#x200B;에서 *[!UICONTROL No]*(으)로 변경하여 **[!DNL Default Config]** [!DNL scope]에서 **[!DNL Configure Google Analytics]**&#x200B;을(를) 사용하지 않도록 설정하십시오. 다른 것은 변경하지 않도록 주의하십시오!
1. **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**(으)로 이동합니다.
1. **[!UICONTROL category]**&#x200B;을(를) 만들고 편집한 다음 예약된 업데이트를 추가합니다.
   * 모든 이름, 미래의 시작 날짜, 미래의 종료 날짜 및 **[!UICONTROL category]**&#x200B;의 변경 사항([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. 업데이트를 저장하고 [!DNL browser developer console]에 오류가 있는지 확인하십시오.

<u>예상 결과</u>:

[!DNL JS] 오류가 없으며 [!DNL staging] 업데이트에 대한 변경 내용이 저장되었습니다.

<u>실제 결과</u>:

콘솔에 [!DNL JS]개의 오류가 표시되고 양식의 형식이 잘못되었으며 저장 후 [!DNL spinner]이(가) 비활성화되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
