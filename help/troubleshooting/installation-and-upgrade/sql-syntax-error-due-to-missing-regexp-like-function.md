---
title: REGEXP_LIKE 함수 누락으로 인해 B2B 1.5.2로 업그레이드하지 못하고 SQL 구문 오류가 발생합니다
description: 이 문서에서는 company_structure 테이블을 업데이트하려고 할 때 누락된 REGEXP_LIKE 함수로 인해 SQL 구문 오류가 발생하는 문제에 대한 핫픽스를 제공합니다.
feature: B2B, Upgrade
role: Admin, Developer
source-git-commit: ec1f0e06c0f2a59d4b78eba69bf02798e6bf66f3
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# REGEXP_LIKE 함수 누락으로 인해 B2B 1.5.2로 업그레이드하지 못하고 SQL 구문 오류가 발생합니다

이 문서에서는 `company_structure` 테이블을 업데이트하려고 할 때 `REGEXP_LIKE` 함수가 누락되어 발생하는 SQL 구문 오류에 대한 핫픽스를 제공합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 방법) 2.4.6-px + B2B 1.5.2([!DNL MariaDB] 10.6 사용)
* Adobe Commerce(모든 배포 방법) 2.4.7-px + B2B 1.5.2([!DNL MariaDB] 10.6 사용)

## 문제

`company_structure` 테이블을 업데이트하려고 할 때 `REGEXP_LIKE` 함수가 누락되어 B2B 버전 1.5.2로 업그레이드하지 못했습니다. SQL 구문 오류가 발생했습니다.

<u>필수 구성 요소</u>:

* MariaDB 10.6
* Adobe Commerce 2.4.6x 또는 2.4.7x
* B2B 버전 1.5.0 또는 1.5.1

<u>재현 단계</u>:

1. 회사를 모회사에 할당하여 회사 계층을 설정합니다. 자세한 내용은 Adobe Commerce B2B 안내서의 [회사 계층 관리](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/company-management/manage-company-hierarchy)를 참조하십시오.
1. B2B를 1.5.2 버전으로 업그레이드하십시오.

<u>예상 결과</u>:

업그레이드가 성공적으로 완료되었습니다.

<u>실제 결과</u>:

다음 오류로 인해 `bin/magento setup:upgrade`이(가) 실패합니다.

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^123(/.+)?$'))
```

## 솔루션

문제를 해결하려면 다음 단계를 수행하십시오.

1. B2B 모듈을 1.5.2 버전으로 업데이트:

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. 첨부된 [ACSD-65540_B2B_1.5.2.zip](assets/ACSD-65540_B2B_1.5.2.zip) 패치를 적용합니다. 자세한 내용은 지원 기술 자료에서 [Adobe에서 제공하는 작성기 패치 적용 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.
1. `bin/magento setup:upgrade` 실행.

### 클라우드 패치를 사용하여 패치 적용

클라우드 인프라의 Adobe Commerce에 대해 아래 단계를 수행합니다.

1. `cloud-patches` 모듈의 버전을 1.1.5로 업데이트:

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer updatemagento/magento-cloud-patches
   ```

1. 변경 사항을 커밋하고 푸시하여 재배포를 시작합니다. 지침은 Adobe Commerce on Cloud 안내서의 [패치 적용](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)을 참조하십시오.
