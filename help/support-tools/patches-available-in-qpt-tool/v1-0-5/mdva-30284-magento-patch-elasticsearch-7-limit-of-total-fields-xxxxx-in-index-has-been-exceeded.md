---
title: 'MDVA-30284-patch: Elasticsearch 7 - Limit of total fields [XXXXX] in index has been across'
description: De patch MDVA-30284 lost het probleem op waarbij u een foutbericht ontvangt dat "Limit of total fields \[XXXXX\] in index is overschreden" wanneer u Elasticsearch 7 gebruikt. Deze patch is beschikbaar wanneer het [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5 is geïnstalleerd. De patch-id is MDVA-30284.
exl-id: cf840558-891a-4a7e-8900-b8434f703be0
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-30284 Reparatie: Elasticsearch 7 - Limiet van totaal aantal velden [XXXXX] in index is overschreden

De patch MDVA-30284 lost het probleem op waarbij u een foutbericht ontvangt dat &quot;Limit of total fields \[XXXXX\] in index is overschreden&quot; wanneer u Elasticsearch 7 gebruikt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versie 1.0.5 is geïnstalleerd. De patch-id is MDVA-30284.

## Betrokken producten en versies

* De patch is ontworpen voor Adobe Commerce op cloudinfrastructuur 2.3.5-p2
* Elasticsearch 7 is compatibel met Adobe Commerce 2.3.5 en 2.4.x

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De limiet voor Elasticsearch-velden is onjuist. Dit resulteert in de volgende fout bij het uitvoeren van de indexfunctie \[cataloguszoekopdracht\_fulltext\]:

*Limiet voor totaal aantal velden [xxx] in index [xxxxxx] is overschreden*

Dit probleem doet zich voor wanneer u een groot aantal productkenmerken hebt. De kwestie wordt teweeggebracht door de manier de Elasticsearch de gebiedstelling berekent. Wanneer er kenmerken zijn waaraan velden zijn toegewezen, indexeren deze velden soms als afzonderlijke indexen. Hierdoor is de grenswaarde overschreden.

<u>Stappen om te reproduceren:</u>

<u>Vereisten</u>

* Geïnstalleerde module-elasticsearch 100.3.5.
* Elasticsearch 7 geïnstalleerd.
* Stel Elasticsearch in als een zoekbackend.

1. Maak meer dan 1000 kenmerken voor producten.
1. Maak producten voor elke familie.
1. Indexer uitvoeren.

<u>Verwacht resultaat:</u>

Alle producten zijn beschikbaar in de index van de Elasticsearch.

<u>Werkelijk resultaat:</u>

1. Fout in Elasticsearch:

   ```
    {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"}],"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"},"status":400}
   ```

1. Nieuw product is niet geïndexeerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
