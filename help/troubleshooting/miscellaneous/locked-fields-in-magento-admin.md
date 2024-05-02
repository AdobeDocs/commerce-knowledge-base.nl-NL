---
title: Vergrendelde velden in Commerce Admin
description: Dit artikel biedt een oplossing voor het geval dat u geen velden in Commerce Admin kunt wijzigen.
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Vergrendelde velden in Commerce Admin

Dit artikel biedt een oplossing voor het geval dat u geen velden in Commerce Admin kunt wijzigen.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.3.x, 2.4.x
* Adobe Commerce op cloud-infrastructuur 2.3.x, 2.4.x

## Probleem

Nadat u een wijziging in uw configuratie hebt opgeslagen in `app/etc/env.php` of `app/etc/config.php`kunt u de instelling in Beheer niet wijzigen.

<u>Stappen om te reproduceren</u>:

Opmerking: dit is een voorbeeld. De uitgave kan van invloed zijn op alle configuraties die zijn opgeslagen.

1. De handelaar bewaart hun geloofsbrieven van leveringsmethodes gebruikend het volgende bevel in de terminal: `./vendor/bin/ece-tools config:dump`. Hiermee worden de gegevens opgeslagen in het dialoogvenster `app/etc/env.php` bestand.
1. De handelaar probeert dan om de geloofsbrieven later te veranderen.

<u>Verwachte resultaten</u>:

De handelaar kan de waarden in de Admin gebiedsmontages plaatsen en hen bewaren.

<u>Werkelijke resultaten</u>:

De velden in Beheer zijn vergrendeld of de waarden kunnen worden gewijzigd, maar worden niet opgeslagen in Beheer.

## Oorzaak

Wanneer de configuratie wordt opgeslagen naar `env.php` of `config.php`kunt u de instelling in Beheer niet wijzigen. Als u het bewerken van de instelling wilt toestaan, moet u de configuratie verwijderen uit `env.php` of `config.php`.

## Oplossing

Zorg ervoor dat de configuratie niet is bewaard aan `app/etc/env.php` of `app/etc/config.php`. Voer de volgende stappen uit als het bestand is opgeslagen:

* `config.php` - Verwijder de instelling en wijzig de implementatie.
* `env.php` - Wijzig dit rechtstreeks op de server en verwijder de instelling en voer vervolgens uit `bin/magento app:config:import`.

## Verwante lezing

* [De configuratie exporteren](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-export.html#sensitive-or-system-specific-settings) in onze ontwikkelaarsdocumentatie.
* [Configuratiewaarden instellen](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-set.html#config-cli-config-set) in onze ontwikkelaarsdocumentatie.
* [Adobe Commerce op cloudinfrastructuur: implementatiedowntime verminderen met configuratiebeheer](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) in onze kennisbasis voor ondersteuning.
