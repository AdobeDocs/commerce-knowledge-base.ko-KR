---
title: "ACSD-52041: 페이지 빌더 렌더링이 잠금을 해제하지 않음"
description: ACSD-52041 패치를 적용하여 잠금 해제 없이 5초 동안 페이지 빌더가 렌더링되는 Adobe Commerce 문제를 해결합니다.
feature: Page Builder
role: Admin, Developer
exl-id: f2a1fd36-2098-46a7-aa42-3a5a0014adc9
source-git-commit: b5c253a5c0651c6027c0795edb2f230bd65f734a
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# ACSD-52041: 페이지 빌더 렌더링이 잠금을 해제하지 않음

ACSD-52041 패치는 잠금 해제 없이 5초 동안 페이지 빌더가 렌더링되는 문제를 해결합니다. 이 패치는 [!DNL Quality Patches Tool (QPT)] 1.1.48이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-52041-v2입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 및 2.4.6 - 2.4.6-p2.



>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.


## 문제

**[!DNL Page Builder]**&#x200B;이(가) 잠금을 해제하지 않고 *5*&#x200B;초 동안 렌더링됩니다.

<u>재현 단계</u>:

1. CMS 페이지, 제품 페이지 또는 **[!DNL Page Builder]**&#x200B;이(가) 있는 항목을 편집합니다.
1. 변경 사항을 저장합니다.
1. 페이지 저장 시간을 확인합니다.

<u>예상 결과</u>

콘텐츠가 저장됩니다. 브라우저 로그에서 오류가 발견되지 않았습니다.

<u>실제 결과</u>

저장이 완료되는 데 평소보다 오래 걸립니다.
콘솔에서 오류 발생: ``Page Builder was rendering for 5 seconds without releasing locks``

## 패치 적용

버전 **2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4 및 2.4.6 - 2.4.6-p2**&#x200B;에 대해 개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용하십시오.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)을 참조하세요.
