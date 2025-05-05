---
title: 'MDVA-43451: 공유 카탈로그의 가격 및 구조를 설정할 때 오류 발생'
description: MDVA-43451 패치는 사용자가 공유 카탈로그의 가격 및 구조를 설정할 수 없는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-43451입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.
exl-id: 78de2e98-dfd7-4829-8e3f-76eadf5570e8
feature: Catalog Management
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-43451: 공유 카탈로그의 가격 및 구조를 설정할 때 오류 발생

MDVA-43451 패치는 사용자가 공유 카탈로그의 가격 및 구조를 설정할 수 없는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-43451입니다. 이 문제는 Adobe Commerce 2.4.5에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.3 - 2.4.4

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

공유 카탈로그에 대한 가격 책정 및 구조를 설정할 수 없습니다. 다음 메시지가 표시됩니다. *요청한 스토어를 찾을 수 없습니다. 스토어를 확인하고 다시 시도하십시오.*

<u>재현 단계</u>:

1. 사용자 지정 웹 사이트를 만듭니다. 웹 사이트의 ID는 0, 1, 2여야 합니다.
1. 위 웹 사이트 아래에 스토어 한 개를 만듭니다. 상점의 ID는 0,1,2여야 합니다.
1. 위 스토어에 대한 스토어 보기를 3개 만듭니다. 스토어 조회수의 ID는 0,1, 2, 3, 4여야 합니다.
1. ID가 2인 스토어 보기를 삭제합니다. 이제 매장 표는 아래 표와 비슷하게 생겼습니다.

   ```bash
   MariaDB [m24devinvb2b]> SELECT store_id,code,website_id,group_id,name FROM store;
   +----------+----------------+------------+----------+--------------------+
   | store_id | code           | website_id | group_id | name               |
   +----------+----------------+------------+----------+--------------------+
   |        0 | admin          |          0 |        0 | Admin              |
   |        1 | default        |          1 |        1 | Default Store View |
   |        3 | web1storeview2 |          2 |        2 | web1storeview2     |
   |        4 | web1storeview3 |          2 |        2 | web1storeview3     |
   +----------+----------------+------------+----------+--------------------+
   ```

1. 새 공유 카탈로그를 만듭니다.
1. 가격 및 구조를 구성할 때는 2단계에서 생성한 스토어를 선택합니다.
1. 공유 카탈로그를 저장합니다.

<u>예상 결과</u>:

공유 카탈로그가 문제 없이 저장됩니다.

<u>실제 결과</u>:

공유 카탈로그를 저장할 수 없습니다. 다음 오류가 표시됩니다.
*요청한 스토어를 찾을 수 없습니다. 스토어를 확인하고 다시 시도하십시오.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)를 참조하십시오.
