---
title: Een nieuw land toevoegen aan Adobe Commerce
description: In dit artikel wordt uitgelegd hoe u een land toevoegt dat niet aanwezig is in Adobe Commerce en de Landbibliotheek van Zend. Hiervoor zijn code- en databasewijzigingen vereist die klantaanpassingen volgens de toepasselijke bepalingen van de overeenkomst vormen. De voorbeeldmaterialen die in dit artikel zijn opgenomen, worden zonder enige garantie geleverd. Noch Adoben, noch verbonden entiteiten zijn verplicht om deze materialen te onderhouden, te corrigeren, bij te werken, te wijzigen, te wijzigen of anderszins te ondersteunen. Hier zullen we de grondbeginselen beschrijven van wat er gedaan moet worden om dit te bereiken.
exl-id: af499add-4966-4a3a-972a-62a34c169a1b
feature: Build, Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 0%

---

# Een nieuw land toevoegen aan Adobe Commerce

In dit artikel wordt uitgelegd hoe u een land toevoegt dat niet aanwezig is in Adobe Commerce en de Landbibliotheek van Zend. Hiervoor zijn code- en databasewijzigingen vereist die klantaanpassingen volgens de toepasselijke bepalingen van de overeenkomst vormen. De voorbeeldmaterialen die in dit artikel zijn opgenomen, worden zonder enige garantie geleverd. Noch Adoben, noch verbonden entiteiten zijn verplicht om deze materialen te onderhouden, te corrigeren, bij te werken, te wijzigen, te wijzigen of anderszins te ondersteunen. Hier zullen we de grondbeginselen beschrijven van wat er gedaan moet worden om dit te bereiken.

