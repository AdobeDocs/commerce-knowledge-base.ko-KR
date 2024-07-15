---
title: "ACSD-51700: 다운로드 가능한 제품 편집 페이지에서 스토어 보기를 전환하는 도중 오류 발생"
description: ACSD-51700 패치를 적용하여 관리자의 다운로드 가능한 제품 편집 페이지에서 스토어 보기를 전환할 때 오류가 발생하는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin
exl-id: 652876a5-275d-437f-9cb3-baf4e7b23aae
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51700: 다운로드 가능한 제품 편집 페이지에서 스토어 보기를 전환하는 도중 오류 발생

ACSD-51700 패치는 관리자의 다운로드 가능한 제품 편집 페이지에서 스토어 보기를 전환할 때 오류가 발생하는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.33이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-51700입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p1

## 문제

관리자의 다운로드 가능한 제품 편집 페이지에서 스토어 보기를 전환할 때 오류가 발생합니다.

<u>재현 단계</u>:

1. 이름, [!DNL SKU] 및 가격으로 다운로드 가능한 제품을 만드십시오. 링크를 추가하지 않고 제품을 저장합니다.
1. 모든 스토어 보기에서 기본 스토어 보기로 전환합니다.
1. 다운로드 가능한 제품에 대한 링크를 만들고 저장합니다.
1. 기본 저장소 보기에서 모든 저장소 보기로 전환합니다.

<u>예상 결과</u>:

연결된 제품이 표시됩니다.

<u>실제 결과</u>:

다음 오류가 표시됩니다.

*사용되지 않는 기능: number_format(): float 유형의 매개 변수 #1($num)에 null을 전달하는 것은 vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php에서 228행의 더 이상 사용되지 않습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
