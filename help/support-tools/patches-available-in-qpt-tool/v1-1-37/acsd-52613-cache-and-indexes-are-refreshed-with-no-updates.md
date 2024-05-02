---
title: 'ACSD-52613: 업데이트 없이 캐시 및 인덱스가 새로 고쳐짐'
description: ACSD-52613 패치를 적용하여 다음과 같이 'Inventory_source' 항목이 업데이트되지 않을 때 캐시와 색인이 새로 고쳐지는 Adobe Commerce 문제를 해결합니다. [!DNL REST API].
feature: REST
role: Admin
exl-id: 78f23fee-a48e-4ee2-bc75-e98e3dd1ac44
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-52613: 업데이트가 없어도 캐시 및 인덱스를 새로 고칩니다.

ACSD-52613 패치는에 대한 업데이트가 없을 때 캐시와 색인이 새로 고쳐지는 Adobe Commerce 문제를 해결합니다 `Inventory_source` 항목별 [!DNL REST API]. 이 패치는 다음 경우에 사용할 수 있습니다. [!DNL Quality Patches Tool (QPT)] 1.1.37이 설치되었습니다. 패치 ID는 ACSD-52613입니다. 이 문제는 Adobe Commerce 2.4.7에서 해결되었습니다.

## 영향을 받는 제품 및 버전

**패치는 Adobe Commerce 버전에 대해 만들어집니다.**

* Adobe Commerce(모든 배포 방법) 2.4.6

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.6 - 2.4.7

>[!NOTE]
>
>이 패치는 새 버전이 설치된 다른 버전에 적용할 수 있습니다 [!DNL Quality Patches Tool] 릴리스. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 최신 버전으로 패키지하고 [[!DNL Quality Patches Tool]: 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

에 대한 업데이트가 없으면 캐시 및 인덱스가 새로 고쳐집니다. `Inventory_source` 항목별 [!DNL REST API].

<u>전제 조건</u>:

설치된 인벤토리 모듈

<u>재현 단계</u>:

1. 다음과 같이 개발자 모드 전환 `debug.log`.
1. 100개의 제품 - import.csv로 가져오기 파일 준비:

   ```
   sku    name    product_type    attribute_set_code    price
   test_sku_1    test_sku_1    simple    Default    10
   test_sku_2    test_sku_2    simple    Default    10
   ...
   test_sku_100    test_sku_100    simple    Default    10
   ```

1. 에서 제품 가져오기 `import.csv`
1. (이)라는 이름의 새 주식과 소스 만들기 **test_stock** 및 **test_source**.
1. 웹 사이트에 신규 재고를 지정하고 재고에 출처를 지정합니다.
1. 모든 항목에 대한 액세스 권한을 가진 새 통합을 만들고 활성화한 다음 액세스 토큰을 복사하여 붙여넣습니다.
1. 다음으로 이동 **스토어** > **구성** > **서비스** > **Oauth** > **소비자 설정** 및 활성화 **OAuth 액세스 토큰을 독립 실행형 전달자 토큰으로 사용할 수 있도록 허용**.
1. 캐시를 플러시합니다.
1. 인덱서를 다음으로 설정 **일정별 업데이트됨**
1. API 요청 실행

   `POST ../rest/V1/inventory/source-items`

   본문으로 사용

   ```
   {
    "sourceItems": [
        {
            "sku": "test_sku_1",
            "source_code": "test_source",
            "quantity": 24,
            "status": 1
        },
        {
            "sku": "test_sku_2",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_3",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_4",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_5",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_6",
            "source_code": "test_source",
            "quantity": 19,
            "status": 1
        },
        {
            "sku": "test_sku_7",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_8",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_9",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_10",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_11",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_12",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_13",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_14",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_15",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_16",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_17",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_18",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_19",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_20",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_21",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_22",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_23",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_24",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_25",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_26",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_27",
            "source_code": "test_source",
            "quantity": 13,
            "status": 1
        },
        {
            "sku": "test_sku_28",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_29",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_30",
            "source_code": "test_source",
            "quantity": 1,
            "status": 1
        },
        {
            "sku": "test_sku_31",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_32",
            "source_code": "test_source",
            "quantity": 1,
            "status": 1
        },
        {
            "sku": "test_sku_33",
            "source_code": "test_source",
            "quantity": 49,
            "status": 1
        },
        {
            "sku": "test_sku_34",
            "source_code": "test_source",
            "quantity": 12,
            "status": 1
        },
        {
            "sku": "test_sku_35",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_36",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_37",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_38",
            "source_code": "test_source",
            "quantity": 10,
            "status": 1
        },
        {
            "sku": "test_sku_39",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_40",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_41",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_42",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_43",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_44",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_45",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_46",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_47",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_48",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_49",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_50",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_51",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_52",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_53",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_54",
            "source_code": "test_source",
            "quantity": 1,
            "status": 1
        },
        {
            "sku": "test_sku_55",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_56",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_57",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_58",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_59",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_60",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_61",
            "source_code": "test_source",
            "quantity": 16,
            "status": 1
        },
        {
            "sku": "test_sku_62",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_63",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_64",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_65",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_66",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_67",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_68",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_69",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_70",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_71",
            "source_code": "test_source",
            "quantity": 16,
            "status": 1
        },
        {
            "sku": "test_sku_72",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_73",
            "source_code": "test_source",
            "quantity": 3,
            "status": 1
        },
        {
            "sku": "test_sku_74",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_75",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_76",
            "source_code": "test_source",
            "quantity": 50,
            "status": 1
        },
        {
            "sku": "test_sku_77",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_78",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_79",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_80",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_81",
            "source_code": "test_source",
            "quantity": 2,
            "status": 1
        },
        {
            "sku": "test_sku_82",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_83",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_84",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_85",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_86",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_87",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_88",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_89",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_90",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_91",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_92",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_93",
            "source_code": "test_source",
            "quantity": 4,
            "status": 1
        },
        {
            "sku": "test_sku_94",
            "source_code": "test_source",
            "quantity": 3,
            "status": 1
        },
        {
            "sku": "test_sku_95",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_96",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_97",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_98",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_99",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        },
        {
            "sku": "test_sku_100",
            "source_code": "test_source",
            "quantity": 0,
            "status": 0
        }
    ]
   }
   ```

1. 에서 모든 로그 제거 `var/log`
1. 실행 [!DNL REST API] 다시 요청하십시오.
1. 다음 확인: `var/log/debug.log`.

<u>예상 결과</u>:

아무것도 변경되지 않았으므로 캐시를 정리하고 두 번째 실행 후에는 색인을 실행하지 말아야 합니다.

<u>실제 결과</u>:

다음 `var/log/debug.log` 캐시 지우기와 관련된 항목을 포함합니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [[!DNL Quality Patches Tool] > 사용](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
* 클라우드 인프라의 Adobe Commerce: [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Commerce on Cloud Infrastructure 안내서에서 참조하십시오.

## 관련 읽기

에 대해 자세히 알아보기 [!DNL Quality Patches Tool]을(를) 참조하시기 바랍니다.

* [[!DNL Quality Patches Tool] 출시됨: 품질 패치를 셀프서비스할 수 있는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 을 참조하십시오.
* [다음을 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 을 참조하십시오.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 다음을 참조하십시오. [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 다음에서 [!DNL Quality Patches Tool] 가이드.
