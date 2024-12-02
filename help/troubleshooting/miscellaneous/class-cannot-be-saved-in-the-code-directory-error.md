---
title: 'Fout: "Klasse kan niet worden opgeslagen in de codedirectory"'
description: In dit artikel wordt beschreven hoe u het probleem kunt verhelpen waarbij de manier waarop u afhankelijkheden hebt opgegeven, voorkomt dat klassen automatisch worden gegenereerd tijdens het uitvoeren van de functie. Bovendien wordt het foutbericht *"Klasse kan niet worden opgeslagen in de gegenereerde/codedirectory"* weergegeven.
exl-id: e2c00d4d-31c3-4446-a317-a8ac92c707d5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Fout: &quot;Klasse kan niet worden opgeslagen in de codedirectory&quot;

Dit artikel beschrijft hoe te om de kwestie te bevestigen waar de manier u gebiedsdelen specificeerde voorkomt klassen worden auto-geproduceerd op de vlucht, en u krijgt *&quot;Klasse kan niet in de geproduceerde/codefolder worden bewaard&quot;* foutenmelding.

## Betrokken producten en versies

* Adobe Commerce on cloud Infrastructure 2.2.0 of hoger

## Probleem

<u> Stappen om te reproduceren </u>

1. In uw lokale milieu, schrijf een douaneklasse met een afhankelijkheid van de auto-geproduceerde klasse.
1. Voer het scenario uit, waarbij de aangepaste klasse wordt geactiveerd, en zie hoe het werkt.
1. Leg uw wijzigingen vast en duw op de integratieomgeving. Dit zou het plaatsingsproces teweegbrengen. Implementatie is geslaagd.
1. In het [ integratiemilieu ](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md), stel het scenario in werking waar uw douaneklasse wordt teweeggebracht.

<u> Verwacht resultaat </u>

Alles werkt correct, net als in uw lokale omgeving.

<u> Werkelijk resultaat </u>

Fout bij het foutbericht dat aangeeft dat uw klasse niet in de map `generated/code` kan worden opgeslagen.

## Oorzaak

De oorzaak van het probleem is dat de klasse waarop u gebiedsdeel hebt, niet tijdens de plaatsing wordt geproduceerd, en niet later op de vlucht kan worden geproduceerd wanneer de klasse wordt teweeggebracht, omdat de `generated/code` folder niet voor het schrijven na plaatsing is voltooid.

Er zijn twee belangrijke redenen waarom dit zou kunnen gebeuren:

* Case 1: De klasse met afhankelijkheden van automatisch gegenereerde klassen bevindt zich in het ingangspunt (zoals `index.php` ), dat tijdens de implementatie niet is gescand op afhankelijkheden.
* Geval 2: De afhankelijkheid van de auto-geproduceerde klasse wordt gespecificeerd direct (vergelijk aan het geadviseerde gebruik van aannemer om gebiedsdeel te verklaren).

## Oplossing

Een algemene oplossing voor beide gevallen is het maken van een echte fabriek in plaats van de automatisch gegenereerde klasse.

Of er is een specifieke oplossing voor elk geval.

### Specifieke oplossing voor geval 1

Verplaats uw klassecode van het ingangspunt naar een afzonderlijke module en gebruik deze vervolgens in het ingangspunt.

<u> Voorbeeld </u>

Oorspronkelijke code in, bijvoorbeeld, `index2.php` :

```php
<?php
use YourVendor\SomeModule\Model\GeneratedFactory;

require realpath(__DIR__) . '/../app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);

class SomeClass
{
    private $generatedFactory;

    public function __construct(GeneratedFactory $generatedFactory)
    {
        $this->generatedFactory = $generatedFactory;
    }

// Some code here...
}

$someObject = $bootstrap->getObjectManager()->create(SomeClass::class);

// There is some code that uses $someObject
```

U moet de volgende stappen uitvoeren:

1. Verplaats de klassedefinitie naar `app/code/YourVendor/YourModule` :

   ```php
      <?php
       namespace YourVendor\YourModule;
       use YourVendor\YourModule\Model\GeneratedFactory;
       class YourClass
       {
           private $generatedFactory;
   
           public function __construct(GeneratedFactory $generatedFactory)
           {
               $this->generatedFactory = $generatedFactory;
           }
       // Some code here...
       }
   ```

1. Bewerk het ingangspunt `my_api/index.php` zodat het er als volgt uitziet:

   ```php
     <?php
     use YourVendor\YourModule\YourClass;
         require realpath(__DIR__) . '/../app/bootstrap.php';
         $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
         $someObject = $bootstrap->getObjectManager()->create(YourClass::class);
     // Some code using $someObject
   ```

### Specifieke oplossing voor geval 2

Afhankelijkheidsdeclaratie verplaatsen naar de constructor.

<u> Voorbeeld </u>

Oorspronkelijke klassendeclaratie:

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\SomeModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam)
    {
        $this--->someParam = $someParam;
        $this->generatedFactory = ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

U moet de constructor als volgt wijzigen:

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\YourModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam, GeneratedFactory $generatedFactory = null)
    {
        $this->someParam = $someParam;
        $this->generatedFactory = $generatedFactory ?: ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

## Gerelateerde lezing

* [ generatie van de Code ](https://developer.adobe.com/commerce/php/development/components/code-generation/) in onze ontwikkelaarsdocumentatie.
