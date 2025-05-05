---
title: 'ACSD-53824: 설치 업그레이드 시 배포가 실패했습니다.'
description: ACSD-53824 패치를 적용하여 설치 업그레이드 시 배포가 실패하는 Adobe Commerce 문제를 해결합니다
feature: Attributes, Upgrade
role: Admin, Developer
exl-id: a071745f-967f-42c8-9e20-52b248e4fefa
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-53824: 설치 업그레이드 시 배포가 실패했습니다.

ACSD-53824 패치는 설치 업그레이드 시 배포가 실패하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-53824입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5 - p2

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

설치 업그레이드 시 배포가 실패했습니다.

<u>재현 단계</u>:

1. Galera Cluster에 **[!DNL MariaDB]**&#x200B;을(를) 사용하여 인프라를 설치합니다.
1. `wsrep_max_ws_size`을(를) 최대 *2GB*(으)로 설정합니다.
1. 새 Adobe Commerce 인스턴스를 설치합니다.
1. 중간 성능 프로파일에서 고정장치를 생성합니다.
   `php bin/magento setup:performance:generate-fixtures -s setup/performance-toolkit/profiles/ee/medium.xml`
1. **12000**&#x200B;개 이상의 다중 선택 특성을 생성합니다.
1. 그런 다음 `Run setup: Upgrade` 명령을 사용합니다.

<u>예상 결과</u>:

`setup:upgrade`이(가) 오류 없이 완료됩니다.

<u>실제 결과</u>:

`setup:upgrade`이(가) 실패하고 [!DNL MySQL] 오류가 발생했습니다.

`Allowed memory size of 6442450944 bytes exhausted in ../module-catalog/Setup/Patch/Data/UpdateMultiselectAttributesBackendTypes.php`

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
