---
title: "ACSD-50858: 배너의 콘텐츠 로드 성능이 개선되었습니다."
description: ACSD-50858 패치를 적용하여 과도한 DB 쿼리 및 페이지 로드 시간 증가로 인해 장바구니/체크아웃 페이지에서 배너 성능이 영향을 받는 Adobe Commerce 문제를 해결합니다.
exl-id: f9526d66-fc0e-44a0-8c72-b9f183004840
feature: Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-50858: 배너의 콘텐츠 로드 성능이 개선되었습니다.

ACSD-50858 패치는 장바구니/체크아웃 페이지에서 배너 성능 문제를 수정합니다. *DB 쿼리 초과 및 페이지 로드 시간 증가*. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31이 설치되어 있을 때 사용할 수 있습니다. 패치 ID는 ACSD-50858입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.5-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.6

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

*과도한 DB 쿼리 및 페이지 로드 시간 증가*(으)로 인해 배너 성능이 장바구니/체크아웃 페이지에서 영향을 받습니다.

이는 배너의 콘텐츠를 로드하는 방식을 리팩터링하여 DB 쿼리 수를 99.99%, 페이지 로드 시간을 ~99% 단축함으로써 해결되었습니다.

<u>재현 단계</u>:

1. 관리자에 로그인하고 간단한 제품을 만듭니다.
1. 관리자 또는 프론트엔드에서 고객을 만들고 배송 주소를 추가합니다.
1. banners.php를 `magento_root/pub/` 폴더로 이동합니다.
1. `php pub/banners.php` 명령을 사용하여 배너를 생성합니다. 간편 배너 1만개, 판매 룰이 적용된 배너 1000개를 생성한다.
1. 이전에 프론트엔드에서 만든 고객에 로그인합니다.
1. 이전에 만든 제품을 장바구니에 추가합니다.
1. 체크아웃 페이지(체크아웃/장바구니)로 이동합니다.
1. `banner/ajax/load` 요청 로드 시간 모니터링:

   * `bin/magento dev:query-log:enable` 없이
   * `bin/magento dev:query-log:enable` 사용

     ```
     grep 'magento_banner_content' var/debug/db.log  | wc -l
     ```

<u>예상 결과</u>:

`magento_banner_content`에 대한 DB 쿼리 수 및 장바구니/체크아웃 페이지 로드 시간을 줄입니다.

<u>실제 결과</u>:

`magento_banner_content`에 대한 DB 쿼리 수 및 장바구니/체크아웃 페이지 로드 시간이 늘어났습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ko).

## 추가 정보

<u>banners.php 콘텐츠</u>:

```php
\Banner::class);
    $banner->setIsEnabled(
        \Magento\Banner\Model\Banner::STATUS_ENABLED
    )->setName(
        'Test Dynamic Block '.$i
    )->setTypes(
        ''
    )->setStoreContents(
        [0 => 'Dynamic Block Content '.$i]
    )->save();
}

$objectManager = \Magento\Framework\App\ObjectManager::getInstance();

/** @var \Magento\SalesRule\Model\Rule $salesRule */
$salesRule = $objectManager->create(\Magento\SalesRule\Model\Rule::class);
$salesRule->setData(
    [
        'name' => '50% Off ',
        'is_active' => 1,
        'customer_group_ids' => [\Magento\Customer\Model\GroupManagement::NOT_LOGGED_IN_ID],
        'coupon_type' => \Magento\SalesRule\Model\Rule::COUPON_TYPE_NO_COUPON,
        'conditions' => [
            [
                'type' => \Magento\SalesRule\Model\Rule\Condition\Address::class,
                'attribute' => 'base_subtotal',
                'operator' => '>',
                'value' => 0
            ]
        ],
        'simple_action' => 'by_percent',
        'discount_amount' => 50,
        'discount_step' => 0,
        'stop_rules_processing' => 1,
        'website_ids' => [
           1
        ]
    ]
);
$salesRule->save();

for ($i = 0; $i < 1000; $i++) {

    $banner = $objectManager->create(\Magento\Banner\Model\Banner::class);
    $banner->setData(
        [
            'name' => 'Get 50% Off ',
            'is_enabled' => \Magento\Banner\Model\Banner::STATUS_ENABLED,
            'types' => [], /*Any Banner Type*/
            'store_contents' => ['<img src="http://example.com/banner_40_percent_off.png" />'],
            'banner_sales_rules' => [$salesRule->getId()],
        ]
    );
    $banner->save();
}
```

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ko)을 참조하세요.
