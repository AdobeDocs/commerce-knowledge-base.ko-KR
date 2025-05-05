---
title: "ACSD-51853: 복사된 텍스트 스타일이 페이지 빌더를 사용하여 적용되지 않음"
description: ACSD-51853 패치를 적용하여 페이지 빌더를 사용할 때 복사된 텍스트 스타일이 적용되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Page Builder
role: Admin
exl-id: 1efd3147-1ae0-468b-af04-1632fbaaefda
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51853: 복사된 텍스트 스타일이 페이지 빌더를 사용하여 적용되지 않음

ACSD-51853 패치는 페이지 빌더를 사용할 때 복사된 텍스트 스타일이 적용되지 않는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.34가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51853입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

페이지 빌더를 사용하면 복사된 텍스트 스타일이 적용되지 않습니다

<u>재현 단계</u>:

1. 책임자에 로그인합니다.
1. &#x200B;> **콘텐츠** > **페이지** > **모든 페이지 열기** > **페이지 빌더로 편집**&#x200B;으로 이동합니다.
1. **[!UICONTROL Elements]**&#x200B;에서 행 및 *텍스트*&#x200B;을(를) 드래그합니다.
1. **보강된 콘텐츠**&#x200B;를 복사하고 해당 텍스트를 **[!UICONTROL Page Builder]**&#x200B;에 붙여 넣으십시오.

<u>예상 결과</u>

복사된 텍스트를 모든 스타일로 붙여넣습니다.

<u>실제 결과</u>

복사된 텍스트를 일반 텍스트로 붙여넣으며 모든 스타일이 손실됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
