---
title: Trage prestaties, langzame en langlopende bekers
description: In dit artikel wordt beschreven hoe u problemen met de siteprestaties kunt oplossen en hoe u de werking en het vastlopen van crons kunt vertragen die worden veroorzaakt door platte tabellen en indexeerders die zijn ingeschakeld.
exl-id: a78ca3c3-85b4-40a1-a693-4703dd3ef4b5
feature: Best Practices, Cache, Categories, Catalog Management
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Trage prestaties, langzame en langlopende bekers

>[!WARNING]
>
>Aangezien bepaalde extensies alleen werken met platte tabellen, is er bij elke Adobe Commerce-versie een risico als u platte tabellen uitschakelt. Als u weet dat u extensies hebt die gebruikmaken van Platte catalogusindexen, moet u dat wellicht in overweging nemen wanneer u die waarden instelt op &quot; *Nee* &quot;.

In dit artikel wordt beschreven hoe u problemen met de prestaties van de site kunt oplossen en hoe u de werking van de crons kunt vertragen en vastlopen die worden veroorzaakt door [vlakke tabellen en indexeertekens](https://docs.magento.com/m2/ce/user_guide/catalog/catalog-flat.html) nadat deze is ingeschakeld.

BETROKKEN PRODUCTEN EN VERSIES

* Adobe Commerce op cloudinfrastructuur 2.1.x en hoger
* Adobe Commerce op locatie 2.1.x en hoger
* Magento Open Source 2.1.x en hoger

## Probleem

Vlakke indexen kunnen:

* Zware problemen met het laden van SQL en de prestaties van de site.
* Langlopende en geplakte manen.

## Oorzaak

Vlakke tabellen en indexeertekens ingeschakeld.

## Oplossing {#solution}

Vanaf Adobe Commerce en Magento Open Source 2.1.x en hoger is het gebruik van een platte catalogus niet langer de beste werkwijze en wordt het gebruik ervan afgeraden. Het is bekend dat voortdurend gebruik van deze functie prestatievermindering en andere indexeringsproblemen kan veroorzaken. De vlakke catalogus uitschakelen:

1. Navigeer in Beheer naar **Winkels** > **Instellingen** > **Configuratie**.
1. In het linkerdeelvenster onder **Catalogus** , kiest u **Catalogus**.
1. Breid uit **Storefront** en voer de volgende handelingen uit:
   * Set **Vlakke catalogus gebruiken** tot *Nee*.
   * Set **Plat catalogusproduct gebruiken** tot *Nee*.
1. Klik op **Config opslaan**. Vernieuw vervolgens de cache wanneer hierom wordt gevraagd.
1. Cache leegmaken door uit te voeren `php bin/magento cache:flush`.

Als u het dialoogvenster **Vlakke catalogus gebruiken** en **Plat catalogusproduct gebruiken** tot *Nee* omdat de opties grijs worden weergegeven, schakelt u vlakke indexen uit in `app/etc/config.php`:

1. Voer deze opdracht uit om ervoor te zorgen dat alle indexen zijn ingesteld op Bijwerken volgens schema: `php bin/magento indexer:set-mode schedule`.
1. Bewerken `app/etc/config.php` en zoek de lijnen met `flat_catalog_product` en `flat_catalog_category` - verander hen van 1 in 0 om hen onbruikbaar te maken.
1. De opdracht uitvoeren `php bin/magento app:config:import`
1. Voer deze opdracht uit om te bevestigen dat de vlakke indexen zijn uitgeschakeld: `php        bin/magento indexer:status`.
1. Cache leegmaken door uit te voeren `php bin/magento cache:flush`.

## Gerelateerde informatie

[Vastgezette Adobe Commerce-snijtaken handmatig opnieuw instellen op Cloud](/help/how-to/general/reset-stuck-magento-cron-jobs-manually-on-cloud.md) in onze kennisbasis voor ondersteuning.
