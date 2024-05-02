---
title: "MDVA-24201: Catalogusprijsregels werken niet"
description: De patch MDVA-24201 lost het probleem op waar de actieve prijsregels voor catalogi in de database niet van toepassing zijn op de frontend.
exl-id: ae541c40-403a-46e9-a486-2a1e8991f05a
feature: Catalog Management, Categories, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-24201: Catalogusprijsregels werken niet

De patch MDVA-24201 lost het probleem op waar de actieve prijsregels voor catalogi in de database niet van toepassing zijn op de frontend.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.3.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over wolkeninfrastructuur 2.3.3

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Vereiste</u>:

Installeer een nieuw exemplaar van het Magento met steekproefgegevens.

<u>Stappen om te reproduceren</u>:

1. Aanmelden bij **Deelvenster Beheer** > **Marketing** > **Catalogusprijsregel** > **Nieuwe regel toevoegen**, stel de volgende instellingen in:
   1. Stel de **Naam van regel**.
   1. Set **Actief** = *Nee.*
   1. Voorwaarden instellen: **Categorie** = *4*. (Voorbeeld: tags)
   1. Handelingen instellen:
      1. Set **Toepassen als**   **percentage van het origineel**.
      1. Set **Korting** = *10*.
      1. Sla het bestand op en ga verder met het bewerken.
   1. Klikken op **Nieuwe update plannen**:
      * Stel de **Naam van regel**.
      * Set **Actief** = *Ja*.
      * Opslaan.
1. Ga naar de achtergrond en voer uit:

   `php    bin/magento cron:run`

<u>Verwachte resultaten</u>:

De prijzen van de producten van categorie 4 &quot;Bags&quot; moeten worden verlaagd met 10% van de oorspronkelijke prijs, zoals bepaald in de regel inzake catalogusprijzen, zoals verwacht.

<u>Werkelijke resultaten</u>:

Er vinden geen prijswijzigingen plaats, ook al is de regel voor catalogusprijzen actief.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
