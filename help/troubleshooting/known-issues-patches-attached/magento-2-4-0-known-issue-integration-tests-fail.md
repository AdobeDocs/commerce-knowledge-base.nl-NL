---
title: "Bekende kwestie Adobe Commerce 2.4.0: integratietests mislukken"
description: Dit artikel bevat een patch voor het Adobe Commerce 2.4.0-probleem waarbij integratietests mislukken omdat de verklaring van "Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()" niet compatibel is met PHPUnit 9, dat wordt gebruikt voor 2.4.0.
exl-id: 8e0ca2da-81d9-4561-a009-593240f46e41
feature: Integration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Bekend probleem van Adobe Commerce 2.4.0: integratietests mislukken

Dit artikel bevat een patch voor het Adobe Commerce 2.4.0-probleem waarbij integratietests mislukken omdat de declaratie van `Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()` niet compatibel is met PHPUnit 9, dat wordt gebruikt voor 2.4.0.

## Betrokken producten en versies

* Adobe Commerce over cloudinfrastructuur 2.4.0
* Adobe Commerce op locatie 2.4.0

## Probleem

<u> Stappen om te reproduceren </u>

Voer 2.4.0 integratietests uit.

<u> Verwacht resultaat </u>

Test geslaagd.

<u> Werkelijk resultaat </u>

*PHP Onherstelbare fout: Verklaring van Dotdigitalgroup\\Email\\Test\\Integration\\Model\\Sync\\Importer\\ImporterFailedTest::setUp() moet compatibel zijn met PHPUnit\\Framework\\TestCase::setUp(): void in /var/www/vendor/dotmailer/dotmailer-magento2-extension/Test/Integration/Model/Sync/Importer/ImporterFailedTest.php op regel 36*

## Oplossing

Pas de patch toe die in dit artikel is opgenomen.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[BUNDLE-2684-composer.patch](assets/BUNDLE-2684-composer.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce over cloudinfrastructuur 2.4.0
* Adobe Commerce op locatie 2.4.0

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze basis van steunkennis voor instructies wordt verstrekt.

## Bijgevoegde bestanden
