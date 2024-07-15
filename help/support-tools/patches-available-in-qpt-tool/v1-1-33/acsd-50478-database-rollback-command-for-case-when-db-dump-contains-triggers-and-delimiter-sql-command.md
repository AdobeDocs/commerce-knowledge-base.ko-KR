---
title: 'ACSD-50478: backups grid and database rollback 명령의 롤백 작업에 대한 JS 문제'
description: ACSD-50478 패치를 적용하여 백업 그리드의 롤백 작업에 대한 JS 문제와 DB 덤프에 트리거와 *구분 기호* SQL 명령이 포함된 경우에 대한 데이터베이스 롤백 명령을 수정합니다.
exl-id: 8b516705-29be-462e-b3ec-3a339b6e8006
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-50478: 백업 그리드 및 데이터베이스 롤백 명령의 롤백 작업에 대해 JS 문제 발생

ACSD-50478 패치는 DB 덤프에 트리거와 *구분 기호* SQL 명령이 포함된 경우에 대한 데이터베이스 롤백 명령과 백업 그리드의 롤백 작업에 대한 JS 문제를 수정합니다. 이 패치는 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33이 설치된 경우에 사용할 수 있습니다. 패치 ID는 ACSD-50478입니다. 이 문제는 Adobe Commerce 2.4.7에서 수정됩니다.

## 영향을 받는 제품 및 버전

**Adobe Commerce 버전에 대한 패치가 만들어졌습니다.**

* Adobe Commerce(모든 배포 방법) 2.4.3-p1

**Adobe Commerce 버전과 호환:**

* Adobe Commerce(모든 배포 방법) 2.4.0 - 2.4.4-p4

>[!NOTE]
>
>새 [!DNL Quality Patches Tool] 릴리스가 있는 다른 버전에 패치를 적용할 수 있습니다. 패치가 Adobe Commerce 버전과 호환되는지 확인하려면 `magento/quality-patches` 패키지를 최신 버전으로 업데이트하고 [[!DNL Quality Patches Tool]에서 호환성을 확인합니다. 패치 검색 페이지](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 패치 ID를 검색 키워드로 사용하여 패치를 찾습니다.

## 문제

DB 덤프에 트리거와 *구분 기호* SQL 명령이 포함된 경우에 대한 데이터베이스 롤백 명령과 백업 그리드의 롤백 작업에 대한 JS 문제.

<u>재현 단계</u>:

1. 인덱서를 [!UICONTROL Update on Schedule] 모드로 설정하여 데이터베이스에 트리거를 만듭니다.
1. 명령줄에서 백업 기능을 활성화합니다.

   `bin/magento config:set system/backup/functionality_enabled 1`

1. **시스템** > **도구** > **백업**(으)로 이동하여 DB 백업을 생성합니다.
1. 브라우저 콘솔을 엽니다. 다음 오류가 표시됩니다.

   ```
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. 명령줄에서 DB를 가져오려고 합니다.

   `bin/magento setup:rollback --db-file="<filename>"`

1. 다음 오류가 나타납니다.

   ```
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u>예상 결과</u>:

관리자 및 명령줄 모두에서 데이터베이스 복원에 성공했습니다.

<u>실제 결과</u>:

4단계와 6단계에서 언급된 오류를 관찰했습니다.

## 패치 적용

개별 패치를 적용하려면 배포 방법에 따라 다음 링크를 사용합니다.

* Adobe Commerce 또는 Magento Open Source 온-프레미스: [!DNL Quality Patches Tool] 가이드의 [[!DNL Quality Patches Tool] > 사용량](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)
* 클라우드 인프라의 Adobe Commerce: Commerce on Cloud Infrastructure 안내서의 [업그레이드 및 패치 > 패치 적용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html).

## 관련 읽기

[!DNL Quality Patches Tool]에 대한 자세한 내용은 다음을 참조하세요.

* [[!DNL Quality Patches Tool] 릴리스됨: 지원 기술 자료에서 품질 패치를 자체 제공하는 새로운 도구](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [지원 기술 자료에서  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)을(를) 사용하여 Adobe Commerce 문제에 대한 패치를 사용할 수 있는지 확인합니다.

QPT에서 사용할 수 있는 다른 패치에 대한 정보는 [!DNL Quality Patches Tool] 안내서에서 [[!DNL Quality Patches Tool]: 패치 검색](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)을 참조하세요.
