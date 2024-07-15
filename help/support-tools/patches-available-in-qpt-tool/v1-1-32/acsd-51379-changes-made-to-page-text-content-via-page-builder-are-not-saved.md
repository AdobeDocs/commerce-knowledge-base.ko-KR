---
title: "ACSD-51379: [!DNL Page Builder] 을(를) 통한 페이지의 텍스트 콘텐츠 변경 내용이 저장되지 않음"
description: ACSD-51379 패치를 적용하여  [!DNL Page Builder] 을(를) 통해 페이지의 텍스트 콘텐츠에 대한 변경 내용이 저장되지 않는 Adobe Commerce 문제를 해결합니다.
exl-id: e274ca03-b675-4ded-9820-1d60978685d0
feature: Page Builder, Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-51379: [!DNL Page Builder]을(를) 통한 페이지의 텍스트 콘텐츠에 대한 변경 내용이 저장되지 않습니다.

ACSD-51379 패치는 [!DNL Page Builder]을(를) 통해 페이지의 텍스트 콘텐츠에 대한 변경 내용이 저장되지 않는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51379입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

[!DNL Page Builder]을(를) 통해 페이지의 텍스트 콘텐츠에 대한 변경 내용이 저장되지 않습니다.

<u>재현 단계</u>:

1. 관리자에 로그인합니다.
1. **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**(으)로 이동합니다.
1. **[!UICONTROL Content]** 탭에서 행 하나와 텍스트 요소 하나를 사용하여 테스트 페이지를 만듭니다.
1. 페이지를 저장하고 **[!UICONTROL Content]** 탭으로 돌아갑니다.
1. 텍스트를 선택하고 변경하여 편집합니다.

   **참고:** 편집기를 활성화하지 않고 텍스트를 선택하고 변경하는 경우에만 문제를 재현할 수 있습니다.

1. 테스트 페이지에서 **[!UICONTROL Save and Close]** 단추를 클릭합니다.
1. 테스트 페이지를 다시 열고 **[!UICONTROL Content]** 탭을 확인합니다.

<u>예상 결과</u>:

원본 및 복제된 텍스트 요소에 대해 새 텍스트가 성공적으로 저장됩니다.

<u>실제 결과</u>:

텍스트 요소는 성공적으로 복제되었지만 새 텍스트는 저장되지 않습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
