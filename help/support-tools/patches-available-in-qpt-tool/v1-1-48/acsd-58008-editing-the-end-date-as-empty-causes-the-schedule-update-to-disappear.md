---
title: 'ACSD-58008: 종료 날짜를 *empty*로 편집하면 일정 업데이트가 사라짐'
description: ACSD-58008 패치를 적용하여 종료 날짜를 *empty*로 편집하면 일정 업데이트가 사라지는 Adobe Commerce 문제를 해결합니다.
feature: Staging, Page Content
role: Admin, Developer
exl-id: bfa590b8-377b-49dd-9aff-f89b8fd815c4
source-git-commit: d7ace1f20defb01105d4a241f971b06fca052215
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-58008: 종료 날짜를 *empty*(으)로 편집하면 일정 업데이트가 사라집니다

ACSD-58008 패치는 종료 날짜를 *empty*(으)로 편집하면 일정 업데이트가 사라지는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-58008입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p5

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

종료 날짜를 *empty*(으)로 편집하면 일정 업데이트가 사라집니다

<u>재현 단계</u>:

1. [!UICONTROL Admin](으)로 로그인합니다.
1. **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**(으)로 이동하여 페이지를 만듭니다.
1. 만든 페이지를 선택하고 **[!UICONTROL Schedule New Update]**&#x200B;을(를) 클릭합니다. *(페이지의 오른쪽 상단 모서리에서 탐색)*.
1. 4개의 업데이트를 만듭니다. *(예:* 2 *분 증가)*.
1. *업데이트 2*&#x200B;을(를) 업데이트하고 지난 *업데이트 4*&#x200B;보다 이전 시간으로 시간을 변경합니다.
1. 수행한 업데이트를 저장합니다.

<u>예상 결과</u>:

일정 업데이트에 *업데이트 3*&#x200B;이 표시됩니다.

<u>실제 결과</u>:

일정 업데이트에 *업데이트 3*&#x200B;이 표시되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
