---
title: Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0 호환성 패키지 핫픽스
description: 이 문서에서는 클라우드 인프라 2.4.7-p4의 Adobe Commerce을 사용하는 새  [!DNL HIPAA] 패키지 1.2.0에 대한 호환성을 추가하는 핫픽스를 제공합니다
feature: Install, Upgrade, Security, Compliance
role: Developer
source-git-commit: 705c43d2328d47fb5f00ae582a2a623ca9f94f70
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0 호환성 패키지 핫픽스

이 문서에서는 Cloud Infrastructure 2.4.7-p4의 Adobe Commerce을 사용하는 새 **[!DNL HIPAA]패키지 1.2.0**&#x200B;에 대한 호환성을 추가하는 핫픽스를 제공합니다.

이 문제는 버전 2.4.7-p5 릴리스에서 수정됩니다.

## 영향을 받는 버전 및 제품

클라우드 인프라 2.4.7-p4 및 이전 버전의 Adobe Commerce

## 전제 조건

* Adobe에서 **[!DNL HIPAA Ready]** 확장에 액세스할 수 있도록 Adobe Commerce 계정을 프로비저닝했습니다. 자세한 내용은 **Adobe Commerce: 시작 안내서**&#x200B;에서 [[!DNL HIPAA] Adobe Commerce의 준비](https://experienceleague.adobe.com/ko/docs/commerce-admin/start/compliance/hipaa-ready-service/overview)를 참조하십시오.
* 확장을 설치하려면 [repo.magento.com](https://repo.magento.com)에 액세스하십시오. 키를 생성하고 필요한 권한을 얻으려면 **Adobe Commerce: 설치 안내서**&#x200B;에서 [인증 키 가져오기](https://experienceleague.adobe.com/ko/docs/commerce-operations/installation-guide/prerequisites/authentication-keys)를 참조하십시오.

## 문제

[!DNL HIPAA] 패키지 1.1.0은 Adobe Commerce 2.4.7x 릴리스 라인과 호환되지 않습니다.

## 솔루션

이 핫픽스를 통해 클라우드 인프라 2.4.7-p4에서 Adobe Commerce을 실행하는 판매자는 [!DNL HIPAA] 패키지 1.2.0을 사용할 수 있습니다.

>[!NOTE]
>
>**[!DNL HIPAA]1.2.0은 Adobe Commerce 2.4.7-p5와만 호환됩니다. Adobe Commerce 2.4.7-p4에 [!DNL HIPAA] 1.2.0과의 호환성을 추가하려면 제공된 패치를 설치하십시오.<br><u>Adobe Commerce 2.4.7-p4를 사용하지 않는 경우 이 패치를 사용하려면 먼저 Adobe Commerce 2.4.7-p4로 업그레이드해야 합니다</u>.**

클라우드 인프라 2.4.7-p4에서 Adobe Commerce의 문제를 해결하려면 패치를 적용해야 합니다.

[ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip](assets/ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip)

## 패치 적용 방법

파일의 압축을 풀고 지침이 필요하면 지원 기술 자료에서 [Adobe에서 제공하는 작성기 패치를 적용하는 방법](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=ko)을 참조하십시오.

## Adobe Commerce on Cloud 판매자의 경우에만 - 패치가 적용되었는지 여부를 확인하는 방법

문제가 패치되었는지 쉽게 확인할 수 없는 점을 고려하면 패치가 성공적으로 적용되었는지 확인할 수 있습니다.

>[!NOTE]
>
><u>다음 단계를 수행하여 `VULN-27015-2.4.7_COMPOSER.patch` **파일을 예로 사용**</u>&#x200B;할 수 있습니다.

1. [품질 패치 도구 설치](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ko).
1. 명령 실행: <br>
   ![cve-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. 다음과 유사한 출력이 표시됩니다. **<u>여기에 사용된 예제 VULN-27015</u>**&#x200B;이(가) *적용됨* 상태를 반환하는 경우:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->
