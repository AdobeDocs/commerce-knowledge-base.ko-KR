---
title: 'ACSD-51574: 다른 이미지로 대체할 때 프론트엔드에 이미지가 업데이트되지 않음'
description: ACSD-51574 패치를 적용하여 다른 이미지로 교체한 후 프론트엔드에 이미지가 업데이트되지 않는 Adobe Commerce 문제를 해결합니다.
feature: Configuration
role: Admin
exl-id: a6f26126-71c3-43c2-bba4-60a914d7ec11
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-51574: 다른 이미지로 대체할 때 프론트엔드에 이미지가 업데이트되지 않음

ACSD-51574 패치는 다른 이미지로 교체한 후 프론트엔드에서 이미지가 업데이트되지 않는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.37이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51574입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

이미지는 다른 이미지로 교체한 후 프론트엔드에서 업데이트되지 않습니다.

<u>재현 단계</u>:

1. 몇 가지 이미지로 제품을 만듭니다.
1. 제품을 편집하고 알려진 이름의 이미지를 업로드하십시오(예: *image.jpg*).
1. 제품을 저장합니다.
1. 제품을 다시 편집하고 이미지의 이전 버전을 삭제한 다음 같은 이름으로 이미지의 새 버전을 업로드합니다. **문제를 보려면 새 버전이 눈에 띄게 다른지 확인하십시오.**
1. 제품을 저장합니다. 관리자와 프론트엔드 모두에 이미지가 표시됩니다.
1. 제품을 다시 편집하고 동일한 새 이미지를 다시 업로드합니다(동일한 이름 사용).
1. 제품을 저장하고 프론트엔드의 제품 페이지를 확인합니다.

<u>예상 결과</u>:

두 번째로 업로드하는 이미지는 이름이 변경된 이미지 이름과 함께 새 이미지여야 합니다.

<u>실제 결과</u>:

두 번째로 업로드한 이미지는 동일한 새 이미지가 아닌 이전에 삭제된 이전 버전의 이미지입니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