In dit voorbeeld maken we een nieuwe Adobe Commerce-module met een gegevenspatch die wordt toegepast bij de installatie of upgrade van Adobe Commerce en voegen we een Abstract land toe met de landcode XX bij Adobe Commerce. De [ Folder van Adobe Commerce ](https://developer.adobe.com/commerce/php/module-reference/module-directory/) bouwt een aanvankelijke landlijst en dan gebruikt het Patches van de Opstelling om gebieden aan die lijst toe te voegen. In dit artikel wordt uitgelegd hoe u een nieuwe module maakt die een nieuw land aan de lijst toevoegt. U kunt de code van de bestaande Adobe Commerce Directory-module ter referentie controleren. Dit is omdat de volgende voorbeeldmodule de modulebaan van de Folder voortzet om een lijst van landen en gebieden te bouwen, en delen van de code van de de modulefbeeldingen van de Opstelling van de Folder van Adobe Commerce opnieuw gebruikt.

## Aanbevolen documentatie

U moet vertrouwd zijn met de ontwikkeling van de Adobe Commerce-module om een nieuwe te maken.

Raadpleeg de volgende onderwerpen in de documentatie voor ontwikkelaars voordat u een nieuwe module gaat maken:

* [ PHP Gids van de Ontwikkelaar ](https://developer.adobe.com/commerce/php/development/)
* [ Overzicht van de Module ](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [ creeer een Nieuwe Module ](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/backend-development/create-module)
* [ de configuratiedossiers van de Module ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/module-files)

## Vereiste informatie

Een nieuw land moet in heel Adobe Commerce een unieke naam, land-id, ISO2- en ISO3-code hebben.

## Modulestructuur

In dit voorbeeld gaan we een nieuwe module maken met de naam \&quot;Extracountries\&quot; met de volgende directorystructuur:

(Om meer over de modulestructuur te weten te komen, zie [ Overzicht van de Module ](https://developer.adobe.com/commerce/php/architecture/modules/overview/) in onze ontwikkelaarsdocumentatie).

<pre><ExtraCountries>
 |
 <etc>
 | |
 | config.xml
 | di.xml
 | module.xml
 |
 <Plugin>
 | |
 | <Framework>
 |   |
 |   <Locale>
 |     |
 |     TranslatedListsPlugin.php
 |
 <Setup>
 | |
 | <Patch>
 |   |
 |   <Data>
 |     |
 |     AddDataForAbstractCountry.php
 |
 composer.json
 registration.php</pre>

>[!NOTE]
>
>In elk gedeelte Koptekst van dit artikel worden de bestanden in de sectie Modulestructuur beschreven.

## ExtraCountries/etc/config.xml

Er wordt een nieuwe moduleconfiguratie gedefinieerd in dit XML-bestand. De volgende configuraties en tags kunnen worden bewerkt om de standaardinstellingen voor het nieuwe land aan te passen.

* `allow` - Als u het nieuwe toegevoegde land standaard wilt toevoegen aan de lijst &#39;Landen toestaan&#39;, voegt u de nieuwe landcode toe aan het einde van de `allow` -tag-inhoud. Landcodes worden gescheiden door komma&#39;s. Houd er rekening mee dat met deze tag de gegevens uit het `Directory` moduleconfiguratiebestand *(Directory/etc/config.xml)* `allow` -tag worden overschreven. Daarom herhalen we hier alle codes plus de nieuwe.
* `optional_zip_countries` - Als de postcode voor het nieuwe toegevoegde land optioneel moet zijn, voegt u de landcode toe aan het einde van de inhoud van de `optional_zip_countries` -tag. Landcodes worden gescheiden door komma&#39;s. Houd er rekening mee dat met deze tag de gegevens uit het `Directory` moduleconfiguratiebestand *(Directory/etc/config.xml)* `optional_zip_countries` -tag worden overschreven. Daarom herhalen we hier alle codes plus de nieuwe.
* `eu_countries` - Als het nieuwe toegevoegde land standaard deel moet uitmaken van de lijst met EU-landen, voegt u de landcode toe aan het einde van de inhoud van de tag `eu_countries` . Landcodes worden gescheiden door komma&#39;s. Houd er rekening mee dat met deze tag de gegevens uit het `Store` moduleconfiguratiebestand *worden overschreven (\_Store/etc/config.xml\_)* `eu_countries` -tag. Daarom herhalen we hier alle codes plus de nieuwe.
* `config.xml` voorbeeld van bestand

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

Voor meer informatie over de dossiers van de moduleconfiguratie, zie [ Gids van de Ontwikkelaar PHP > de dossiers van Configuraties ](https://developer.adobe.com/commerce/php/development/build/required-configuration-files/) in onze ontwikkelaarsdocumentatie bepalen.

Deze wijzigingen zijn optioneel en hebben alleen invloed op het standaardlidmaatschap van het nieuwe land op de lijsten &quot;Allow countries&quot;, &quot;Zip/Postal Code is Optional for&quot; en &quot;European Union countries&quot;. Als dit dossier van de modulestructuur wordt overgeslagen, zal een nieuw land nog worden toegevoegd, maar het zal manueel moeten worden gevormd bij **Admin** > **Opslag** > *Montages* > **Configuratie** > **Algemene** > **de montagespagina van de Opties van het Land 11}.**

### ExtraCountries/etc/di.xml

Het bestand `di.xml` configureert welke afhankelijkheden door objectbeheer worden geïnjecteerd. Zie <a> Gids van de Ontwikkelaar PHP > di.xml </a> in onze ontwikkelaarsdocumentatie voor meer details over `di.xml`.

In ons voorbeeld moeten we een `_TranslatedListsPlugin_` registreren die de nieuw geïntroduceerde landcodes omzet in een volledige landnaam als er geen codes aanwezig zijn in de lokalisatiegegevens van de landbibliotheek van Zend.

`di.xml` voorbeeld

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

In het dossier van de moduleregistratie moeten wij het gebiedsdeel voor de module &quot;van de Folder van Adobe Commerce&quot;specificeren ervoor zorgen dat de module &quot;Extra Landen&quot;na de module van de Folder zal worden geregistreerd en worden uitgevoerd.

Zie [ het Leiden modulegebiedsdelen ](https://developer.adobe.com/commerce/php/architecture/modules/dependencies/#managing-module-dependencies) in onze ontwikkelaarsdocumentatie voor meer informatie over modulegebiedsdelen.

`module.xml` voorbeeld

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

In de insteekmodule `aroundGetCountryTranslation()` moeten we een landcode omzetten in een volledige landnaam. Dit is een vereiste stap voor landen die geen volledige naam hebben die is gekoppeld aan een nieuwe landcode in de Landbibliotheek van Zend.

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

Deze gegevenspatch wordt uitgevoerd tijdens de installatie/upgrade van Adobe Commerce en voegt een nieuwe landrecord toe aan de database.

Zie [ gegevens en schemapatches ontwikkelen ](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) in onze ontwikkelaarsdocumentatie voor meer informatie over gegevenspatches.

In het onderstaande voorbeeld ziet u dat de `$data` -array van de methode `apply()` landinstellings-id-, ISO2- en ISO3-code voor het nieuwe land bevat en dat deze gegevens in de database worden ingevoegd.

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

Dit is een voorbeeld van het bestand registration.php. Om meer over moduleregistratie te weten te komen, zie [ Gids van de Ontwikkelaar PHP > registreer uw component ](https://developer.adobe.com/commerce/php/development/build/component-registration/) in onze ontwikkelaarsdocumentatie.

```php
<?php
use Magento\Framework\Component\ComponentRegistrar;
​
ComponentRegistrar::register(ComponentRegistrar::MODULE, 'VendorName_ExtraCountries', __DIR__);
```

### ExtraCountries/composer.json

Dit is een voorbeeld van het bestand composer.json.

Om meer over composer.json te weten te komen, zie [ Gids van de Ontwikkelaar PHP > het composer.json- dossier ](https://developer.adobe.com/commerce/php/development/build/composer-integration/) in onze ontwikkelaarsdocumentatie.

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

## Module-installatie

Om te weten te komen hoe te om de module te installeren, zie {de plaatsen van de 0} Module ](https://developer.adobe.com/commerce/php/architecture/modules/overview/#module-locations) in onze ontwikkelaarsdocumentatie.[

Nadat de moduledirectory op de juiste locatie is geplaatst, voert u `bin/magento setup:upgrade` uit om de gegevenspatches toe te passen en de vertaalinsteekmodule te registreren.

Mogelijk moet u de cache van de browser opschonen om de nieuwe wijzigingen door te voeren.
