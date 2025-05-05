---
title: 관리자 암호가 작업 로그에 일반 텍스트로 저장되었습니다.
description: 이 문서에서는 Commerce 관리자가 관리자 권한을 가진 새 사용자를 만들고 암호가 'magento_logging_event_changes' 데이터베이스 테이블에 일반 텍스트로 저장되는 경우에 대한 수정 사항을 제공합니다.
exl-id: 0e91198e-66b9-456a-9b75-5986369ed8e6
feature: Admin Workspace, Logs
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 관리자 암호가 작업 로그에 일반 텍스트로 저장되었습니다.

이 문서에서는 Commerce 관리자가 관리자 권한을 가진 새 사용자를 만들 때 암호를 `magento_logging_event_changes` 데이터베이스 테이블에 일반 텍스트로 저장하는 경우에 대한 수정 사항을 제공합니다.

이 보안 문제를 해결하려면 Adobe Commerce 2.0.16 및 2.1.9 보안 업데이트를 설치합니다. 보안 업데이트를 적용하면 암호가 암호화되며 일반 텍스트로 표시되지 않습니다.

## 영향을 받는 버전 {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Affectedversions}

* Adobe Commerce 온-프레미스 2.X.X
* 클라우드 인프라의 Adobe Commerce 2.X.X

## 문제 {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Issue}

기존 Commerce 관리자가 **시스템** > **권한** > **모든 사용자** > **새 사용자 추가**&#x200B;를 통해 관리자 권한을 가진 새 사용자를 만들 때 암호(확인으로 입력됨)가 `magento_logging_event_changes` 데이터베이스 표에 일반 텍스트로 저장됩니다.

### 재현 단계: {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Stepstoreproduce}

1. 관리자로 로그인하고 **시스템** > 권한 > **모든 사용자** 경로로 이동하여 새 사용자를 만드십시오.

   ![add_user_magento_2.4.1.png](assets/add_user_magento_2.4.1.png)

1. **새 사용자 추가** 페이지를 클릭합니다. 메시지가 표시되면 현재 관리자의 암호를 입력합니다.
1. **시스템** > **작업 로그** > **보고서** 페이지로 이동하여 마지막 로그 항목을 찾습니다.
1. 암호화되거나 해시되지 않은 현재 암호를 볼 수 있습니다.

## 솔루션 {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Solution}

[Adobe Commerce 2.0.16 및 2.1.9 보안 업데이트](https://magento.com/security/patches/magento-2016-and-219-security-update)를 설치하면 이 문제가 해결됩니다.

보안 업데이트를 설치한 후 암호가 암호화되며 `magento_logging_event_changes` 표에 일반 텍스트로 표시되지 않습니다.

## 추가 정보 {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Moreinformation}

* 보안 센터의 [Adobe Commerce 2.0.16 및 2.1.9 보안 업데이트 페이지](https://magento.com/security/patches/magento-2016-and-219-security-update)
* 개발자 설명서에서 [Adobe Commerce 애플리케이션 및 구성 요소 업그레이드](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html?lang=ko)
* Commerce 구현 플레이북의 [데이터베이스 테이블 수정 우수 사례](https://experienceleague.adobe.com/ko/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
