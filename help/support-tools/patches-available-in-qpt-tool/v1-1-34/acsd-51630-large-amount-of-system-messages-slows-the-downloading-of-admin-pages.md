---
title: 'ACSD-51630: 많은 시스템 메시지가 관리 페이지의 다운로드를 느리게 합니다.'
description: ACSD-51630 패치를 적용하여 대량의 시스템 메시지가 관리 페이지 다운로드를 느리게 하는 Adobe Commerce 성능 문제를 해결합니다.
feature: Admin Workspace, System
role: Admin
exl-id: 28f85199-625e-4299-bbca-8d2fc75df602
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# ACSD-51630: 많은 시스템 메시지가 관리 페이지의 다운로드를 느리게 합니다.

ACSD-51630 패치는 대량의 시스템 메시지가 관리 페이지 다운로드를 느리게 하는 성능 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.34가 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51630입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 &lt; 2.4.6-p1

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

많은 시스템 메시지가 관리 페이지의 다운로드를 느리게 합니다.

<u>재현 단계</u>:

1. `/rest/async/v1/products/ {sku}` DELETE에 많은 요청(~50k)을 합니다.
1. **관리 페이지**&#x200B;에 액세스합니다.

<u>예상 결과</u>:

적절한 시간에 페이지가 로드됩니다. 표시되는 메시지만 로드해야 합니다.

<u>실제 결과</u>:

페이지를 로드하는 데 너무 오래 걸립니다. 기존의 모든 메시지는 데이터베이스에서 로드됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
