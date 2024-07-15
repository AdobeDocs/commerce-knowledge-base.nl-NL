---
title: 'MCP-87 Adobe Commerce patch: storefront broken'
description: Met de MCP-87 Adobe Commerce-patch is het probleem verholpen waarbij het opnieuw indexeren van catalogi traag verloopt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 is geïnstalleerd.
exl-id: 048b2764-6bbf-4a02-9a0a-dbea4e48f92a
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# MCP-87 Adobe Commerce patch: storefront broken

Met de MCP-87 Adobe Commerce-patch is het probleem verholpen waarbij het opnieuw indexeren van catalogi traag verloopt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 geïnstalleerd is.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce on cloud Infrastructure 2.4.0.

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De aandelenindexering van catalogi met grote profielen gaat erg langzaam.

<u> Stappen om te reproduceren:</u>

1. Meld u aan bij het deelvenster Beheer.
1. Navigeer aan: **Producten** > **Catalogus**.
1. Selecteer alle items in het raster Producten.
1. Selecteer **Attributen van de Update** in de Uitgezochte drop-down lijst van de Acties van het Product. Klik **voorleggen**.
1. Klik op **Geavanceerde Inventaris** van de Geavanceerde Montages tabel. De Beschikbaarheid van de Voorraad van de verandering **** aan *in Voorraad*. Klik **sparen**.
1. Voer de volledige herindex handmatig uit en voer de volgende opdracht uit vanaf het hoofdniveau: `bin/magento indexer:reindex`

<u> Verwacht resultaat:</u>

De indexeerfunctie van de voorraad wordt snel opnieuw berekend.

<u> Ware resultaat:</u>

De beursindexator is erg langzaam en/of niet volledig.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
