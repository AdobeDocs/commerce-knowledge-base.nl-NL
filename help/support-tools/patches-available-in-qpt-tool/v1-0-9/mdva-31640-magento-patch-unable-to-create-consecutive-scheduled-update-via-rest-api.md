---
title: 'MDVA-31640 patch: unable to create sequence scheduled update via REST API'
description: De MDVA-31640-patch verhelpt het probleem dat er geen nieuwe geplande update voor de speciale prijs kan worden gemaakt voor meerdere winkels die gebruikmaken van REST API, als de begindatum van de update samenvalt met de einddatum van de vorige bestaande update. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 8d91db3d-7c94-4757-8087-4cf53cad81e7
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-31640-patch: kan geen opeenvolgende geplande update maken via REST API

De MDVA-31640-patch verhelpt het probleem dat er geen nieuwe geplande update voor de speciale prijs kan worden gemaakt voor meerdere winkels die gebruikmaken van REST API, als de begindatum van de update samenvalt met de einddatum van de vorige bestaande update. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard werd gecreeerd voor versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.1 - 2.3.5-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Hiermee wordt het probleem verholpen waarbij een nieuwe geplande update voor de speciale prijs niet kan worden gemaakt voor meerdere opslagruimten die gebruikmaken van REST API, als de begindatum van de update samenvalt met de einddatum van de vorige bestaande update.

<u> Stappen om </u> te reproduceren:

1. Stel een extra website-, opslag- en opslagweergave in.
1. Maak twee eenvoudige producten: &quot;product1&quot; en &quot;product2&quot;.
1. Product1 toewijzen aan één website en product2 aan beide websites.
1. Maak een geplande update voor de speciale prijs voor product1 in de winkelweergave voor de winkel met ID 1. REST API `POST` -aanvraag gebruiken voor `rest/V1/products/special-price` met de volgende payload:
   `{        "prices": [            {                "price": 15,                "store_id": 1,                "sku": "product1",                "price_from": "2021-11-15 04:00:00",                "price_to": "2021-11-15 04:10:00"            }        ]    }`
1. Maak een geplande update voor de speciale prijs voor product2 voor zowel winkelweergaven voor winkels met ID 1 en 2 met de REST API `POST` -aanvraag naar `rest/V1/products/special-price` met de volgende payload (de `price_from` -datum is dezelfde als `price_to` -datum in de vorige aanvraag):
   `{        "prices": [            {                "price": 14,                "store_id": 1,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            },            {                "price": 13,                "store_id": 2,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            }        ]    }`

<u> Verwachte resultaten </u>:

De geplande update met de speciale prijsverandering wordt gecreeerd op beide opslagmeningen.

<u> Ware resultaten </u>:

Adobe Commerce genereert een fout. De geplande update wordt niet gemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
