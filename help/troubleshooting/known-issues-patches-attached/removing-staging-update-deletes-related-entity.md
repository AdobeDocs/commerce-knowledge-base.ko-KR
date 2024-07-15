---
title: 스테이징 업데이트를 제거하면 관련 엔터티가 삭제됩니다.
description: 이 문서에서는 엔티티(카테고리, CMS 페이지 등)와 관련된 알려진 Adobe Commerce 2.2.3 문제에 대한 패치를 제공합니다. 관련 일정 업데이트가 삭제되면 자체가 제거됩니다.
exl-id: 91138ac1-916e-4dd1-bad5-892524fdd9e1
feature: CMS, Cache, Categories, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# 스테이징 업데이트를 제거하면 관련 엔터티가 삭제됩니다.

이 문서에서는 엔티티(카테고리, CMS 페이지 등)와 관련된 알려진 Adobe Commerce 2.2.3 문제에 대한 패치를 제공합니다. 관련 일정 업데이트가 삭제되면 자체가 제거됩니다.

>[!NOTE]
>
>Adobe Commerce 2.2.6에서 문제가 해결되었습니다.

## 문제

시작 날짜와 종료 날짜 사이의 활성 일정 업데이트를 삭제하면 관련 엔터티(범주, 하위 범주, CMS 페이지)도 삭제됩니다.

<u>재현할 단계(범주 포함)</u>:

1. Commerce 관리자에 로그인합니다.
1. **카탈로그** > **범주**&#x200B;에서 새 하위 범주를 만듭니다.
1. 시작 및 종료 시간으로 새 스테이징 업데이트를 만듭니다.
1. 업데이트가 적용될 때까지 기다립니다. 즉, 시작 시간이 됩니다.
1. **보기/편집** 링크를 사용하여 업데이트를 삭제합니다.

<u>예상 결과</u>:

업데이트가 삭제되고 하위 범주가 여전히 관리자에 존재합니다.

<u>실제 결과</u>:

업데이트 및 하위 범주가 삭제됩니다.

## 솔루션

이 문서에 제공된 패치를 적용하고 실행 중인 캐시를 정리하십시오.

```bash
bin/magento
  cache:clean
```

## 패치

패치는 이 문서에 첨부되어 있습니다. 패치를 다운로드하려면 문서 끝까지 아래로 스크롤하여 파일 이름을 클릭하거나 해당 링크를 클릭합니다.

* [MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11059_EE_2.2.3_COMPOSER_v1.patch.zip)
* [MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch 다운로드](assets/MDVA-23505_EE_2.2.4_COMPOSER_v1.patch.zip)
* [MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch 다운로드](assets/MDVA-12158_EE_2.2.5_COMPOSER_v2.patch.zip)

### 호환 가능한 Adobe Commerce 버전:

패치는 다음에 대해 생성되었습니다.

* Adobe Commerce(모든 배포 방법) 2.2.3에 대해 MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch가 생성되었습니다.
* Adobe Commerce(모든 배포 방법) 2.2.4에 대해 MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch가 생성되었습니다.
* Adobe Commerce(모든 배포 방법) 2.2.5에 대해 MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch가 생성되었습니다.

MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch도 다음 Adobe Commerce 버전 및 버전과 호환(하지만 문제를 해결하지 못할 수 있음)됩니다.

* Adobe Commerce 온-프레미스 2.2.0-2.2.2
* 클라우드 인프라 2.2.0-2.2.3의 Adobe Commerce

MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch도 다음 Adobe Commerce 버전 및 버전과 호환(하지만 문제를 해결하지 못할 수 있음)됩니다.

* Adobe Commerce 온-프레미스 2.1.0-2.1.18, 2.2.0-2.2.3
* 클라우드 인프라 2.1.0-2.1.18, 2.2.0-2.2.3의 Adobe Commerce

MDVA-23505\_EE\_2.2.5\_COMPOSER\_v1.patch도 다음 Adobe Commerce 버전 및 버전과 호환(하지만 문제를 해결하지 못할 수 있음)됩니다.

* 클라우드 인프라의 Adobe Commerce 2.2.5

## 패치 적용 방법

지침은 [Adobe Commerce에서 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
