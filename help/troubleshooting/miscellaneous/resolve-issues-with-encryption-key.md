---
title: Problemen met coderingssleutel oplossen
description: Dit artikel praat over hoe te om de kwesties te bevestigen die door de encryptiesleutel worden veroorzaakt die niet samen met de stortplaats van DB aan het andere milieu wordt bewogen.
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: bee0263da487399ab07bf9158c4d60ab316d6ea1
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Problemen met coderingssleutel oplossen

Dit artikel praat over hoe te om de kwesties te bevestigen die door de encryptiesleutel worden veroorzaakt die niet samen met de stortplaats van DB aan het andere milieu wordt bewogen.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x

## Probleem

Nadat u een [databasedruk](/help/how-to/general/create-database-dump-on-cloud.md) van Productie tot Staging/Integratie-omgevingen, de opgeslagen creditcardnummers lijken onjuist en/of betalingen mislukken voor betalingsintegraties die het gebruik van zakelijke gegevens vereisen.

## Oorzaak

De encryptiesleutel die wordt gebruikt om gevoelige gegevens, zoals creditcardaantallen en commerciële geloofsbrieven te coderen, wordt niet opgeslagen in het gegevensbestand, en wordt daarom niet overgebracht naar andere milieu na de invoer/de uitvoer van de gegevensbestandstortplaats.

## Oplossing

U moet de encryptiesleutel van het bronmilieu kopiëren en het toevoegen aan het bestemmingsmilieu.

De coderingssleutel kopiëren:

1. SSH aan uw project dat de bron voor de gegevensbestandstortplaats was, zoals die in wordt beschreven [SSH naar omgeving](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) in onze ontwikkelaarsdocumentatie.
1. Openen `app/etc/env.php` in een teksteditor.
1. De waarde kopiëren van `key` for `crypt`.

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

Om de belangrijkste waarde voor het bestemmingsproject te plaatsen:

1. Open de [Cloud Console](https://console.adobecommerce.com) en zoek uw project.
1. Stel de waarde van de optie [CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) (in onze ontwikkelaarsdocumentatie), zoals beschreven in [Uw project configureren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) in onze ontwikkelaarsdocumentatie. Dit zal het plaatsingsproces teweegbrengen en `CRYPT_KEY` wordt overschreven in het dialoogvenster `app/etc/env.php` bestand bij elke implementatie.

U kunt desgewenst de coderingssleutel handmatig overschrijven in het dialoogvenster `app/etc/env.php` bestand:

1. SSH aan het bestemmingsmilieu.
1. Openen `app/etc/env.php` in een teksteditor.
1. De gekopieerde gegevens plakken als de `key` waarde voor `crypt`.
1. Bewerkte opslaan `env.php`.
1. Cache opschonen in de doelomgeving door het programma uit te voeren `bin/magento cache:clean` of in Commerce Admin onder **Systeem** > **Gereedschappen** > **Cachebeheer**.
