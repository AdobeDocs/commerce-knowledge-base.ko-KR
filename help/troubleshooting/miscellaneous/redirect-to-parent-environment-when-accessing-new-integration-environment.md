---
title: 새 통합 환경에 액세스할 때 상위 환경으로 리디렉션
description: 이 문서에서는 새로 생성된 통합 환경에 액세스하려고 하면 대신 상위 환경으로 이동하기 위한 Adobe Commerce on cloud infrastructure 문제에 대한 문제 해결 지침을 제공합니다.
exl-id: d1d40c8d-d43c-442e-95c9-76f3cdcafb0e
feature: Cache, Integration, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# 새 통합 환경에 액세스할 때 상위 환경으로 리디렉션

이 문서에서는 새로 생성된 통합 환경에 액세스하려고 하면 대신 상위 환경으로 이동하기 위한 Adobe Commerce on cloud infrastructure 문제에 대한 문제 해결 지침을 제공합니다.

이 문제를 해결하려면 데이터베이스에서 base\_url 값을 수정하고 `UPDATE_URLS` 변수 값이 `true`(으)로 설정되어 있는지 확인해야 합니다. 자세한 내용은 아래 섹션에서 확인하십시오.

영향을 받는 버전 및 버전:

* 클라우드 인프라의 Adobe Commerce 2.X.X

## 문제

<u>재현 단계</u>:

1. 기존 통합 분기를 복제합니다.
1. 새 환경에 액세스하기 위한 URL을 클릭합니다.

<u>예상 결과</u>:

새로 생성된 환경에 도달합니다.

<u>실제 결과</u>:

상위 분기의 환경으로 리디렉션됩니다.

## 솔루션

이 문제를 해결하려면 사용자 지정 환경 데이터베이스에서 `base_url` 값(보안 및 비보안)을 수정하고 `.magento.env.yaml` 파일에서 `UPDATE_URL` 변수를 설정해야 합니다.

### 데이터베이스의 base\_url 값 수정

버전 2.2.0 이상을 사용하는 경우 수동으로 또는 Adobe Commerce CLI를 사용하여 데이터베이스 변경을 수행할 수 있습니다.

#### DB의 값을 수동으로 수정합니다.

1. 데이터베이스에 연결합니다.
1. 다음 명령을 실행합니다.

```sql
UPDATE core_config_data SET value = %your_new_environment_unsecure_url% WHERE path="web/unsecure/base_url"
```

```sql
update core_config_data set value = %your_new_environment_secure_url% where path="web/secure/base_url"
```

#### Adobe Commerce CLI를 사용하여 데이터베이스 수정(버전 2.2.X에서 사용 가능)

1. [Adobe Commerce 파일 시스템 소유자](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/web-server/apache.html)(으)로 로그인하거나 (으)로 전환합니다.
1. 다음 명령을 실행합니다.

```bash
php <your_magento_install_dir>/bin/magento config:set web/unsecure/base_url http://example.com
php <your_magento_install_dir>/bin/magento config:set web/secure/base_url https://example.com
```

### `UPDATE_URLS` 변수 설정

로컬 코드베이스에서 `.magento.env.yaml` 파일 집합:

```
 stage:
    deploy:
        UPDATE_URLS: true
```

### 구성 캐시 지우기

변경 사항을 적용하려면 다음 명령을 실행하여 구성 캐시를 정리합니다.

```bash
php <your_magento_install_dir>/bin/magento cache:clean config
```

## 개발자 설명서의 관련 문서:

[변수 배포](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html)
