---
title: 패치를 적용하면 사이트가 다운됩니다.
description: 이 문서에서는 방금 적용한 패치가 사이트를 삭제하는 문제에 대해 설명합니다. 이 문제를 해결하려면 패치를 제거합니다.
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# 패치를 적용하면 사이트가 다운됩니다.

이 문서에서는 방금 적용한 패치가 사이트를 삭제하는 문제에 대해 설명합니다. 이 문제를 해결하려면 패치를 제거합니다.

## 영향을 받는 제품 및 버전

* Adobe Commerce(모든 배포 메서드), 지원되는 모든 버전
* Magento Open Source, 모든 버전

## 문제

패치를 적용하면 사이트가 다운됩니다.

## 원인

이 문제는 웹 사이트에 방금 적용한 패치, 사용자 정의, 이전에 적용한 다른 패치 또는 기타 오류 간의 버전 비호환성 때문에 나타날 수 있습니다.

## 솔루션

패치를 제거합니다. 패치 제거 방법은 Adobe Commerce on cloud infrastructure와 Adobe Commerce on-premise 및 Magento Open Source의 경우와 다릅니다.

### Magento Open Source, 모든 1.X 버전

Magento Open Source 1.X 버전의 경우,

* 다음 SSH 명령을 실행합니다. `h SUPEE_patch --revert `

### Adobe Commerce 온-프레미스, Magento Open Source, 모든 2.x 버전

Adobe Commerce 온-프레미스 및 Magento Open Source 2.x 버전의 경우,

1. 다음 SSH 명령을 실행합니다.

   ```
   patch -p1 -R %patch_name%.composer.patch
   ```

   (위 명령이 작동하지 않으면 `-p1` 대신 `-p2`을(를) 사용해 보십시오.)

1. 변경 내용을 반영하려면 **시스템** > **캐시 관리**&#x200B;에서 관리자의 캐시를 새로 고치십시오.

### 클라우드 인프라의 Adobe Commerce, 모든 버전

클라우드 인프라의 Adobe Commerce, 모든 버전

1. `m2-hotfixes` 디렉터리에서 `%patch_name%.composer.patch` 파일을 제거합니다.
1. 코드 변경 사항을 커밋하고 푸시합니다.

   ```
   git commit -m "Remove %patch_name%.composer.patch patch" && git push origin
   ```

## 관련 읽기

* 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).
