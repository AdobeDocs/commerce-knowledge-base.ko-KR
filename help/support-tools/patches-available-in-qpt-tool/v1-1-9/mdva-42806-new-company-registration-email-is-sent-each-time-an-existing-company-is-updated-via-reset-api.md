---
title: 'MDVA-42806: 기존 회사가 업데이트될 때마다 새 회사 등록 이메일이 전송됩니다.'
description: MDVA-42806 패치는 REST API를 통해 기존 회사가 업데이트될 때마다 새 회사 등록 이메일이 전송되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9가 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-42806입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: 957b89f7-cd4d-4c94-8d1d-c30442aafa6a
feature: REST, B2B, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-42806: 기존 회사가 업데이트될 때마다 새 회사 등록 이메일이 전송됩니다.

MDVA-42806 패치는 REST API를 통해 기존 회사가 업데이트될 때마다 새 회사 등록 이메일이 전송되는 문제를 해결합니다. 이 패치는 다음 경우에 사용할 수 있습니다. [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9가 설치되었습니다. 패치 ID는 MDVA-42806입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

REST API를 통해 기존 회사가 업데이트될 때마다 새 회사 등록 이메일이 전송됩니다.

<u>전제 조건</u>:

B2B 모듈이 설치되었습니다.

<u>재현 단계</u>:

1. 회사 계정을 만듭니다.
1. 사용 `/V1&#x200B;/company&#x200B;/<company_id>` 엔드포인트. 생성된 회사를 업데이트하려면 다음을 참조하십시오 [회사 업데이트](https://devdocs.magento.com/guides/v2.4/b2b/company-object.html#update-the-company) 개발자 설명서에서 확인할 수 있습니다. 다음은 샘플 페이로드입니다.

```php
{
    "company": {
        "id": 2,
        "status": 1,
        "company_name": "Company",
        "company_email": "company@example.test",
        "street": [
            "Test"
        ],
        "city": "Test",
        "country_id": "US",
        "region_id": "1",
        "postcode": "12345",
        "telephone": "8009994301",
        "customer_group_id": 2,
        "sales_representative_id": 1,
        "super_user_id": 2
    }
}
```

<u>예상 결과</u>:

API가 기존 회사를 업데이트하고 있으므로 &quot;새 회사 등록 요청&quot;이라는 이메일이 전송되지 않습니다.

<u>실제 결과</u>:

API 요청이 전송될 때마다 &quot;새 회사 등록 요청&quot;이라는 이메일이 전송됩니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 개발자 설명서에서 확인할 수 있습니다.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html) 개발자 설명서에서 확인할 수 있습니다.

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 툴 출시: 품질 패치를 셀프서비스할 수 있는 새로운 툴](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [품질 패치 도구 를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [QPT에서 사용 가능한 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 개발자 설명서에서 확인할 수 있습니다.
