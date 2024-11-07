---
title: 'MDVA-40550: 리인덱싱 후 프런트 엔드에 제품이 누락됨'
description: MDVA-40550 패치는 리인덱싱이 상점 카테고리 중 일부 또는 전부에 제품이 누락되는 문제를 해결합니다. 이 패치는 [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6이 설치된 경우 사용할 수 있습니다. 패치 ID는 MDVA-40550입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.
exl-id: 0aca6eb2-6eb2-4ac4-8ae1-052f671c14e5
feature: Categories, Console, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40550: 리인덱싱 후 프런트 엔드에 제품이 누락되었습니다.

MDVA-40550 패치는 리인덱싱이 상점 카테고리 중 일부 또는 전부에 제품이 누락되는 문제를 해결합니다. 이 패치는 [품질 패치 도구(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6이 설치된 경우에 사용할 수 있습니다. 패치 ID는 MDVA-40550입니다. 이 문제는 Adobe Commerce 2.4.4에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.2-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>이 패치는 새로운 품질 패치 도구 릴리스가 있는 다른 버전에 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

<u>재현 단계</u>:

1. 제품을 만듭니다.
1. 인덱서를 **일정별 업데이트**(으)로 전환합니다.
   * 제품을 범주에 할당합니다.
1. xdebug를 사용하도록 설정하고 `\Magento\Indexer\Model\Indexer::reindexAll` 및 `\Magento\Indexer\Model\IndexMutex::execute`에서 xdebug 중단점을 만듭니다.
1. 다음 명령을 사용하여 `catalog_category_product`의 **전체 인덱스**&#x200B;을(를) 실행합니다.

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * 중단점 `\Magento\Indexer\Model\Indexer::reindexAll`에서 실행이 중지될 때까지 기다립니다.

1. 다른 콘솔에서 다음 명령을 사용하여 **부분 인덱스**&#x200B;를 동시에 실행합니다.

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 중단점 `\Magento\Indexer\Model\IndexMutex::execute`에서 실행이 중지될 때까지 기다립니다. `catalog_category_product` 인덱서를 잠급니다.
1. `catalog_category_product`의 전체 리인덱스 실행을 다시 시작하고 잠금 제한 시간(60초)을 기다립니다.

<u>예상 결과</u>:

콘솔에 오류 메시지가 없습니다.

<u>실제 결과</u>:

다음 오류가 발생합니다.

*색인: catalog_category_product에 대한 잠금을 가져올 수 없습니다.*

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* 개발자 설명서에서 Adobe Commerce 또는 Magento Open Source 온-프레미스: [소프트웨어 업데이트 안내서 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
* 클라우드 인프라의 Adobe Commerce: 개발자 설명서에서 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## 관련 읽기

품질 패치 도구에 대한 자세한 내용은 다음을 참조하십시오.

* [품질 패치 도구 릴리스: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* 지원 기술 자료에서 [품질 패치 도구를 사용하여 Adobe Commerce 문제에 패치를 사용할 수 있는지 확인](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 개발자 설명서에서 [QPT에서 사용할 수 있는 패치](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)를 참조하십시오.
