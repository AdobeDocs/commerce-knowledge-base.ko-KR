---
title: 404 카탈로그 가격 규칙 일정 업데이트가 수행되면 스토어 프런트에 오류 발생
description: 이 문서에서는 카탈로그 가격 규칙 업데이트를 만든 후 시작 시간을 나중에 편집한 후 모든 스토어 전면 페이지에서 404 오류를 가져오는 것과 관련된 알려진 Adobe Commerce 2.2.1 문제를 해결하는 데 필요한 단계 및 패치를 제공합니다. 이 문제를 해결하려면 패치를 적용해야 합니다.
exl-id: 7ea148a5-56cb-479a-8b2f-fae8b3bd4b22
feature: Cache, Catalog Management, Marketing Tools, Orders, Price Rules
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# 404 카탈로그 가격 규칙 일정 업데이트가 수행되면 스토어 프런트에 오류 발생

이 문서에서는 카탈로그 가격 규칙 업데이트를 만든 후 시작 시간을 나중에 편집한 후 모든 스토어 전면 페이지에서 404 오류를 가져오는 것과 관련된 알려진 Adobe Commerce 2.2.1 문제를 해결하는 데 필요한 단계 및 패치를 제공합니다. 이 문제를 해결하려면 패치를 적용해야 합니다.

## 문제

Storefront 페이지를 사용할 수 없게 되어 404 오류가 반환됩니다. 이 문제는 활성 카탈로그 가격 규칙 업데이트 기한이 지난 후에 나타나며, 이 업데이트의 시작 날짜가 초기 생성 후에 편집되었습니다.

<u>재현 단계</u>:

1. Commerce 관리자의 **마케팅** > **프로모션** > **카탈로그 가격 규칙**&#x200B;에서 새 카탈로그 가격 규칙을 만듭니다.
1. **카탈로그 가격 규칙** 그리드에서 **편집,** 새 업데이트 일정을 클릭하고 **상태**&#x200B;를 *활성*(으)로 설정합니다.
1. **컨텐츠** > **컨텐츠 스테이징** > **대시보드**&#x200B;로 이동합니다.
1. 최근에 만든 업데이트를 선택하고 시작 시간을 변경합니다.
1. 변경 사항을 저장합니다.

<u>예상 결과</u>:

업데이트 시작 일자가 발효되면 카탈로그 가격 규칙이 성공적으로 적용됩니다.

<u>실제 결과</u>:

업데이트 시작 날짜가 발효되면 404 오류를 반환하는 상점 내 모든 카탈로그 및 제품을 사용할 수 없게 됩니다.

## 솔루션

카탈로그 페이지를 복원하고 카탈로그 가격 규칙 업데이트 기능을 완전히 사용하려면 패치를 설치하고 수동으로 및 관리자에서 규칙을 삭제하고 데이터베이스의 잘못된 링크를 수정해야 합니다. 카탈로그 가격 규칙도 다시 만들어야 합니다.

다음은 필수 단계에 대한 자세한 설명입니다.

1. [패치 적용](#patch).
1. Commerce 관리에서 문제(시작 시간이 업데이트된 경우)와 관련된 카탈로그 가격 규칙을 삭제합니다. 이렇게 하려면 **마케팅** > **프로모션** > **카탈로그 가격 규칙**&#x200B;에서 규칙 페이지를 열고 **규칙 삭제**&#x200B;를 클릭하십시오.
1. 데이터베이스에 액세스하면 `catalogrule` 테이블에서 관련 레코드가 수동으로 삭제됩니다.
1. 데이터베이스에서 잘못된 링크를 수정합니다. 자세한 내용은 [관련 단락](#fix_links)을 참조하세요.
1. **마케팅**&#x200B;의 Commerce 관리에서 **프로모션** > **카탈로그 가격 규칙**(으)로 이동하여 필요한 구성으로 새 규칙을 만듭니다.
1. **시스템** > **캐시 관리**&#x200B;에서 브라우저 캐시를 지웁니다.
1. cron 작업이 올바르게 구성되어 있고 성공적으로 실행되었는지 확인하십시오.

## 패치 {#patch}

패치가 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 스크롤하여 파일 이름을 클릭하거나 다음 링크를 클릭합니다.

[MDVA-7392\_EE\_2.2.1\_COMPOSER\_v2.patch 다운로드](assets/MDVA-7392_EE_2.2.1_COMPOSER_v2.patch.zip)

## 호환 가능한 Adobe Commerce 버전:

다음에 대한 패치를 만들었습니다.

* Adobe Commerce 2.2.1

이 패치는 다음 Adobe Commerce 버전 및 에디션과도 호환됩니다(그러나 문제를 해결하지는 못할 수 있음).

* 클라우드 인프라 2.2.0의 Adobe Commerce - 2.2.4
* Adobe Commerce 온-프레미스 2.2.0 및 2.2.2 - 2.2.4

## 패치 적용 방법

지침은 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## DB의 스테이징에 대한 잘못된 링크 수정 {#fix_links}

>[!WARNING]
>
>데이터베이스를 조작하기 전에 데이터베이스 백업을 만드는 것이 좋습니다. 또한 개발 환경에서 쿼리를 먼저 테스트하는 것이 좋습니다.

`staging_update` 테이블에 대한 링크가 잘못된 행을 수정하려면 다음 단계를 따르십시오.

1. `flag` 테이블에 `staging_update` 테이블에 대한 잘못된 링크가 있는지 확인하십시오. 이는 `flag_code=staging`에 있는 레코드입니다.
1. 다음 쿼리를 사용하여 `flag` 테이블에서 잘못된 버전을 식별합니다.

   ```sql
   SELECT flag_data FROM flag WHERE flag_code = 'staging';
   ```

1. `staging_update` 테이블에서 현재(잘못된) 버전보다 낮은 기존 버전을 선택하고 두 숫자인 버전 값을 다시 가져옵니다. 이전 버전이 적용 가능한 `staging_update` 테이블의 최대 버전이고 다시 적용해야 하는 상황을 방지하기 위해 이전 버전이 아닌 버전을 사용합니다.

   ```sql
   SELECT id FROM staging_update WHERE id < %current_id% ORDER BY id DESC LIMIT 1, 1
   ```

   응답에서 받은 버전은 올바른 버전 `id`입니다.

1. `flag` 테이블에 잘못된 링크가 있는 행의 경우 `flag_data` 값을 올바른 버전 ID를 포함할 데이터로 설정하십시오. 이렇게 하면 색인 재지정 단계에서 성능을 절약할 수 있으며 모든 엔티티를 색인화하지 않아도 됩니다.

   ```sql
   UPDATE flag SET flag_data=REPLACE(flag_data, '%invalid_id%', '%new_valid_id%') WHERE flag_code='staging';
   ```

<u>예:</u>

```sql
SELECT flag_data FROM flag WHERE flag_code = 'staging'; <code class="language-bash">Response < 2.2 version</code>
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| a:1:{s:15:"current_version";s:10:"1490005140";} |
```

```bash
+-------------------------------------------------+
```

```bash
Response from 2.2 version
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| {"current_version":"1490005140"} |
```

```bash
+-------------------------------------------------+
```

```sql
SELECT id FROM staging_update WHERE id < 1490005140 <code class="language-sql">ORDER BY id DESC LIMIT 1, 1</code>;
```

```bash
Response:
```

```bash
1490005138
```

```sql
UPDATE flag SET flag_data=REPLACE(flag_data, '1490005140', '1490005138') WHERE flag_code='staging';
```

## 첨부 파일
