---
title: 'MDVA-21095: "search_tmp.."에 삽입은 대량 특성 업데이트 후 끝나지 않습니다.'
description: MDVA-21095 패치는 대량 속성 업데이트 후 'INSERT INTO' "search\_tmp..." 쿼리가 종료되지 않을 때 문제를 수정합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-21095입니다. 향후 버전에서는 이 문제를 해결할 계획이 없습니다.
exl-id: fd599473-b49a-4f9c-a13f-612d05e43f09
feature: Attributes, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-21095: 대량 속성 업데이트 후 &quot;search_tmp..&quot;에 INSERT가 종료되지 않음

MDVA-21095 패치는 대량 특성 업데이트 후 `INSERT INTO` &quot;search\_tmp...&quot; 쿼리가 끝나지 않을 때 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-21095입니다. 향후 버전에서는 이 문제를 해결할 계획이 없습니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

클라우드 인프라의 Adobe Commerce 2.3.2

**Adobe Commerce 버전과 호환:**

Adobe Commerce(모든 배포 방법) 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

`INSERT INTO` &quot;search\_tmp..&quot; 대량 특성 업데이트 후에는 끝나지 않습니다.

<u>재현할 단계</u>:

~30,000개의 항목으로 대량 속성 값 업데이트를 수행합니다.

<u>예상 결과</u>:

색인 재지정 프로세스는 예상대로 정상적으로 완료됩니다.

<u>실제 결과</u>:

색인 재지정 프로세스가 완료되지만 서버가 `pm.max_children` 매개 변수 값에 도달하고 PHP-fpm이 삭제될 때까지 많은 쿼리 `INSERT INTO` &quot;search\_tmp...&quot;가 시작되며, MySQL을 다시 시작하고 프로세스가 중지된 후에도 이러한 쿼리가 계속 발생합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://devdocs.magento.com/cloud/project/project-patch.html).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)를 참조하십시오.
