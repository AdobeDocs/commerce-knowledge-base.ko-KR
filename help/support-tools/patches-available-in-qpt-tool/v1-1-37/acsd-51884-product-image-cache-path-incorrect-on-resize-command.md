---
title: 'ACSD-51884: 크기 조정 명령에서 제품 이미지 캐시 경로가 잘못됨'
description: ACSD-51884 패치를 적용하여 resize 명령을 실행한 후 제품 이미지 캐시 경로가 잘못되는 Adobe Commerce 문제를 해결합니다.
feature: Products
role: Admin
exl-id: cf542c4b-07b1-4f05-95bc-82bc098bcd4d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-51884: 크기 조정 명령에서 제품 이미지 캐시 경로가 잘못됨

ACSD-51884 패치는 resize 명령을 실행한 후 제품 이미지 캐시 경로가 잘못되는 내부 오류 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.37이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-51884입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7- 2.4.7

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

크기 조정 명령에서 제품 이미지 캐시 경로가 올바르지 않게 됩니다.

<u>재현 단계</u>:

1. 새 웹 사이트/스토어/스토어를 만듭니다.
1. 제품을 만들어 두 웹 사이트에 할당하고 제품 이미지를 업로드합니다.
1. 새 테마를 만듭니다(첨부된 Adobe.zip 참조).
1. `app/design/Adobe/theme/etc/view.xml`에서 변경:

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">1</var>
</vars>
```

끝

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">0</var>
</vars>
```

1. 이전에 만든 스토어에 테마를 적용합니다.
1. 두 번째 웹사이트에서 제품 페이지를 확인하세요. 제품 이미지가 올바르게 표시됩니다.
1. 플러시 캐시 사용:
   `bin/magento cache:flush`
1. 두 번째 웹사이트에서 제품 페이지를 확인하세요.

<u>예상 결과</u>:

제품 이미지가 올바르게 표시됩니다.

<u>실제 결과</u>:

제품 이미지가 없습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
