---
title: 'MDVA-38559: /V1/customers/search API가 오류를 반환합니다.'
description: MDVA-38559 패치에서는 "/V1/customers/search" API가 두 개 이상의 구독을 가진 고객에 대해 오류를 반환하는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-38559입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.
exl-id: 434fe78c-c384-4fa8-b26a-cb00007e490e
feature: REST, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-38559: /V1/customers/search API에서 오류 반환

MDVA-38559 패치는 다음 문제를 해결합니다. `/V1/customers/search` API가 두 개 이상의 구독을 가진 고객에 대해 오류를 반환합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15가 설치되어 있습니다. 패치 ID는 MDVA-38559입니다. 이 문제는 Adobe Commerce 2.4.3에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.1-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`/V1/customers/search` API가 두 개 이상의 구독을 가진 고객에 대해 오류를 반환합니다.

<u>전제 조건</u>:

Adobe Commerce 스토어는 둘 이상의 웹 사이트를 사용합니다.

<u>재현 단계</u>:

1. 다음으로 이동 **저장** > **구성** > **고객** > **고객 구성** > **계정 공유 옵션** 및 선택 **글로벌**.
1. 다음으로 이동 **고객** > **모든 고객**, 선택 **편집** 모든 고객에서 다음을 선택합니다 **뉴스레터**.
1. 두 개 이상의 웹 사이트에 대한 뉴스레터를 구독하고 고객을 저장합니다.
1. 다음 요청을 보냅니다.

```REST API
V1/customers/search?searchCriteria[filterGroups][0][filters][0][field]=email&searchCriteria[filterGroups][0][filters][0][value]=test@example.com&searchCriteria[filterGroups][0][filters][0][conditionType]=eq
```

<u>예상 결과</u>:

고객의 검색 결과가 표시됩니다.

<u>실제 결과</u>:

다음 오류는 exception.log에 기록됩니다. *ID가 &quot;1&quot;인 항목(Magento\Customer\Model\Customer\Interceptor)이 이미 있습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
