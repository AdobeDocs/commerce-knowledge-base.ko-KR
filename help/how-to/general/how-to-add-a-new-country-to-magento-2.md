---
title: Adobe Commerce에 새 국가를 추가하는 방법
description: 이 문서에서는 Adobe Commerce 및 Zend 로케일 라이브러리에 없는 국가를 추가하는 방법에 대해 설명합니다. 이를 위해서는 적용 가능한 계약 조건에 따라 고객 맞춤화를 구성하는 코드 및 데이터베이스 변경 사항이 필요합니다. 이 문서에 포함된 예제 자료는 어떠한 종류의 보증도 없이 "있는 그대로" 제공됩니다. Adobe 및 관련 업체는 이러한 자료를 유지, 수정, 업데이트, 변경, 수정 또는 지원할 의무가 없습니다. 여기에서 우리는 이것을 달성하기 위해 무엇이 행해져야 하는지에 대한 기본 원칙을 기술할 것이다.
exl-id: af499add-4966-4a3a-972a-62a34c169a1b
feature: Build, Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 0%

---

# Adobe Commerce에 새 국가를 추가하는 방법

이 문서에서는 Adobe Commerce 및 Zend 로케일 라이브러리에 없는 국가를 추가하는 방법에 대해 설명합니다. 이를 위해서는 적용 가능한 계약 조건에 따라 고객 맞춤화를 구성하는 코드 및 데이터베이스 변경 사항이 필요합니다. 이 문서에 포함된 예제 자료는 어떠한 종류의 보증도 없이 &quot;있는 그대로&quot; 제공됩니다. Adobe 및 관련 업체는 이러한 자료를 유지, 수정, 업데이트, 변경, 수정 또는 지원할 의무가 없습니다. 여기에서 우리는 이것을 달성하기 위해 무엇이 행해져야 하는지에 대한 기본 원칙을 기술할 것이다.

