---
title: B2B 1.5.2 업데이트 후 Magento_Company 모듈 업그레이드의 성능 문제
description: 이 문서에서는 B2B 1.5.2 업데이트 후 Magento_Company 모듈 업그레이드의 성능 문제에 대한 핫픽스를 제공하여 company_structure 테이블의 대규모 데이터 세트에 대해 지나치게 긴 처리 시간을 해결합니다.
feature: B2B, Upgrade
role: Admin, Developer
source-git-commit: d06f0045b4c4c1615bd3abec963eb17fdee93860
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# B2B 1.5.2 업데이트 후 Magento_Company 모듈 업그레이드의 성능 문제

이 문서에서는 B2B 1.5.2 업데이트 후 `Magento_Company` 모듈 업그레이드의 성능 문제에 대한 핫픽스를 제공하여 `company_structure` 테이블의 대규모 데이터 세트(~10만 개 이상의 레코드)에 대해 너무 긴 처리 시간을 해결합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 방법) 2.4.6-px + B2B 1.5.2
* Adobe Commerce(모든 배포 방법) 2.4.7-px + B2B 1.5.2
* Adobe Commerce(모든 배포 방법) 2.4.8 + B2B 1.5.2

## 문제

B2B 1.5.2로 업데이트한 후 `Magento_Company` 모듈을 업그레이드하면 `company_structure` 테이블에서 많은 레코드(~100,000+)를 처리하는 데 시간이 너무 오래 걸립니다.

<u>필수 구성 요소</u>:

* ACSD-65540_B2B_1.5.2.patch를 설치해야 합니다.
* Adobe Commerce 2.4.6 - 2.4.8
* ACSD-65540 패치가 적용된 B2B 버전 1.5.0, 1.5.1 또는 B2B 1.5.2

<u>재현 단계</u>:

1. 회사를 모회사에 할당하여 회사 계층을 설정합니다. 자세한 내용은 Adobe Commerce B2B 안내서의 [회사 계층 관리](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/company-management/manage-company-hierarchy)를 참조하십시오.
1. B2B를 1.5.2 버전으로 업그레이드하십시오.

<u>예상 결과</u>:

업그레이드가 성공적으로 완료되었습니다.

<u>실제 결과</u>:

`company_structure` 테이블에 많은 레코드가 있는 경우 `Magento_Company` 모듈 업그레이드를 완료하는 데 시간이 오래 걸립니다.

## 솔루션

문제를 해결하려면 다음 단계를 수행하십시오.

1. B2B 모듈을 1.5.2 버전으로 업데이트:

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. [ACSD-65540_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2.zip)를 적용합니다.

1. 첨부된 [ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch를 적용합니다](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip).
1. 패치를 적용한 후 `bin/magento setup:upgrade`을(를) 실행합니다.

### 패치 적용 방법

파일의 압축을 풀고 지침이 필요하면 지원 기술 자료에서 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)을 참조하십시오.

### 클라우드 패치를 사용하여 패치 적용

Adobe Commerce on Cloud 판매자의 경우 아래 단계를 따르십시오.

1. 클라우드 패치 모듈의 버전을 1.1.5로 업데이트하여 MCLOUD-13605으로 배포된 ACSD-65540_B2B_1.5.2.패치를 설치합니다.

   >[!NOTE]
   >
   >패치가 이미 설치되어 있는지 확인하려면 다음을 실행합니다.
   > `./vendor/bin/magento-patches -n status | grep MCLOUD-13605`

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch를 `m2-hotfixes` 디렉터리에 추가합니다.
1. 변경 내용을 커밋하고 푸시하여 재배포 및 `bin/magento setup:upgrade`을(를) 시작합니다. 지침은 Adobe Commerce on Cloud 안내서의 [패치 적용](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)을 참조하십시오.

## 관련 읽기

* [REGEXP_LIKE 함수 누락으로 인해 SQL 구문 오류가 발생하여 B2B 1.5.2로 업그레이드할 수 없습니다](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/sql-syntax-error-due-to-missing-regexp-like-function)
