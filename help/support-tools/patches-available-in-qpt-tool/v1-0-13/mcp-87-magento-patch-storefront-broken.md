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

Met de MCP-87 Adobe Commerce-patch is het probleem verholpen waarbij het opnieuw indexeren van catalogi traag verloopt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 is geïnstalleerd.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce on cloud Infrastructure 2.4.0.

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De aandelenindexering van catalogi met grote profielen gaat erg langzaam.

<u>Stappen om te reproduceren:</u>

1. Meld u aan bij het deelvenster Beheer.
1. Navigeren naar: **Producten** > **Catalogus**.
1. Selecteer alle items in het raster Producten.
1. Selecteren **Kenmerken bijwerken** in de vervolgkeuzelijst Handelingen product selecteren. Klikken **Verzenden**.
1. Klikken op **Geavanceerde inventarisatie** op het tabblad Geavanceerde instellingen. Wijzigen **Beschikbaarheid voorraad** tot *In voorraad*. Klikken **Opslaan**.
1. Voer de volledige herindex handmatig uit en voer de volgende opdracht uit vanaf het hoofdniveau: `bin/magento indexer:reindex`

<u>Verwacht resultaat:</u>

De indexeerfunctie van de voorraad wordt snel opnieuw berekend.

<u>Werkelijk resultaat:</u>

De beursindexator is erg langzaam en/of niet volledig.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
