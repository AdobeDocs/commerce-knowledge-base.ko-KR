---
title: Adobe Commerce에서 최대 쿠키 수 초과 오류
description: 최대 쿠키 수를 초과한다고 발표하는 오류가 발생하는 Adobe Commerce 문제를 해결하는 방법에 대해 알아봅니다.
feature: Deploy, Support, Upgrade, Tools and External Services
role: Admin, Developer
source-git-commit: 44e167c801bbcd313f74c9fc51f9cde9473ef96f
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Adobe Commerce에서 *최대 쿠키 수를 초과했습니다* 오류

이 문서에서는 Adobe Commerce에서 *최대 쿠키 수가*&#x200B;개를 초과한다는 오류를 해결하기 위한 패치를 제공합니다.

## 영향을 받는 제품 및 버전

다음 패치 중 하나가 적용된 Adobe Commerce(모든 배포 방법) 2.4.4 - 2.4.7

* [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ko/docs/commerce-operations/tools/quality-patches-tool/release-notes)을(를) 사용하여 MDVA-12304 패치가 적용됨
* [APSB25-08 격리 보안 패치](/help/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08.md)
* [!DNL Commerce] 1.1.4[&#128279;](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches)용 클라우드 패치

## 문제

Adobe Commerce의 쿠키와 관련된 문제로 인해 오류 로그에 다음 오류가 표시됩니다.

*report.WARNING: 쿠키를 보낼 수 없습니다. 최대 쿠키 수를 초과했습니다.*

### 원인

이 문제는 허용된 최대 쿠키 수가 *50*(으)로 설정되어 있기 때문에 발생합니다.

## 솔루션

1. [!DNL Quality Patches Tool (QPT)]을(를) 사용하여 MDVA-12304 패치를 적용한 경우 해당 패치를 제거합니다.

   * 클라우드 인프라의 Adobe Commerce에 대해 `.magento.env.yaml`에서 패치를 제거하십시오.
   * Adobe Commerce 온-프레미스 설치의 경우 다음 명령을 실행하여 패치를 되돌립니다.

     `vendor/bin/magento/quality-patches revert MDVA-12304`

1. Adobe Commerce 버전에 따라 첨부된 패치를 적용합니다.

   * 버전 2.4.4-p12, 2.4.5-p11, 2.4.6-p9 및 2.4.7-p4의 경우 [ACSD-64710 패치](assets/acsd-64710_2.4.5-p11.patch.zip)를 적용합니다.

   * 버전 2.4.4-p13, 2.4.5-p12, 2.4.6-p10, 2.4.7-p5 및 2.4.8의 경우 [ACSD-65562 패치](assets/acsd-65562_2.4.5-p12.patch.zip)를 적용합니다.

### 관련 읽기

* Adobe Commerce 업그레이드 가이드의 [패치 적용](https://experienceleague.adobe.com/ko/docs/commerce-operations/upgrade-guide/patches/apply)
* Adobe Commerce 구현 플레이북의 [Adobe Commerce 패치를 대규모로 배포하는 모범 사례](https://experienceleague.adobe.com/ko/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale)
* Commerce on Cloud 안내서의 [Commerce Cloud 도구 모음 릴리스 정보](https://experienceleague.adobe.com/ko/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite).
