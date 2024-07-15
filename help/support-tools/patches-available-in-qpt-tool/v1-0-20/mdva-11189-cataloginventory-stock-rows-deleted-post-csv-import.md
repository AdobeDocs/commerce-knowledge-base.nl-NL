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

De MDVA-11189 Adobe Commerce-patch verhelpt het probleem wanneer na het importeren van een .csv-bestand om de productvoorraad bij te werken, rijen uit de `cataloginventory_stock` -tabel worden verwijderd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 geïnstalleerd is. De patch-id is MDVA-1189. De kwestie is opgelost in Adobe Commerce 2.3.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.2.3

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce (alle plaatsingsmethodes) 2.3.0-2.3.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Hiermee wordt het probleem verholpen wanneer na het importeren van een `.csv` om de productvoorraad bij te werken, rijen uit de tabel `cataloginventory_stock` worden verwijderd.

<u> Stappen om te reproduceren:</u>

1. Voer in de database de volgende MySQL-opdracht uit: `select count(*) from cataloginventory_stock_status;`
1. Noteer het aantal rijen.
1. Stel de tab als volgt in: `* * * * * /usr/bin/php <path to installation>/bin/magento cron:run  | grep -v "Ran jobs by schedule" >> <path to installation>/var/log/cron.log 2>&1`
1. Ga naar het Admin paneel in **Systeem** > **Hulpmiddelen** > **het Beheer van de Index**.
1. Plaats indexeerders aan *Update door Programma.*
1. Ga naar **Systeem** > *Overdracht van Gegevens* > **Uitvoer**.
1. Plaats **Type van Entiteit** gelijk aan *Producten* > **gaat** verder.
1. Open het opgeslagen `.csv` -bestand > Alle kolommen verwijderen behalve SKU en QTY.
1. Werk de hoeveelheid voor alle producten bij tot 150.
1. Sla het `.csv` -bestand op.
1. Ga naar **Systeem** > *Overdracht van Gegevens* > **de Invoer**.
1. Stel de volgende waarden in:
   1. Type van entiteit: *Producten*
   1. Het Gedrag van de invoer: *voeg/Update* toe
   1. Laat alle andere waarden standaard staan.
   1. Kies Bestand om de productspreadsheet van de catalogus te selecteren.
1. Klik **Gegevens van de Controle** > **de Invoer**. Laat 5-10 minuten passeren.
1. Voer in de database de volgende MySQL-opdracht uit:
   `select count(*) from cataloginventory_stock_status;`

<u> Ware resultaat:</u>

Het aantal rijen in `cataloginventory_stock` wordt verlaagd nadat de CSV-bestanden zijn geïmporteerd om de bestanden bij te werken.

<u> Verwacht resultaat:</u>

Het aantal rijen in `cataloginventory_stock` moet gelijk blijven na het importeren van de CSV om de voorraad bij te werken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
