---
title: 더 이상 사용되지 않는 Google 이미지 차트를 이미지 차트로 바꾸기
description: 현재 대부분의 Adobe Commerce 에디션 및 버전은 [Google 이미지 차트](https://developers.google.com/chart/image/)를 사용하여 관리 대시보드에서 정적 차트를 렌더링합니다. 2019년 3월 14일부터 Google은 Google 이미지 차트 지원을 중단할 예정입니다. 이 문제를 해결하기 위해 Google 이미지 차트를 [Image-Charts](https://www.image-charts.com/) 무료 서비스로 바꾸는 패치를 제공합니다.
exl-id: f86f0bb9-8a03-471d-8696-1eba4b8acbd1
feature: Cache, Compliance
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# 더 이상 사용되지 않는 Google 이미지 차트를 이미지 차트로 바꾸기

대부분의 Adobe Commerce 버전 및 버전은 현재 [Google 이미지 차트](https://developers.google.com/chart/image/)를 사용하여 관리 대시보드에서 정적 차트를 렌더링합니다. 2019년 3월 14일부터 Google은 Google 이미지 차트 지원을 중단할 예정입니다. 이 문제를 해결하기 위해 Google 이미지 차트를 [이미지 차트](https://www.image-charts.com/) 무료 서비스로 바꾸는 패치를 제공하고 있습니다.

## 영향을 받는 버전

* Adobe Commerce 1.X, 모든 에디션
* Adobe Commerce 2.X, 모든 에디션

>[!NOTE]
>
>Adobe Commerce 온-프레미스 1.14.4.1, Magento Open Source 1.9.4.1, Adobe Commerce 온-프레미스 및 Adobe Commerce on cloud infrastructure 2.3.2에는 이 차트 업데이트가 포함될 예정입니다. 이러한 버전으로 업그레이드하면 추가 패치 없이 이미지 차트를 계속 지원할 수 있습니다.

## 문제

Google은 2019년 3월 14일에 Google 이미지 차트 지원을 중단했습니다. Adobe Commerce 1.X 및 Adobe Commerce 2.2.X 모든 버전 사용자는 패치를 다운로드하여 적용하지 않으면 Google 이미지 차트를 이미지 차트 솔루션으로 바꿀 수 없습니다. 표시된 차트는 [GDPR](https://www.image-charts.com/data-processing-addendum.html) 준수 개인정보 처리방침이 있는 이미지 차트 무료 계정 서비스를 통해 Google 이미지 차트의 디자인과 기능이 동일합니다. 추가 옵션은 [이미지 차트](https://www.image-charts.com/)를 참조하십시오.

## 솔루션

Commerce 관리에서 정적 차트를 볼 수 있도록 Adobe Commerce에서 제공하는 패치를 다운로드하여 적용합니다. 추가적인 구성은 필요하지 않습니다.

### Adobe Commerce 온-프레미스

1. [연결된 MAGETWO-98833\_composer\_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch.zip) 패치를 저장하고 Adobe Commerce 루트 디렉터리에 업로드합니다.
1. 패치 이름을 실제 이름으로 대체하고 다음 SSH 명령을 실행합니다.

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch
   ```

   위의 명령이 작동하지 않으면 `-p1` 대신 `-p2`을(를) 사용해 보십시오.)

1. 변경 내용을 반영하려면 **시스템** > **캐시 관리**&#x200B;에서 관리자의 캐시를 새로 고치십시오.

### 클라우드 인프라의 Adobe Commerce

클라우드 판매자의 경우 해당 패치가 가장 가까운 ECE 도구 업데이트에 포함됩니다.

### Magento 2 Source 열기

1. [https://magento.com/tech-resources/download\#download2291](https://magento.com/tech-resources/download#download2291)(으)로 이동
1. **형식 선택** 드롭다운 목록에서 작성기 버전을 선택하고 **다운로드**&#x200B;를 클릭합니다.
1. Adobe Commerce 루트 디렉토리에 패치를 업로드합니다.
1. 패치 이름을 실제 이름으로 대체하고 다음 SSH 명령을 실행합니다.

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-37-48.patch
   ```

   (위의 명령이 작동하지 않으면 `-p1` 대신 `-p2`을(를) 사용해 보십시오.)

1. 변경 내용을 반영하려면 **시스템** > **캐시 관리**&#x200B;에서 관리자의 캐시를 새로 고치십시오.

### Adobe Commerce 1 온-프레미스

다음 단계에 따라 패치를 다운로드하여 적용합니다.

1. [첨부된 MPERF-10509-EE-2019-03-13-06-32-19.diff](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff.zip) 패치를 저장하고 Adobe Commerce 루트 디렉터리에 업로드합니다.
1. 다음 SSH 명령을 실행합니다.

   ```git
   patch -p1 < MPERF-10509-EE-2019-03-13-06-32-19.diff
   ```

   (위의 명령이 작동하지 않으면 `-p1` 대신 `-p2`을(를) 사용해 보십시오.)

1. 변경 내용을 반영하려면 **시스템** > **캐시 관리**&#x200B;에서 관리자의 캐시를 새로 고치십시오.

### Magento 1 Source 열기

다음 단계에 따라 패치를 다운로드하여 적용합니다.

1. [**이 링크**](https://magento.com/tech-resources/download#download2283)를 클릭하여 관리 대시보드 차트 패치를 찾습니다.
1. 선택

   ```git
   MPERF-10509.diff
   ```

   **포맷을 선택** 드롭다운에서 다운로드를 클릭합니다.

1. 파일을 Adobe Commerce 루트 디렉토리에 업로드합니다.
1. 다음 SSH 명령을 실행합니다.

   ```git
   patch -p1 < MPERF-10509.diff
   ```

   (위의 명령이 작동하지 않으면 `-p1` 대신 `-p2`을(를) 사용해 보십시오.)

1. 변경 내용을 반영하려면 **시스템** > **캐시 관리**&#x200B;에서 관리자의 캐시를 새로 고치십시오.

## 첨부 파일

[MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch 다운로드](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch)

[MPERF-10509-EE-2019-03-13-06-32-19.diff 다운로드](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff)
