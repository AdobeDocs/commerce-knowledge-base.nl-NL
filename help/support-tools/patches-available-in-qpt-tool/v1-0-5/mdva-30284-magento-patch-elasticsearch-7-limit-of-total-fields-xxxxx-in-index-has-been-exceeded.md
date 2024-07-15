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

# MDVA-30284 Reparatie: Elasticsearch 7 - de Grens van totale gebieden [ XXXXX ] in index is overschreden

De patch MDVA-30284 lost het probleem op waarbij u een foutbericht ontvangt dat &quot;Limit of total fields \[XXXXX\] in index is overschreden&quot; wanneer u Elasticsearch 7 gebruikt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5 geïnstalleerd is. De patch-id is MDVA-30284.

## Betrokken producten en versies

* De patch is ontworpen voor Adobe Commerce op cloudinfrastructuur 2.3.5-p2
* Elasticsearch 7 is compatibel met Adobe Commerce 2.3.5 en 2.4.x

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De limiet voor Elasticsearch-velden is onjuist. Dit resulteert in de volgende fout bij het uitvoeren van de indexfunctie \[cataloguszoekopdracht\_fulltext\]:

*Grens van totale gebieden [ xxx ] in index [ xxxxxx ] is overschreden*

Dit probleem doet zich voor wanneer u een groot aantal productkenmerken hebt. De kwestie wordt teweeggebracht door de manier de Elasticsearch de gebiedstelling berekent. Wanneer er kenmerken zijn waaraan velden zijn toegewezen, indexeren deze velden soms als afzonderlijke indexen. Hierdoor is de grenswaarde overschreden.

<u> Stappen om te reproduceren:</u>

<u> Eerste vereisten </u>

* Geïnstalleerde module-elasticsearch 100.3.5.
* Elasticsearch 7 geïnstalleerd.
* Stel Elasticsearch in als een zoekbackend.

1. Maak meer dan 1000 kenmerken voor producten.
1. Maak producten voor elke familie.
1. Indexer uitvoeren.

<u> Verwacht resultaat:</u>

Alle producten zijn beschikbaar in de index van de Elasticsearch.

<u> Ware resultaat:</u>

1. Fout in Elasticsearch:

   ```
    {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"}],"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"},"status":400}
   ```

1. Nieuw product is niet geïndexeerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
