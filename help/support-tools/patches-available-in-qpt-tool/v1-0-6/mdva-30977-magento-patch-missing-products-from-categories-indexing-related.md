---
title: "MDVA-30977: ontbrekende producten uit categorieën, indexeergerelateerd"
description: De patch MDVA-30977 verhelpt de problemen met producten die op pagina's van winkelcategorieën worden weergegeven tijdens herindexering of massale acties met een groot aantal producten. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 is geïnstalleerd. De problemen zullen volgens de planning worden opgelost in Adobe Commerce 2.4.2.
exl-id: 66ec4f53-c01d-4f87-a175-84f44a26f5d3
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# MDVA-30977: ontbrekende producten uit categorieën, indexering in verband hiermee

De patch MDVA-30977 verhelpt de problemen met producten die op pagina&#39;s van winkelcategorieën worden weergegeven tijdens herindexering of massale acties met een groot aantal producten. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 geïnstalleerd is. De problemen zullen volgens de planning worden opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

De patch is gemaakt voor Adobe Commerce op cloud-infrastructuur 2.3.4. Het is ook compatibel met Adobe Commerce op locatie 2.3.4.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Problemen

### Uitgave 1

Het aantal producten dat op de categoriepagina op de winkelpagina wordt weergegeven, verschilt nadat elke pagina tijdens de update van het massaproduct opnieuw is geladen.

<u> Stappen om te reproduceren:</u>

1. Ten minste 30000 producten in twee categorieën maken - ten minste 15000 producten per categorie.
1. Ga naar **Catalogus** > **Producten** in Commerce Admin.
1. Selecteer alle producten in het raster en voer een update voor het massakenmerk uit. Bijvoorbeeld, plaats **Nieuw** = *ja* attribuut.
1. Uitsnijdtaak van Magento tweemaal uitvoeren met de opdracht `bin/magento cron:run` .
1. Rubriekpagina&#39;s vernieuwen in winkelcentrum terwijl Adobe Commerce 30000 producten bijwerkt.

<u> Verwacht resultaat:</u>

Het aantal producten in categorieën is altijd 15000 op elke pagina die van de categorie verfrist.

<u> Ware resultaat:</u>

Het aantal producten in categorieën is verschillend op elke categoriepagina verfrist zich.

### Uitgave 2

Wanneer de volledige herindex van de inventaris wordt uitgevoerd, worden de categoriepagina&#39;s leeg en *wij kunnen geen producten vinden die de selectie* bericht aanpassen wordt getoond.

<u> Stappen om te reproduceren:</u>

1. Configureer Adobe Commerce met Elasticsearch.
1. Voeg een nieuwe website toe.
1. Maak een nieuwe bron en wijs deze toe aan de nieuwe website met behulp van Stock beheren.
1. Maak 30000 configureerbare producten.
1. Wijs alle producten toe aan de nieuwe website en voeg ook inventaris aan de nieuwe inventarisbron toe.
1. Voer een volledige redex uit.
1. De voorraadherindex uitvoeren door `bin/magento indexer:reindex inventory` uit te voeren
1. Blader door een categorie met een groot aantal producten.

<u> Verwacht resultaat:</u>

Categoriepagina&#39;s geven producten weer zoals gewoonlijk tijdens de herindex.

<u> Ware resultaat:</u>

Categoriepagina&#39;s worden leeg tijdens opnieuw indexeren.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
