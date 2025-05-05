---
title: 'ACSD-55414: MariaDB가 entitys_ids를 캐스팅하려고 할 때 성능이 저하됨'
description: ACSD-55414 패치를 적용하여 Adobe Commerce 문제를 해결합니다. MariaDB가 'entys_ids'를 문자열에서 정수로 변환하려고 하면 리인덱싱 성능이 저하됩니다.
feature: Attributes
role: Admin, Developer
exl-id: 008a4fda-5d80-47e2-8fb4-c1e39d15a6ba
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-55414: MariaDB가 `entitys_ids`을(를) 캐스팅하려고 할 때 성능이 저하됩니다.

ACSD-55414 패치는 MariaDB가 `entitys_ids`을(를) 문자열에서 정수로 변환하려고 할 때 리인덱싱 성능이 저해되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.41이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-55414입니다. 이 문제는 Adobe Commerce 2.4.6에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p4

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

MariaDB가 문자열에서 정수로 `entitys_ids`을(를) 캐스팅하려고 하면 리인덱싱이 수행되지 않습니다.

<u>재현 단계</u>:

1. *50000* 간단한 제품을 설정하여 `setup/performance-toolkit/profiles/ce/small.xml`을(를) 업데이트합니다.
1. 명령을 실행하여 이 프로필을 생성합니다. `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. 색인 재지정 실행: `bin/magento indexer:reindex catalog_product_attribute`.

<u>예상 결과</u>:

색인 재지정은 완료하는 데 시간이 적당히 걸립니다.

<u>실제 결과</u>:

색인 재지정은 완료하는 데 시간이 너무 오래 걸립니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
