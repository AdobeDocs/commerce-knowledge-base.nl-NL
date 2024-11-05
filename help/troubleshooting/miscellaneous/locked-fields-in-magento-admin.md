---
title: Vergrendelde (grijs weergegeven) velden in Commerce Admin
description: Dit artikel biedt een oplossing voor het geval dat u geen velden in Commerce Admin kunt wijzigen.
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: bc800397a3c0c3a86eb717db60e445e13b299688
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Vergrendelde (grijs weergegeven) velden in Commerce Admin

Dit artikel biedt een oplossing voor het probleem wanneer u vergrendelde (grijze) velden in Commerce Admin niet kunt wijzigen.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.3.x, 2.4.x
* Adobe Commerce op cloud-infrastructuur 2.3.x, 2.4.x

## Probleem

Nadat u een wijziging in uw configuratie in `app/etc/env.php` of `app/etc/config.php` hebt opgeslagen, kunt u de instelling niet meer wijzigen in Beheer.

<u> Stappen om </u> te reproduceren:

Opmerking: dit is een voorbeeld. De uitgave kan van invloed zijn op alle configuraties die zijn opgeslagen.

1. De handelaar bewaart hun geloofsbrieven van leveringsmethodes gebruikend het volgende bevel in de terminal: `./vendor/bin/ece-tools config:dump`. Hiermee worden de gegevens in het `app/etc/env.php` -bestand opgeslagen.
1. De handelaar probeert dan om de geloofsbrieven later te veranderen.

<u> Verwachte resultaten </u>:

De handelaar kan de waarden in de Admin gebiedsmontages plaatsen en hen bewaren.

<u> Ware resultaten </u>:

De velden in Beheer zijn vergrendeld of de waarden kunnen worden gewijzigd, maar worden niet opgeslagen in Beheer.

## Oorzaak

Wanneer de configuratie wordt opgeslagen in `env.php` of `config.php` , kunt u de instelling niet wijzigen in de beheerfunctie. Als u het bewerken van de instelling wilt toestaan, moet u de configuratie verwijderen uit `env.php` of `config.php` .

## Oplossing

Controleer of de configuratie niet is opgeslagen in `app/etc/env.php` of `app/etc/config.php` . Voer de volgende stappen uit als het bestand is opgeslagen:

* `config.php` - Verwijder de instelling en herimplementeer deze.
* `env.php` - Wijzig dit rechtstreeks op de server en verwijder de instelling en voer `bin/magento app:config:import` uit.

## Verwante lezing

* [ voer de Configuratie ](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-export.html#sensitive-or-system-specific-settings) in onze ontwikkelaarsdocumentatie uit.
* [ plaats de waarden van de Configuratie ](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-set.html#config-cli-config-set) in onze ontwikkelaarsdocumentatie.
* [ Adobe Commerce op wolkeninfrastructuur: verminder plaatsingsonderbreking met het Beheer van de Configuratie ](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) in onze steun kennisbasis.
