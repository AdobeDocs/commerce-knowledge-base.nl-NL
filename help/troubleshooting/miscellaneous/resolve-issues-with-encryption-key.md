---
title: Problemen met coderingssleutel oplossen
description: Dit artikel praat over hoe te om de kwesties te bevestigen die door de encryptiesleutel worden veroorzaakt die niet samen met de stortplaats van DB aan het andere milieu wordt bewogen.
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: 0458b37e2af4c9ad2ec92a1fdd6844ef222ef84a
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Problemen met coderingssleutel oplossen

Dit artikel praat over hoe te om de kwesties te bevestigen die door de encryptiesleutel worden veroorzaakt die niet samen met de stortplaats van DB aan het andere milieu wordt bewogen.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur 2.4.x

## Probleem

Na het invoeren van a [ gegevensbestandstortplaats ](/help/how-to/general/create-database-dump-on-cloud.md) van Productie aan het Opvoeren/de milieu&#39;s van de Integratie, verschijnen de bewaarde creditcardaantallen verkeerd en/of de betalingen ontbreken voor betalingsintegratie die gebruik van koopvaardijgeloofsbrieven vereisen.

## Oorzaak

De encryptiesleutel die wordt gebruikt om gevoelige gegevens, zoals creditcardaantallen en commerciële geloofsbrieven te coderen, wordt niet opgeslagen in het gegevensbestand, en wordt daarom niet overgebracht naar andere milieu na de invoer/de uitvoer van de gegevensbestandstortplaats.

## Oplossing

U moet de encryptiesleutel van het bronmilieu kopiëren en het toevoegen aan het bestemmingsmilieu.

De coderingssleutel kopiëren:

1. SSH aan uw project dat de bron voor de gegevensbestandstortplaats was, zoals die in [ SSH aan milieu ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) in onze ontwikkelaarsdocumentatie wordt beschreven.
1. Open `app/etc/env.php` in een teksteditor.
1. Kopieer de waarde van `key` for `crypt` .

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

Om de belangrijkste waarde voor het bestemmingsproject te plaatsen:

1. Open de [ Console van de Wolk ](https://console.adobecommerce.com) en bepaal de plaats van uw project.
1. Plaats de waarde van [ CRYPT \_KEY ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) (in onze ontwikkelaarsdocumentatie) variabele, zoals die in [ wordt beschreven uw project ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) in onze ontwikkelaarsdocumentatie vormt. Hierdoor wordt het implementatieproces geactiveerd en wordt `CRYPT_KEY` bij elke implementatie overschreven in het `app/etc/env.php` -bestand.

U kunt desgewenst de coderingssleutel in het `app/etc/env.php` -bestand handmatig overschrijven:

1. SSH aan het bestemmingsmilieu.
1. Open `app/etc/env.php` in een teksteditor.
1. Plak de gekopieerde gegevens als de `key` -waarde voor `crypt` .
1. Sla het bewerkte bestand op `env.php` .
1. Het schone geheime voorgeheugen op het bestemmingsmilieu door `bin/magento cache:clean` of in Commerce Admin in werking te stellen onder **Systeem** > **Hulpmiddelen** > **Beheer van het Geheime voorgeheugen**.
