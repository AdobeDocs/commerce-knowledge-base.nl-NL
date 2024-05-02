---
title: 'MDVA-40134: GraphQL retourneert geen verwante producten als gedeelde catalogus is ingeschakeld.'
description: De MDVA-40134-patch verhelpt het probleem dat GraphQL geen verwante producten retourneert wanneer de gedeelde catalogus is ingeschakeld. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-40134. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 7b14355a-1c14-4c80-9426-6c40505d638b
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-40134: GraphQL retourneert geen verwante producten als gedeelde catalogus is ingeschakeld

De MDVA-40134-patch verhelpt het probleem dat GraphQL geen verwante producten retourneert wanneer de gedeelde catalogus is ingeschakeld. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-40134. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL retourneert geen verwante producten wanneer de gedeelde catalogus is ingeschakeld.

<u>Vereisten</u>:

B2B-modules moeten worden geïnstalleerd.
Het exemplaar moet schoon zijn met alleen de monstergegevens.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkels** > **Configuratie** > **Algemeen** > **B2B-functies** en **Bedrijf en gedeelde catalogus**.
1. Ga naar **Catalogus** > **Gedeelde catalogus** en alle producten aan de **Algemene catalogus**.
1. Gebruik de voorbeeldgegevens en wijzig de joust Duffle Bag (SKU 24-MB01).
1. Onder **Verwante producten** de twee duffelzakken (ID 7 en 13).
1. Een **Post** verzoek:

<pre>{ products(filter: {sku: {eq: "24-MB01"}, sort: {name: ASC}) { items { related_products { uid name } } } }</pre>

<u>Verwachte resultaten</u>:

Verwante producten worden weergegeven in de reactie van GraphQL.

<u>Werkelijke resultaten</u>:

Gebruikers krijgen de volgende fout:

<pre>Retourwaarde van Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() moet van het type int zijn, null geretourneerd {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Retourwaarde van Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() moet van het type int zijn, null geretourneerd </pre>

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
