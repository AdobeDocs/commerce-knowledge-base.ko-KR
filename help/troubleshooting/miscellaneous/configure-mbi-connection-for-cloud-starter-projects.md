---
title: 기존 Cloud Starter 프로젝트에 대한 Adobe Commerce Intelligence 연결 구성
description: 이 문서에서는 기존 Cloud Starter 프로젝트에 대해 Adobe Commerce Intelligence 연결을 구성하려는 경우에 대한 솔루션을 제공합니다.
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: b75328202952bf4c8f57ddc538b5c9e4318b2001
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# 기존 Cloud Starter 프로젝트에 대한 Adobe Commerce Intelligence 연결 구성

>[!NOTE]
>
>Adobe Commerce Intelligence은 이전에 Magento Business Intelligence(MBI)라고 했습니다.

이 문서에서는 기존 Cloud Starter 프로젝트에 대해 Adobe Commerce Intelligence 연결을 구성하려는 경우에 대한 솔루션을 제공합니다.

## 영향을 받는 제품 및 버전

Adobe Commerce on cloud starter(모든 버전)

## 문제

기존 Cloud Starter 프로젝트에 대해 Commerce Intelligence 연결을 구성하려고 합니다.

>[!NOTE]
>
>Adobe은 더 이상 새 Cloud Starter 구독을 지원하지 않지만 기존 스타터 프로젝트가 있는 경우 아래 단계를 따라 연결을 구성해야 합니다.

## 솔루션

Cloud Starter 프로젝트용 Commerce Intelligence을 활성화하려면 Commerce Intelligence 계정을 만들고 SSH 키를 만든 다음, 마지막으로 Adobe Commerce 데이터베이스에 연결하십시오.

다음 단계를 수행합니다.

