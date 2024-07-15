---
title: 고급 보고 cron 작업 오류 Adobe Commerce
description: 이 문서에서는 Adobe Commerce의 고급 보고 cron 작업 문제에 대한 패치를 제공합니다. 이 경우 고급 보고에 액세스하려는 고객에게 404 오류가 발생할 수 있습니다.
exl-id: c11a5faf-a243-411a-af0f-585a401e6e39
feature: Cache
role: Developer
source-git-commit: 6287e708c830680e04dd068b64cf63ca13ecdedb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# 고급 보고 cron 작업 오류 Adobe Commerce

이 문서에서는 Adobe Commerce의 고급 보고 cron 작업 문제에 대한 패치를 제공합니다. 이 경우 고급 보고에 액세스하려는 고객에게 404 오류가 발생할 수 있습니다.

## 영향을 받는 제품 및 버전

Adobe Commerce(모든 배포 옵션) 2.3.x

## 문제

고객이 고급 보고에 액세스하려고 할 때 `analytics_collect_data job`에 연결된 로그에 오류가 있으면 404 오류가 발생합니다.

## 호환 Magento 버전:

패치는 다음 Adobe Commerce 버전 및 버전과 호환되지만 문제를 해결할 수 없습니다.

* [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip): Adobe Commerce(모든 배포 옵션) 2.3.1-2.3.4-p2
* [MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce(모든 배포 옵션) 2.3.0
* [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce(모든 배포 옵션) 2.3.0

## **솔루션**

이 문제를 해결하려면 이 문서에 첨부된 관련 패치를 적용하십시오. 다운로드하려면 다음 링크를 클릭하십시오.

* [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip) 다운로드
* [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch 다운로드](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip)
* [MDVA-18980\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip) 다운로드

사용할 패치를 확인하려면:

<ol><li>다음 명령을 사용하여 로그를 검토하십시오.<code>grep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz</code>
</li><li>표시되는 오류에 따라 다음 표의 정보를 사용하여 패치를 선택합니다.<table style="width: 826px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center">
<p>오류</p>
</td>
<td class="wysiwyg-text-align-center">패치</td>
</tr>
<tr>
<td>
<pre>report.CRITICAL: cron 작업 {"exception":"[object] (RuntimeException(code:
  0): /srv/public_html/vendor/magento/module-cron/Observer/ProcessCronQueueObserver.php:327에서 cron 작업을 실행할 때 오류 발생,
  TypeError(코드: 0): substr_count()에는 매개 변수 1이 문자열이어야 하고 null이 주어져야 합니다.
  at /srv/public_html/vendor/magento/module-page-builder-analytics/Model/ContentTypeUsageReportProvider.php:106)"}
  []</pre>또는<pre>report.ERROR: Cron Job analytics_collect_data에 오류 발생: substr_count()가 예상함
  문자열 매개 변수 1을 반환합니다. null이 제공됩니다. 통계: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384}
  [] []</pre>
<p> </p>
</td>
<td><a href="assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch">MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip</a>을 적용하고 캐시를 지운 후 작업이 다시 실행될 때까지 24시간 기다린 후 다시 시도하십시오.</td>
</tr>
<tr>
<td>
<p><em>/tmp/analytics/tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/./tmp/../tmp/./tmp/../tmp/./tmp/./tmp/./tmp/../tmp/../ 파일을 열지 못했습니다.</em></p>
</td>
<td><a href="assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch">MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip</a>을 적용하고 캐시를 지운 후 작업이 다시 실행될 때까지 24시간 기다린 후 다시 시도하십시오.</td>
</tr>
<tr>
<td><em>암호가 잘못되었습니다.</em></td>
<td><a href="assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch">MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip</a>을 적용하고 캐시를 지운 후 작업이 다시 실행될 때까지 24시간 기다린 후 다시 시도하십시오.</td>
</tr>
</tbody>
</table>
</li></ol>

## 패치 적용 방법

파일의 압축을 풀고 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)의 지침을 따릅니다.

## 관련 읽기

[파일을 삭제할 수 없습니다. 경고!unlink: 관리자의 파일 또는 디렉터리 오류가 없습니다.](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md)
