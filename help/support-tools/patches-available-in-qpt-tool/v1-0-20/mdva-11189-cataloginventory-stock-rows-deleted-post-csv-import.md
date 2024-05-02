---
title: "MDVA-11189: catalog voorraad_rows deleted post CSV import"
description: De patch MDVA-11189 Adobe Commerce verhelpt het probleem wanneer na het importeren van een .csv-bestand om de productvoorraad bij te werken, rijen uit de tabel 'catalogvoorraad_voorraad' worden verwijderd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MDVA-1189. De kwestie is opgelost in Adobe Commerce 2.3.5.
exl-id: 84e1979c-826c-4c01-b0c7-8054bb4b23f0
feature: Catalog Management, Data Import/Export, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# MDVA-11189: catalogusvoorraad rijen verwijderd na CSV-import

De MDVA-11189 Adobe Commerce-patch verhelpt het probleem bij het importeren van een .csv-bestand om de productvoorraad bij te werken, rijen van de `cataloginventory_stock` de tabel wordt verwijderd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MDVA-1189. De kwestie is opgelost in Adobe Commerce 2.3.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over wolkeninfrastructuur 2.2.3

**Compatibel met Adobe Commerce-versies:** Adobe Commerce (alle implementatiemethoden) 2.3.0-2.3.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het probleem bij het importeren van een `.csv` om productvoorraad bij te werken, rijen van `cataloginventory_stock` de tabel wordt verwijderd.

<u>Stappen om te reproduceren:</u>

1. Voer in de database de volgende MySQL-opdracht uit: `select count(*) from cataloginventory_stock_status;`
1. Noteer het aantal rijen.
1. Stel de tab als volgt in: `* * * * * /usr/bin/php <path to installation>/bin/magento cron:run  | grep -v "Ran jobs by schedule" >> <path to installation>/var/log/cron.log 2>&1`
1. Ga naar het deelvenster Beheer in **Systeem** > **Gereedschappen** > **Indexbeheer**.
1. Indexeerders instellen op *Bijwerken volgens schema.*
1. Ga naar **Systeem** > *Gegevensoverdracht* > **Exporteren**.
1. Set **Type entiteit** gelijk aan *Producten* > **Doorgaan**.
1. Opgeslagen bestanden openen `.csv` Bestand > Alle kolommen verwijderen behalve SKU en QTY.
1. Werk de hoeveelheid voor alle producten bij tot 150.
1. Sla de `.csv` bestand.
1. Ga naar **Systeem** > *Gegevensoverdracht* > **Importeren** .
1. Stel de volgende waarden in:
   1. Type entiteit: *Producten*
   1. Gedrag bij importeren: *Toevoegen/bijwerken*
   1. Laat alle andere waarden standaard staan.
   1. Kies Bestand om de productspreadsheet van de catalogus te selecteren.
1. Klikken **Gegevens controleren** > **Importeren**. Laat 5-10 minuten passeren.
1. Voer in de database de volgende MySQL-opdracht uit:
   `select count(*) from cataloginventory_stock_status;`

<u>Werkelijk resultaat:</u>

Het aantal rijen in `cataloginventory_stock` wordt verlaagd na de CSV-invoer om de voorraad bij te werken.

<u>Verwacht resultaat:</u>

Het aantal rijen in `cataloginventory_stock` moeten na de CSV-invoer gelijk blijven om de voorraad bij te werken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