이 예제에서는 Adobe Commerce 설치 또는 업그레이드 프로세스 시 적용되는 데이터 패치를 사용하여 새 Adobe Commerce 모듈을 만들고 국가 코드가 XX인 Abstract Country를 Adobe Commerce에 추가합니다. [Adobe Commerce 디렉터리](https://developer.adobe.com/commerce/php/module-reference/module-directory/)에서 초기 국가 목록을 만든 다음 설치 패치를 사용하여 해당 목록에 영역을 추가합니다. 이 문서에서는 새 국가를 목록에 추가할 새 모듈을 만드는 방법을 설명합니다. 기존 Adobe Commerce 디렉토리 모듈의 코드를 참조하여 검토할 수 있습니다. 이는 다음 예제 모듈이 국가 및 지역 목록을 작성하는 디렉토리 모듈 작업을 계속하고 Adobe Commerce 디렉토리 모듈 설치 패치 코드의 일부를 재사용하기 때문입니다.

## 권장 설명서

새 모듈을 만들려면 Adobe Commerce 모듈 개발에 익숙해야 합니다.

새 모듈을 만들기 전에 개발자 설명서에서 다음 항목을 참조하십시오.

* [PHP 개발자 안내서](https://developer.adobe.com/commerce/php/development/)
* [모듈 개요](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [새 모듈 만들기](https://experienceleague.adobe.com/ko/docs/commerce-learn/tutorials/backend-development/create-module)
* [모듈 구성 파일](https://experienceleague.adobe.com/ko/docs/commerce-operations/configuration-guide/files/module-files)

## 필수 정보

새 국가에는 Adobe Commerce 전체에서 고유한 이름, 국가 ID, ISO2 및 ISO3 코드가 있어야 합니다.

## 모듈 구조

이 예제에서는 다음 디렉터리 구조로 \`ExtraCountries\`라는 새 모듈을 만듭니다.

모듈 구조에 대한 자세한 내용은 개발자 설명서에서 [모듈 개요](https://developer.adobe.com/commerce/php/architecture/modules/overview/)를 참조하십시오.

<pre>&lt;ExtraCountries>
 |
 &lt;etc>
 | |
 | config.xml
 | di.xml
 | module.xml
 |
 &lt;Plugin>
 | |
 | &lt;Framework>
 |   |
 |   &lt;Locale>
 |     |
 |     TranslatedListsPlugin.php
 |
 &lt;Setup>
 | |
 | &lt;Patch>
 |   |
 |   &lt;Data>
 |     |
 |     AddDataForAbstractCountry.php
 |
 composer.json
 registration.php</pre>

>[!NOTE]
>
>이 문서의 각 헤더 섹션에서는 모듈 구조 섹션의 파일에 대해 설명합니다.

## ExtraCountries/etc/config.xml

이 XML 파일에 새 모듈 구성이 정의되어 있습니다. 새 국가 기본 설정을 조정하기 위해 다음 구성 및 태그를 편집할 수 있습니다.

* `allow` - 기본적으로 새로 추가된 국가를 &quot;허용 국가&quot; 목록에 추가하려면 `allow` 태그 콘텐츠의 끝에 새 국가 코드를 추가하십시오. 국가 코드는 쉼표로 구분됩니다. 이 태그는 `Directory` 모듈 구성 파일 *(Directory/etc/config.xml)* `allow` 태그의 데이터를 덮어씁니다. 따라서 여기에 있는 모든 코드와 새 코드를 추가합니다.
* `optional_zip_countries` - 새로 추가된 국가의 우편 번호를 선택 사항이어야 하는 경우 `optional_zip_countries` 태그의 콘텐츠 끝에 국가 번호를 추가하십시오. 국가 코드는 쉼표로 구분됩니다. 이 태그는 `Directory` 모듈 구성 파일 *(Directory/etc/config.xml)* `optional_zip_countries` 태그의 데이터를 덮어씁니다. 따라서 여기에 있는 모든 코드와 새 코드를 추가합니다.
* `eu_countries` - 새로 추가된 국가가 기본적으로 유럽 연합 국가 목록의 일부여야 하는 경우 `eu_countries` 태그의 콘텐츠 끝에 국가 코드를 추가합니다. 국가 코드는 쉼표로 구분됩니다. 이 태그는 `Store` 모듈 구성 파일 *(\_Store/etc/config.xml\_)* `eu_countries` 태그의 데이터를 덮어씁니다. 따라서 여기에 있는 모든 코드와 새 코드를 추가합니다.
* `config.xml` 파일 예제

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <general>
            <country>
                <!-- append a new country codes to the end of this list -->
                <allow>AF,AL,DZ,AS,AD,AO,AI,AQ,AG,AR,AM,AW,AU,AT,AX,AZ,BS,BH,BD,BB,BY,BE,BZ,BJ,BM,BL,BT,BO,BQ,BA,BW,BV,BR,IO,VG,BN,BG,BF,BI,KH,CM,CA,CD,CV,KY,CF,TD,CL,CN,CX,CW,CC,CO,KM,CG,CK,CR,HR,CU,CY,CZ,DK,DJ,DM,DO,EC,EG,SV,GQ,ER,EE,ET,FK,FO,FJ,FI,FR,GF,PF,TF,GA,GM,GE,DE,GG,GH,GI,GR,GL,GD,GP,GU,GT,GN,GW,GY,HT,HM,HN,HK,HU,IS,IM,IN,ID,IR,IQ,IE,IL,IT,CI,JE,JM,JP,JO,KZ,KE,KI,KW,KG,LA,LV,LB,LS,LR,LY,LI,LT,LU,ME,MF,MO,MK,MG,MW,MY,MV,ML,MT,MH,MQ,MR,MU,YT,FX,MX,FM,MD,MC,MN,MS,MA,MZ,MM,NA,NR,NP,NL,AN,NC,NZ,NI,NE,NG,NU,NF,KP,MP,NO,OM,PK,PW,PA,PG,PY,PE,PH,PN,PL,PS,PT,PR,QA,RE,RO,RS,RU,RW,SH,KN,LC,PM,VC,WS,SM,ST,SA,SN,SC,SL,SG,SK,SI,SB,SO,ZA,GS,KR,ES,LK,SD,SR,SJ,SZ,SE,CH,SX,SY,TL,TW,TJ,TZ,TH,TG,TK,TO,TT,TN,TR,TM,TC,TV,VI,UG,UA,AE,GB,US,UM,UY,UZ,VU,VA,VE,VN,WF,EH,XK,YE,ZM,ZW,XX</allow>
​
                <!-- if added countries need to belong to the European Union Countries list by default, append their codes to the end of this list -->
                <eu_countries>AT,BE,BG,CY,CZ,DK,EE,FI,FR,DE,GR,HR,HU,IE,IT,LV,LT,LU,MT,NL,PL,PT,RO,SK,SI,ES,SE,GB,XX</eu_countries>
​
                <!-- if added countries are not require zip code, append it's code to the end of this list -->
                <optional_zip_countries>HK,IE,MO,PA,GB,XX</optional_zip_countries>
            </country>
        </general>
    </default>
</config>
```

모듈 구성 파일에 대한 자세한 내용은 개발자 설명서에서 [PHP 개발자 안내서 > 구성 파일 정의](https://developer.adobe.com/commerce/php/development/build/required-configuration-files/)를 참조하십시오.

이러한 변경 사항은 선택 사항이며 &quot;허용 국가&quot;, &quot;우편 번호는 선택 사항입니다&quot; 및 &quot;유럽 연합 국가&quot; 목록에 대한 새 국가의 기본 속성인 경우에만 영향을 미칩니다. 이 파일을 모듈 구조에서 건너뛰면 새 국가가 추가되지만 **관리자** > **스토어** > *설정* > **구성** > **일반** > **국가 옵션** 설정 페이지에서 수동으로 구성해야 합니다.

### ExtraCountries/etc/di.xml

`di.xml` 파일은 개체 관리자가 삽입하는 종속성을 구성합니다. `di.xml`에 대한 자세한 내용은 개발자 설명서에서 <a>PHP 개발자 안내서 > di.xml</a>을 참조하십시오.

이 예제에서는 Zend 로케일 라이브러리 지역화 데이터에 코드가 없는 경우 새로 도입된 국가 코드를 전체 국가 이름으로 변환하는 `_TranslatedListsPlugin_`을(를) 등록해야 합니다.

`di.xml` 예

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\Framework\Locale\TranslatedLists">
        <plugin name="Magento_Directory" type="VendorName\ExtraCountries\Plugin\Framework\Locale\TranslatedListsPlugin"/>
    </type>
</config>
```

### ExtraCountries/etc/module.xml

모듈 등록 파일에서 &quot;Adobe Commerce Directory&quot; 모듈에 대한 종속성을 지정해야 하므로 &quot;Extra Countries&quot; 모듈이 Directory 모듈 다음에 등록 및 실행됩니다.

모듈 종속성에 대한 자세한 내용은 개발자 설명서에서 [모듈 종속성 관리](https://developer.adobe.com/commerce/php/architecture/modules/dependencies/#managing-module-dependencies)를 참조하십시오.

`module.xml` 예

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="VendorName_ExtraCountries" >
        <sequence>
            <module name="Magento_Directory"/>
        </sequence>
    </module>
</config>
```

### ExtraCountries/Plugin/Framework/Locale/TranslatedListsPlugin.php

`aroundGetCountryTranslation()` 플러그인 메서드에서 국가 코드를 전체 국가 이름으로 변환해야 합니다. Zend 로케일 라이브러리에서 새 국가 코드와 연결된 전체 이름이 없는 국가에 대해 필요한 단계입니다.

```php
<?php
namespace VendorName\ExtraCountries\Plugin\Framework\Locale;
​
use Magento\Framework\Locale\ListsInterface;
​
/**
 * Plugin to add full names of added countries that are not included in Zend Locale Data
 */
class TranslatedListsPlugin
{
    /**
     * Get the full name of added countries
     *
     * Since the locale data for the added country may not be present in the Zend Locale Library,
     * we need to provide full country name matching the added code
     *
     * @param ListsInterface $subject
     * @param callable $proceed
     * @param $value
     * @param null $locale
     * @return string
     */
    public function aroundGetCountryTranslation(
        ListsInterface $subject,
        callable $proceed,
        $value,
        $locale = null
    )
    {
        if ($value == 'XX') {
            return 'Abstract Country';
        }
​
        return $proceed($value, $locale);
    }
}
```

### ExtraCountries/Setup/Patch/Data/AddDataForAbstractCountry.php

이 데이터 패치는 Adobe Commerce 설치/업그레이드 프로세스 중에 실행되며 새 국가 레코드를 데이터베이스에 추가합니다.

데이터 패치에 대한 자세한 내용은 개발자 설명서에서 [데이터 및 스키마 패치 개발](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/)을 참조하십시오.

아래 예제에서 `apply()` 메서드의 `$data` 배열에 새 국가의 국가 ID, ISO2 및 ISO3 코드가 포함되어 있으며 이 데이터가 데이터베이스에 삽입되어 있음을 확인할 수 있습니다.

```php
<?php
namespace Magento\ExtraCountries\Setup\Patch\Data;
​
use Magento\Framework\Setup\ModuleDataSetupInterface;
use Magento\Framework\Setup\Patch\DataPatchInterface;
use Magento\Framework\Setup\Patch\PatchVersionInterface;
​
/**
 * Add Abstract Country data to the country list
 *
 * @package Magento\ExtraCountries\Setup\Patch
 */
class AddDataForAbstractCountry implements DataPatchInterface, PatchVersionInterface
{
    /**
     * @var ModuleDataSetupInterface
     */
    private $moduleDataSetup;
​
    /**
     * @param ModuleDataSetupInterface $moduleDataSetup
     */
    public function __construct(
        ModuleDataSetupInterface $moduleDataSetup
    ) {
        $this->moduleDataSetup = $moduleDataSetup;
    }
​
    /**
     * @inheritdoc
     */
    public function apply()
    {
        /**
         * Fill table directory/country
         */
        $data = [
            ['XX', 'XX', 'XX']
        ];
​
        $columns = ['country_id', 'iso2_code', 'iso3_code'];
        $this->moduleDataSetup->getConnection()->insertArray(
            $this->moduleDataSetup->getTable('directory_country'),
            $columns,
            $data
        );
    }
​
    /**
     * @inheritdoc
     */
    public static function getDependencies()
    {
        return [];
    }
​
    /**
     * @inheritdoc
     */
    public static function getVersion()
    {
        return '0.0.1';
    }
​
    /**
     * @inheritdoc
     */
    public function getAliases()
    {
        return [];
    }
}
```

### ExtraCountries/registration.php

다음은 registration.php 파일의 예입니다. 모듈 등록에 대한 자세한 내용은 개발자 설명서에서 [PHP 개발자 안내서 > 구성 요소 등록](https://developer.adobe.com/commerce/php/development/build/component-registration/)을 참조하십시오.

```php
<?php
use Magento\Framework\Component\ComponentRegistrar;
​
ComponentRegistrar::register(ComponentRegistrar::MODULE, 'VendorName_ExtraCountries', __DIR__);
```

### ExtraCountries/composer.json

다음은 composer.json 파일의 예입니다.

composer.json에 대한 자세한 내용은 개발자 설명서에서 [PHP 개발자 안내서 > composer.json 파일](https://developer.adobe.com/commerce/php/development/build/composer-integration/)을 참조하십시오.

```json
{
    "name": "vendor_name/module-extra-countries",
    "description": "A module that adds extra countries to magento directory",
    "type": "magento2-module",
    "license": [
    ],
    "require": {
        "php": "~7.3.0||~7.4.0",
        "lib-libxml": "*",
        "magento/framework": "*",
        "magento/module-directory": "*"
    },
    "autoload": {
        "files": [
            "registration.php"
        ],
        "psr-4": {
            "VendorName\\ExtraCountries\\": ""
        }
    },
    "config": {
        "sort-packages": true
    }
}
```

## 모듈 설치

모듈을 설치하는 방법은 개발자 설명서에서 [모듈 위치](https://developer.adobe.com/commerce/php/architecture/modules/overview/#module-locations)를 참조하십시오.

모듈 디렉터리가 올바른 위치에 배치되면 `bin/magento setup:upgrade`을(를) 실행하여 데이터 패치를 적용하고 번역 플러그인을 등록합니다.

새 변경 사항이 작동하려면 브라우저 캐시를 정리해야 할 수 있습니다.
