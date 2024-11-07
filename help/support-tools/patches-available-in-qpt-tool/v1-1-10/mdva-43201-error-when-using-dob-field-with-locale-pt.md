---
title: 'MDVA-43201: 로케일 PT로 DOB 필드를 사용할 때 오류 발생'
description: MDVA-43201 패치는 포르투갈어 로케일에 대한 고객 등록 양식에서 DOB 고객 속성을 사용할 때 오류가 발생하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43201입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 02979378-adc1-4a1a-93bf-a35ad50e6b80
feature: B2B, Cache
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43201: 로케일 PT로 DOB 필드를 사용할 때 오류 발생

MDVA-43201 패치는 포르투갈어 로케일에 대한 고객 등록 양식에서 DOB 고객 속성을 사용할 때 오류가 발생하는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-43201입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

DOB 고객 특성이 포르투갈어 로케일에 대한 고객 등록 양식에 추가되면 이 양식에서 iterator_to_array()에 전달된 *인수 1이(가) 인터페이스 트래블 가능, null을 구현해야 함*&#x200B;을(를) 제공합니다.

<u>필수 구성 요소</u>:

B2B 모듈이 설치되어 있습니다.

<u>재현 단계</u>:

1. 관리자 > **스토어** > **구성** > **일반** > **로케일 옵션**(으)로 이동하여 로케일을 **포르투갈어(포르투갈)**(으)로 설정하고 **저장**&#x200B;을 클릭합니다.
1. 캐시를 다시 인덱싱하고 지웁니다.
1. **스토어** > **특성** > **고객**(으)로 이동합니다.
1. DOB 고객 특성을 열고 **Storefront에 표시**&#x200B;를 **예**(으)로 설정합니다.
1. **Form에서**&#x200B;에 사용할 모든 양식을 선택하십시오.
1. 속성을 저장합니다.
1. 프론트엔드의 새 계정 만들기 페이지로 이동합니다.

<u>예상 결과</u>:

포르투갈 스토어의 고객 등록 양식은 DOB 속성을 추가하는 데 오류를 주지 않습니다.

<u>실제 결과</u>:

포르투갈 스토어의 고객 등록 양식에서 DOB 속성 추가 시 오류가 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하십시오.
