---
title: 동일한 기간에 여러 cron 작업이 예약되었습니다.
description: 이 문서에서는 특정 작업의 시간 변수를 Commerce 관리자에서 편집한 후 여러 cron 작업이 동시에 실행되도록 예약하는 것과 관련된 알려진 Adobe Commerce 2.2.2 문제에 대한 패치를 제공합니다.
exl-id: a3c1fe77-ed4c-43b5-8d6f-e5c549096c73
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# 동일한 기간에 여러 cron 작업이 예약되었습니다.

이 문서에서는 특정 작업의 시간 변수를 Commerce 관리자에서 편집한 후 여러 cron 작업이 동시에 실행되도록 예약하는 것과 관련된 알려진 Adobe Commerce 2.2.2 문제에 대한 패치를 제공합니다.

## 문제

cron이 매 분마다 실행되도록 구성된 경우 Admin에서 예약된 세 작업의 시간 변수를 편집하면 `cron_schedule` 데이터베이스 테이블에 동시에 실행되도록 예약된 여러 작업의 그룹이 표시됩니다.

<u>재현 단계</u>:

1. Commerce 관리에서 **스토어** > 설정 > **구성** > **고급** > **시스템** > **Cron(예약된 작업)** > **그룹에 대한 Cron 구성 옵션: 기본값.**
1. 다음 옵션을 구성합니다.
   * **기록 정리 간격**: **시스템 사용** 확인란의 선택을 취소하고 *1440*(으)로 설정합니다.
   * **성공 기록 수명**: **시스템 사용** 확인란을 지우고 *1440*(으)로 설정합니다.
   * **실패 기록 수명**: **시스템 사용** 확인란을 지우고 *1440*(으)로 설정합니다.

1. **구성 저장**&#x200B;을 클릭합니다.
1. SSH에서 `crontab -e` 명령을 실행합니다.
1. cron을 1분마다 실행되도록 설정합니다.
1. 터미널 탭/창을 세 개 엽니다.
1. 각 터미널 창의 Adobe Commerce `root/base/project` 디렉터리로 이동합니다.
1. 각 탭/창에서 다음 명령을 실행합니다.

   ```bash
   bin/magento cache:flush && bin/magento cron:run && bin/magento cache:flush && bin/magento cron:run
   ```

1. MySQL로 이동하여 다음 쿼리를 실행합니다.

   ```sql
   SELECT job_code, scheduled_at, count as count FROM cron_schedule GROUP BY job_code, scheduled_at HAVING count > 1 ORDER BY scheduled_at;
   ```

1. 동시에 실행되도록 예약된 작업 그룹을 참조하십시오.

<u>예상 결과</u>: 특정 기간에 하나의 cron `job_code`을(를) 예약해야 합니다.

<u>실제 결과</u>: 같은 기간에 예약된 cron 작업이 여러 개 있습니다.

## 솔루션

클라우드 인프라 판매자의 Adobe Commerce의 경우 [ECE 도구를 업데이트](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html)하면 문제가 해결됩니다.

Adobe Commerce 온-프레미스 가맹점은 첨부된 패치 중 하나를 적용해 문제를 해결해야 합니다.

## 패치

패치는 이 문서에 첨부되어 있습니다. 다운로드하려면 문서 끝까지 아래로 스크롤하여 파일 이름을 클릭하거나 다음 링크 중 하나를 클릭합니다.

* [MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip)
* [MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip)
* [MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* [MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip)
* [MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip)
* [MDVA-11304\_EE\_2.2.2\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip)
* [MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip)

### 호환 가능한 Adobe Commerce 버전

패치는 패치 파일 이름에 언급된 특정 버전에 대해 생성되었습니다. 예를 들어, MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch는 Adobe Commerce 2.2.4용으로 만들어졌으며 이 버전에 사용할 수 있는 가장 좋은 패치입니다.

패치는 다음 버전과도 호환됩니다.

* Adobe Commerce 온-프레미스 2.1.0-2.1.4의 경우: [MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip) 이 패치는 다음 Adobe Commerce 버전 및 버전과 호환되지만 문제를 해결할 수는 없습니다.
   * 클라우드 인프라 2.1.0-2.1.4의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.1.5-2.1.12의 경우: [MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip) 이 패치는 다음 Adobe Commerce 버전 및 버전과 호환되지만 문제를 해결할 수는 없습니다.
   * 클라우드 인프라의 Adobe Commerce 2.1.5-2.1.12
* 클라우드 인프라 2.1.13의 Adobe Commerce: [MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* Adobe Commerce 온-프레미스 2.1.14-2.1.17의 경우: [MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip) 이 패치는 다음 Adobe Commerce 버전 및 버전과 호환되지만 문제를 해결할 수는 없습니다.
   * Adobe Commerce 온-프레미스 2.1.18
   * 클라우드 인프라의 Adobe Commerce 2.1.14-2.1.18
* Adobe Commerce 온-프레미스 2.2.0-2.2.1의 경우: [MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip) 이 패치는 다음 Adobe Commerce 버전 및 버전과 호환되지만 문제를 해결할 수는 없습니다.
   * 클라우드 인프라 2.2.0-2.2.1의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.2.0-2.2.3의 경우: [MDVA-11304\_EE\_2.2.2\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip) 이 패치는 다음 Adobe Commerce 버전 및 버전과 호환되지만 문제를 해결할 수는 없습니다.
   * 클라우드 인프라 2.2.0-2.2.3의 Adobe Commerce
* Adobe Commerce 온-프레미스 2.2.4의 경우: [MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch 다운로드](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip) 이 패치는 다음 Adobe Commerce 버전 및 버전과 호환되지만 문제를 해결할 수는 없습니다.
   * 클라우드 인프라의 Adobe Commerce 2.2.4

## 패치 적용 방법

지침은 지원 기술 자료의 [Adobe Commerce에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)을 참조하십시오.

## 첨부 파일
