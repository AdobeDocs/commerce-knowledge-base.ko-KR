---
title: Adobe Commerce에 사용 가능한 보안 업데이트 - [!DNL APSB25-08]
promoted: true
description: Adobe Commerce 2.4.8-beta1, 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11 및 이전 버전에 대해  [!DNL critical, important, and moderate vulnerabilities] 수정할 격리된 패치를 적용합니다.
feature: Compliance, Security
role: Developer
exl-id: 567e6ad2-704e-461f-a54d-75f6bd96e996
source-git-commit: d669c097767b5855c6bd747a0ab11b3520f405a0
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Adobe Commerce에 사용 가능한 보안 업데이트 - [!DNL APSB25-08]

2025년 2월 11일에 Adobe은 Adobe Commerce 및 Magento Open Source에 대해 정기적으로 예약된 보안 업데이트를 발표했습니다. 이 업데이트는 [[!DNL critical, important] 및 [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html)개의 취약점을 해결합니다. 이러한 취약점을 성공적으로 사용하면 임의 코드 실행, 보안 기능 우회 및 권한 에스컬레이션이 발생할 수 있습니다. 자세한 내용은 [Adobe 보안 게시판([!DNL APSB25-08])의 ](https://helpx.adobe.com/security/products/magento/apsb25-08.html)에서 확인할 수 있습니다.

>[!NOTE]
>
>**위의 보안 게시판에 나열된 [!DNL CVE-2025-24434]에 대한 수정 사항을 가능한 한 빨리 적용할 수 있도록 하기 위해 Adobe은 [!DNL CVE-2025-24434]을(를) 확인하는 격리된 패치도 발표했습니다. 이를 통해 판매자는 잠재적인 통합 문제로 인해 지연될 위험이 적은 상태로 이 수정 사항을 별도로 적용할 수 있습니다.**

**가능한 한 빨리 최신 보안 업데이트를 적용하십시오. 그렇게 하지 않으면 이러한 보안 문제에 취약해질 수 있으며 Adobe은 문제를 더 이상 해결할 수 있는 제한된 수단이 있습니다.**

>[!NOTE]
>
>보안 패치/격리된 패치를 적용하는 데 문제가 발생하는 경우 지원 서비스에 문의하십시오.

## 영향을 받는 제품 및 버전

Adobe Commerce on Cloud infrastructure, Adobe Commerce 온프레미스 및 Magento Open Source:

* 2.4.8-beta1 및 이전
* 2.4.7-p3 및 이전
* 2.4.6-p8 및 이전
* 2.4.5-p10 및 이전
* 2.4.4-p11 및 이전

## Adobe Commerce on Cloud, Adobe Commerce 온프레미스 및 Magento Open Source 소프트웨어 솔루션

영향을 받는 제품 및 버전의 취약성을 해결하려면 Adobe Commerce/Magento Open Source 버전에 따라 [!DNL CVE-2025-24434] Isolated 패치를 적용해야 합니다.

## 격리된 패치 세부 정보

Adobe Commerce/Magento Open Source 버전에 따라 다음과 같이 첨부된 Isolated 패치를 사용하십시오.

### 버전 2.4.8-beta1의 경우:

* [vuln-28982-2-4-8x-v2-composer-patch.zip](assets/vuln-28982-2-4-8x-v2-composer-patch.zip)

### 버전 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3:

* [vuln-28982-2-4-7x-v2-composer-patch.zip](assets/vuln-28982-2-4-7x-v2-composer-patch.zip)

### 버전 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8:

* [vuln-28982-2-4-6x-v2-composer-patch.zip](assets/vuln-28982-2-4-6x-v2-composer-patch.zip)

### 버전 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10:

* [vuln-28982-2-4-5x-v2-composer-patch.zip](assets/vuln-28982-2-4-5x-v2-composer-patch.zip)

### 버전 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11:

* [vuln-28982-2-4-4x-v2-composer-patch.zip](assets/vuln-28982-2-4-4x-v2-composer-patch.zip)


## Isolated 패치를 적용하는 방법

파일의 압축을 풀고 지침이 필요하면 지원 기술 자료에서 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)을 참조하십시오.

## Adobe Commerce on Cloud 판매자의 경우에만 - 격리된 패치가 적용되었는지 여부를 확인하는 방법

문제가 패치되었는지 쉽게 확인할 수 없는 점을 고려하여 [!DNL CVE-2025-24434] 격리된 패치가 성공적으로 적용되었는지 확인할 수 있습니다.

>[!NOTE]
>
><u>다음 단계를 수행하여 `VULN-27015-2.4.7_COMPOSER.patch` **파일을 예로 사용**</u>&#x200B;할 수 있습니다.

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

* [Adobe 보안 게시판([!DNL APSB25-08])](https://helpx.adobe.com/security/products/magento/apsb25-08.html)
* [Adobe Commerce에서 사용할 수 있는 최신 보안 업데이트](https://helpx.adobe.com/security/products/magento.html)