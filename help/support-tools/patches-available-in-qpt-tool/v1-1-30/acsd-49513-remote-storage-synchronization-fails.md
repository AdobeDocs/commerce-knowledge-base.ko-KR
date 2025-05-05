---
title: 'ACSD-49513: 원격 스토리지 동기화 실패'
description: ACSD-49513 패치를 적용하여 0바이트 파일로 인해 원격 스토리지 동기화가 실패하는 Adobe Commerce 문제를 해결합니다.
exl-id: fce5f60f-d21f-40cd-8d8a-a1a26e0fbe75
feature: Iaas, Storage
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-49513: 0바이트 파일로 인해 원격 저장소 동기화가 실패합니다.

ACSD-49513 패치는 0바이트 파일로 인해 원격 스토리지 동기화가 실패하는 문제를 해결합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-49513입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.4-p3

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

0바이트 파일로 인해 원격 저장소 동기화에 실패합니다.

<u>재현 단계</u>:

1. AWS S3를 원격 스토리지로 구성합니다.
1. `[bin/magento remote-storage:sync]`을(를) 실행하여 동기화가 시작 부분에서 제대로 작동하는지 확인하십시오.
1. `[pub/media]` 내부에 0바이트 파일을 만듭니다.
1. `[bin/magento remote-storage:sync]`을(를) 다시 실행합니다.

<u>예상 결과</u>:

AWS S3는 S3 직접 푸시에서 0바이트 파일을 허용하므로 오류가 없습니다.

<u>실제 결과</u>:

다음 오류가 발생합니다.

```PHP
Uploading media files to remote storage.
In File.php line 387:
  The file or directory "pub/media/xxxx.file" cannot be copied to "*.amazonaws.com/media/xxxx.file"
```

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 패치 설치 후 추가 단계 필요

(이 섹션은 선택 사항입니다. 문제를 해결하기 위해 패치를 적용한 후 몇 가지 단계가 필요할 수 있습니다.) 

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
