---
title: 'ACSD-59378: 저장소 수준 [!DNL URL] 가져오는 동안 잘못 업데이트된 다시 쓰기'
description: ACSD-59378 패치를 적용하여 가져오는 동안 저장소 수준 [!DNL URL] 재작성이 잘못 업데이트되는 Adobe Commerce 문제를 해결합니다.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 3f400c3e325c3f377a5e12170b08615ebeadbcd1
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# ACSD-59378: 가져오기 중에 저장소 수준 [!DNL URL]이(가) 잘못 업데이트된 리쓰기를 다시 작성합니다.

ACSD-59378 패치는 가져오는 동안 저장소 수준 [!DNL URL] 다시 쓰기가 잘못 업데이트되는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-59378입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

Adobe Commerce(모든 배포 방법) 2.4.5-p5

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.4.5x(모든 버전 2.4.5)

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

가져오는 동안 저장소 수준 [!DNL URL] 다시 쓰기가 잘못 업데이트되었습니다.

<u>재현 단계</u>:

1. **모든 스토어 보기** 범위에서 `url_key = key_default`을(를) 사용하여 제품을 만드십시오.
1. **기본 저장소 보기** 범위에서 `url_key = key_store`을(를) 설정합니다.
1. 제품 내보내기.
1. 다음 데이터가 포함된 이 제품에 대한 [!DNL CSV] 파일을 가져옵니다.
   * `store_view_code` 열이 **모든 저장소 보기** 범위에 적용되도록 *empty*(으)로 설정되어 있습니다.
   * `url_key`이(가) 기본 키 *`key_default`*(으)로 설정되어 있습니다.

<u>예상 결과</u>:

재정의된 `url_key`이(가) 없는 저장소 보기에 대해서만 [!DNL URL] 다시 쓰기가 다시 생성됩니다(기본값 `url_key`이(가) 적용됨).

<u>실제 결과</u>:

`key_store`개의 [!DNL URL] 다시 쓰기가 삭제되었지만 제품에 대한 **기본 저장소 보기** 수준의 [!DNL URL] 다시 쓰기가 여전히 *`key_store`*(으)로 설정되어 있습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