1. Adobe Commerce Intelligence 계정 만들기:

   * [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login)(으)로 이동합니다.
   * **[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**(으)로 이동합니다.
   * **[!UICONTROL Create Instance]**&#x200B;을(를) 클릭합니다. 이 단추가 표시되지 않으면 Customer Success Manager 또는 Customer Technical Advisor에게 문의하십시오.
   * Cloud Starter 구독을 선택합니다. Cloud Starter 구독만 있는 경우 자동으로 선택됩니다.
   * **[!UICONTROL Continue]**&#x200B;을(를) 클릭합니다.
   * 계정을 만들려면 정보를 입력하십시오.

   ![MBI 계정 만들기](/help/troubleshooting/miscellaneous/assets/create_mbi_account.png)

   * 받은 편지함으로 이동하여 이메일 주소를 확인합니다.

   ![전자 메일 주소 확인](/help/troubleshooting/miscellaneous/assets/verify_email_address_mbi.png)

   * 암호를 만듭니다.

   ![암호 만들기](/help/troubleshooting/miscellaneous/assets/create_password_mbi.png)

   * 계정을 만든 후에는 새 계정에 사용자를 추가할 수 있는 옵션이 제공됩니다. 이제 기술 관리자를 추가하여 다음 단계를 수행할 수 있습니다.

   ![사용자 추가](/help/troubleshooting/miscellaneous/assets/add_users_mbi.png)

1. 환경 설정을 지정할 스토어에 대한 정보를 입력하십시오.

   ![저장소 정보 추가](/help/troubleshooting/miscellaneous/assets/add_store_info_mbi.png)

   온보딩 흐름의 세 번째 단계에서 데이터베이스를 연결하기 전에 수집해야 하는 정보가 있습니다. 9단계에서 *[!UICONTROL Connect your database]* 페이지를 작성합니다.

1. 전용 Commerce Intelligence 사용자를 만듭니다.

   * [account.adobe.com](https://account.adobe.com/)에서 새 사용자를 만듭니다.
   * [https://accounts.magento.com/customer/account/](https://accounts.magento.com/customer/account/)(으)로 이동하여 Adobe Commerce 계정을 생성합니다.
   * 왜 새 사용자입니까? Adobe Commerce Intelligence을 사용하려면 프로젝트에 추가된 사용자가 계정의 Commerce Intelligence 데이터 웨어하우스로 전송할 새 데이터를 계속 가져와야 합니다. 이 사용자는 해당 연결 역할을 합니다. 이 사용자를 프로젝트에 추가하는 단계는 4단계에서 수행됩니다.
   * 전용 Commerce Intelligence 사용자가 있는 이유는 추가된 사용자가 실수로 비활성화되거나 삭제되어 Commerce Intelligence 연결이 중지되는 것을 방지하기 위해서입니다.

1. 새로 만든 사용자를 프로젝트의 기본 환경에 *기여자*(으)로 추가합니다.

   ![기여자로 사용자 추가](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png)

1. Commerce Intelligence SSH 키를 가져옵니다.

   * Commerce Intelligence 설정 사용자 인터페이스의 **[!UICONTROL Connect your database]** 페이지로 이동한 다음 **[!UICONTROL Encryption settings]**(으)로 스크롤합니다.
   * 필드 **[!UICONTROL Encryption Type]**&#x200B;에 대해 **[!UICONTROL SSH Tunnel]**&#x200B;을(를) 선택합니다.
   * 드롭다운에서 제공된 Magento BI Essentials 공개 키를 복사하여 붙여넣을 수 있습니다.

   ![암호화 설정](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. 5단계에서 만든 Commerce Intelligence 사용자에게 새 Magento BI Essentials 공개 키를 추가합니다.

   * [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login)(으)로 이동합니다. 새로 만든 Commerce Intelligence 사용자에 대한 계정 로그인 정보로 로그인합니다. 그런 다음 **[!UICONTROL Account Settings]** 탭으로 이동합니다.
   * 페이지를 아래로 스크롤하고 SSH 키에 대한 드롭다운을 확장합니다. **[!UICONTROL Add a public key]**&#x200B;을(를) 클릭합니다.

   ![공개 키 추가](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png)

   * 위에서 Magento MBI Essentials SSH 공개 키를 추가합니다.

   ![SSH 공개 키 추가](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. Business Intelligence Essentials MySQL 자격 증명을 제공합니다.

   * `.magento/services.yaml`을(를) 업데이트합니다.

   ```
   mysql:
    type: mysql:10.0
    disk: 2048
    configuration:
        schemas:
            - main
        endpoints:
            mysql:
                default_schema: main
                privileges:
                    main: admin
            mbi:
                default_schema: main
                privileges:
                    main: ro
   ```

   * `.magento.app.yaml`을(를) 업데이트합니다.

   ```
   relationships:
            database: "mysql:mysql"
            mbi: "mysql:mbi"
            redis: "redis:redis"
   ```

1. 데이터베이스를 Commerce Intelligence에 연결하기 위한 정보를 가져옵니다.

   데이터베이스 연결에 대한 정보를 보려면 `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp`을(를) 실행하십시오.

   아래 출력과 유사한 정보를 수신해야 합니다.

   ```
   "mbi" : [
              {
                 "scheme" : "mysql",
                 "rel" : "mbi",
                 "cluster" : "vfbfui4vmfez6-master-7rqtwti",
                 "query" : {
                    "is_master" : true
                 },
                 "ip" : "169.254.169.143",
                 "path" : "main",
                 "host" : "mbi.internal",
                 "hostname" : "3m7xizydbomhnulyglx2ku4wpq.mysql.service._.magentosite.cloud",
                 "username" : "mbi",
                 "service" : "mysql",
                 "port" : 3306,
                 "password" : "[password]"
              }
           ],
   ```

1. Adobe Commerce 데이터베이스를 연결합니다.

   ![Adobe Commerce 데이터베이스 연결](/help/troubleshooting/miscellaneous/assets/connect_magento_database_mbi.png)

   *입력*:

   * 통합 이름: [통합 이름을 선택하십시오.]
   * 호스트: `mbi.internal`
   * 포트: 3306
   * 사용자 이름: mbi
   * 암호: [8단계 출력에 입력한 암호.]
   * 데이터베이스 이름: main
   * 테이블 접두사: [테이블 접두사가 없으면 비워 둡니다]

1. [!UICONTROL Timezone Settings]을(를) 설정합니다.

   ![표준 시간대 설정](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *입력*

   * 데이터베이스: 시간대: UTC
   * 원하는 시간대: [데이터를 표시할 시간대를 선택합니다.]

1. 암호화 설정에 대한 정보를 가져옵니다.

   * 프로젝트 UI는 SSH 액세스 문자열을 제공합니다. 이 문자열은 **[!UICONTROL Encryption settings]**&#x200B;을(를) 설정할 때 원격 주소 및 사용자 이름에 필요한 정보를 수집하는 데 사용할 수 있습니다. 사용자 이름과 원격 주소를 보려면 **[!UICONTROL SSH]**&#x200B;을(를) 선택하십시오. *@* 앞의 텍스트 문자열은 사용자 이름이고 *@* 뒤의 텍스트 문자열은 원격 주소입니다.

   ![사이트 마스터에 액세스](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. [!UICONTROL Encryption Settings]에 대한 정보를 입력하십시오.

   ![암호화 설정](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *입력*

   * 암호화 유형: SSH 터널
   * 원격 주소: ssh.us-3.magento.cloud
   * 사용자 이름: vfbfui4vmfez6-master-7rqtwti—mymagento
   * 포트: 22

1. **[!UICONTROL Save Integration]**&#x200B;을(를) 클릭합니다.
1. 이제 Commerce Intelligence Essentials 계정에 성공적으로 연결했습니다.
1. Adobe Commerce Intelligence Pro 고객인 경우 고객 성공 관리자 또는 고객 기술 관리자에게 문의하여 다음 단계를 조정하십시오.
