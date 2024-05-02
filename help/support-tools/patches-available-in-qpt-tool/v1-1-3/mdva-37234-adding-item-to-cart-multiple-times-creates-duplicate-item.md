---
title: 'MDVA-37234: Als u een item aan een winkelwagentje toevoegt, wordt een dubbel regelitem gemaakt.'
description: Met de MDVA-37234-patch is het probleem verholpen waarbij een item meerdere keren (parallel verzoek) voor dezelfde SKU aan het winkelwagentje wordt toegevoegd, waardoor een dubbel lijstitem voor dezelfde winkelwagentje-id wordt gemaakt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3 is geïnstalleerd. De patch-id is MDVA-37234. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 8f0dc249-10b2-4f2c-abca-1f5b7aea204d
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-37234: Als u een item meerdere keren aan het winkelwagentje toevoegt, wordt een dubbel lijstitem gemaakt

Met de MDVA-37234-patch is het probleem verholpen waarbij een item meerdere keren (parallel verzoek) voor dezelfde SKU aan het winkelwagentje wordt toegevoegd, waardoor een dubbel lijstitem voor dezelfde winkelwagentje-id wordt gemaakt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3 is geïnstalleerd. De patch-id is MDVA-37234. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.3.6, 2.4.1 en 2.4.2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.3.7-p1 en 2.4.1 - 2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een item meerdere keren (parallel verzoek) voor dezelfde SKU aan het winkelwagentje toevoegt, wordt een dubbele regel voor dezelfde winkelwagentje-id gemaakt.

<u>Stappen om te reproduceren</u>:

1. Creeer een eenvoudig product met SKU = simple1.
1. Maak een klant.
1. Een klanttoken genereren voor GraphQL-aanvragen.

   <pre>
    <code class="language-graphql">
    mutation {
        generateCustomerToken(
            email: "customer email"
            password: "customer password"
        )
        {
            token
        }
    }
    </code>
    </pre>

1. Gebruik het token dat in stap 3 wordt vermeld om een leeg winkelwagentje voor de klant te maken.

   <pre>
    <code class="language-graphql">
    mutation{
     createEmptyCart
    }
    </code>
    </pre>

1. Een script maken om twee te maken `addSimpleProductsToCart` aanvragen die parallel lopen. Bijvoorbeeld:

   <pre>
    <code class="language-#!/bin/bash">
    curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MywiaWF0IjoxNjIzOTUyNjcwLCJleHAiOjE2MjM5NTYyNzB9.-fh7ysqiQTAacdB3MVvaXzFE9AmKyfF8TsVmICLJoWI" -d '{"query" : "mutation { addSimpleProductsToCart( input: { cart_id: \"S8dCF7uan1POMy0qY0Hup7tEv1AhFGdY\" cart_items: [ { data: { quantity: 2 sku: \"simple1\" } } ] } ) { cart { items { id product { name sku } quantity } } } }"}' http://magento2.3.local/graphql &
    curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MywiaWF0IjoxNjIzOTUyNjcwLCJleHAiOjE2MjM5NTYyNzB9.-fh7ysqiQTAacdB3MVvaXzFE9AmKyfF8TsVmICLJoWI" -d '{"query" : "mutation { addSimpleProductsToCart( input: { cart_id: \"S8dCF7uan1POMy0qY0Hup7tEv1AhFGdY\" cart_items: [ { data: { quantity: 1 sku: \"simple1\" } } ] } ) { cart { items { id product { name sku } quantity } } } }"}' http://magento2.3.local/graphql
    </code>
    </pre>

1. Voer het script uit.

<u>Verwachte resultaten</u>:

In het winkelwagentje wordt slechts één productlijn met een totale hoeveelheid (drie in dit geval) gemaakt.

<u>Werkelijke resultaten</u>:

In de winkelwagentje worden twee afzonderlijke regels voor hetzelfde product gemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over kwaliteitspatches voor Adobe Commerce:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
