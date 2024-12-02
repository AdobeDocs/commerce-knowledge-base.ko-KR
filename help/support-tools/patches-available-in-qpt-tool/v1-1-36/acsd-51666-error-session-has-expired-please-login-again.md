---
title: 'ACSD-51666: "세션이 만료되었습니다. 다시 로그인하십시오." 오류 로그인 후'
description: ACSD-51666 패치를 적용하여 오류가 발생한 Adobe Commerce 문제를 해결합니다. *세션이 만료되었습니다. 다시 로그인하십시오.* 로그인하려고 시도한 후에 발생합니다.
feature: Customers
role: Admin, Developer
exl-id: c3913f1c-f401-440b-b6b3-10702f13fff5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-51666: 오류 *세션이 만료되었습니다. 다시 로그인하십시오.로그인 후*

ACSD-51666 패치를 통해 오류 *이(가) 만료된 문제가 해결되었습니다. 다시 로그인하십시오.*&#x200B;은(는) 로그인하려고 시도한 후에 발생합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-51666입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

오류 *이(가) 발생했습니다. 세션이 만료되었습니다. 다시 로그인하십시오.다른 장치에서 암호를 다시 설정한 후 한 장치에서 새 암호로 로그인하려고 할 때*. 사용자 지정 모듈에서 추가한 페이지에 추가 Ajax 요청이 있는 경우에만 발생합니다.

<u>재현 단계</u>:

1. 상점 첫 화면의 모든 페이지에 Ajax 요청을 추가하는 사용자 지정 모듈을 설치합니다.
1. 새 계정을 만듭니다.
1. 로그아웃한 후 로그인 페이지로 돌아갑니다.
1. 다른 브라우저에서 *암호 찾기* 링크를 열고 *암호 재설정* 이메일을 보냅니다.
1. 첫 번째 브라우저에서 암호 재설정 이메일을 열고 새 암호를 설정합니다.
1. 두 번째 브라우저에서 로그인해 보십시오.

<u>예상 결과</u>:

첫 번째 시도에 성공적으로 로그인할 수 있습니다.

<u>실제 결과</u>:

* *세션이 만료되었습니다. 다시 로그인하십시오.* 오류입니다.
* 로그인하지 않았으며 홈페이지로 리디렉션되었습니다.
* 두 번째 로그인 시도가 성공했습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
