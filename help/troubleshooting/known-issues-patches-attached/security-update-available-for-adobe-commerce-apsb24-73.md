---
title: Adobe Commerce에 사용 가능한 보안 업데이트 - [!DNL APSB24-73]
promoted: true
description: Adobe Commerce 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11 및 이전 버전의 경우  [!DNL B2B] module만 실행하는 [!DNL critical, important, and moderate vulnerabilities] 에 격리된 패치를 적용합니다.
feature: Compliance, Security
role: Developer
source-git-commit: 181316dc0bd42feae0a857ff52edd80dbfd492ad
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Adobe Commerce에 사용 가능한 보안 업데이트 - [!DNL APSB24-73]

2024년 10월 8일, Adobe은 Adobe Commerce, Magento Open Source 및 [!DNL Adobe Commerce Webhooks Plugin]에 대해 정기적으로 예약된 보안 업데이트를 발표했습니다.
이 업데이트는 [[!DNL critical, important] 및 [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html)개의 취약점을 해결합니다. 성공적으로 사용하면 임의 코드 실행, 임의 파일 시스템 읽기, 보안 기능 우회 및 권한 에스컬레이션이 발생할 수 있습니다. 게시판은 [Adobe 보안 게시판([!DNL APSB24-73])](https://helpx.adobe.com/security/products/magento/apsb24-73.html)입니다.

>[!NOTE]
>
>위의 보안 게시판에 나열된 **[!DNL CVE-2024-45115]은(는) [!DNL B2B] 모듈을 사용하는 경우에만 적용됩니다.** 이 취약성에 대한 수정 사항을 가능한 한 빨리 적용할 수 있도록 하기 위해 Adobe은 [!DNL CVE-2024-45115]을(를) 확인하는 격리된 패치도 발표했습니다.

**가능한 한 빨리 최신 보안 업데이트를 적용하십시오. 그렇게 하지 않으면 이러한 보안 문제에 취약할 수 있으며 Adobe에서 수정할 수 있는 수단이 제한됩니다.**

>[!NOTE]
>
>보안 패치/격리된 패치를 적용하는 데 문제가 발생하는 경우 지원 서비스에 문의하십시오.

## 영향을 받는 제품 및 버전

Adobe Commerce on Cloud, Adobe Commerce 온-프레미스 및 Magento Open Source:

* 2.4.7-p3 및 이전
* 2.4.6-p8 및 이전
* 2.4.5-p10 및 이전
* 2.4.4-p11 및 이전

## Adobe Commerce on Cloud, Adobe Commerce 온프레미스 소프트웨어 및 Magento Open Source 솔루션

영향을 받는 제품 및 버전의 취약성을 해결하려면 [!DNL CVE-2024-45115] Isolated 패치를 적용해야 합니다.

## 격리된 패치 세부 정보

다음과 같은 연결된 Isolated 패치를 사용합니다.

[vuln-25610-composer-patch.zip](assets/vuln-25610-composer-patch.zip)

## Isolated 패치를 적용하는 방법

파일의 압축을 풀고 지침이 필요하면 지원 기술 자료에서 [Adobe이 제공한 작성기 패치를 적용하는 방법](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)을 참조하십시오.

## Adobe Commerce on Cloud 판매자의 경우에만 - 격리된 패치가 적용되었는지 여부를 확인하는 방법

문제가 패치되었는지 쉽게 확인할 수 없는 점을 고려하여 [!DNL CVE-2024-45115] 격리된 패치가 성공적으로 적용되었는지 확인할 수 있습니다.

<u>다음 단계를 수행하여 `VULN-27015-2.4.7_COMPOSER.patch` **파일을 예로 사용**</u>&#x200B;할 수 있습니다.

1. [품질 패치 도구 설치](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. 명령 실행: <br>
   ![cve-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. 다음과 유사한 출력이 표시되어야 합니다. 여기서 VULN-27015은 *적용됨* 상태를 반환합니다.

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

## 보안 업데이트

Adobe Commerce에서 사용할 수 있는 보안 업데이트:

* [Adobe 보안 게시판([!DNL APSB24-73])](https://helpx.adobe.com/security/products/magento/apsb24-73.html)
