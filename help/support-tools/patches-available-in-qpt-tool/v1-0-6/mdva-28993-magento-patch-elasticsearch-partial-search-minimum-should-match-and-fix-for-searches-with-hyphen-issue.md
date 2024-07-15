---
title: '''MDVA-28993: Gedeeltelijke zoekopdracht in Elasticsearch, ''minimum dient overeen te komen'' en probleem ''doorzoeken met afbreekstreepje'' oplossen'
description: De patch MDVA-28993 implementeert de functionaliteit "Minimum dient overeen te komen" en gedeeltelijk zoeken naar de Elasticsearch-engine, en lost problemen met koppeltekens op in zoekopdrachten. De patch is beschikbaar wanneer [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 is geïnstalleerd.
exl-id: 2af0f950-284b-42f2-9660-8aafce4b04d7
feature: Search, Services
role: Admin
source-git-commit: 6f4d6382cbdb7bedddcc3f264fbf6ef997729323
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-28993: Gedeeltelijke zoekopdracht Elasticsearch, &quot;minimum dient overeen te komen&quot; en probleem &quot;zoekopdrachten met afbreekstreepje&quot; oplossen

De patch MDVA-28993 implementeert de functionaliteit &quot;Minimum dient overeen te komen&quot; en gedeeltelijk zoeken naar de Elasticsearch-engine, en lost problemen met koppeltekens op in zoekopdrachten. Het flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6 geïnstalleerd is.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.3.4

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op-gebouw/Adobe Commerce op wolkeninfrastructuur 2.3.4-2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.


## Probleem

Wanneer het gebruiken van Elasticsearch 6 voor het zoeken SKU die een koppelteken (-) bevat, keert het onderzoek teveel resultaten terug.

<u> Stappen om te reproduceren:</u>

1. Ga naar de winkel.

1. Voer op de zoekbalk een tekenreeks in met een afbreekstreepje, bijvoorbeeld &quot;WS-M-Blue&quot;.

<u> Verwacht resultaat:</u>

Retourneert alleen WS-M-Blue.

<u> Ware resultaat:</u>

Retourneert alle SKU&#39;s die beginnen met &quot;WS&quot;.

## Patchdetails

De MDVA-28993-patch bevat de volgende oplossingen en verbeteringen:

* Hiermee implementeert u de nieuwe functionaliteit &quot;Minimum moet overeenkomen&quot; en gedeeltelijk zoeken naar de Elasticsearch-engine. Voor configuratiedetails verwijzen naar [ het Vormen het Onderzoek van de Catalogus ](https://docs.magento.com/user-guide/catalog/search-configuration.html#step-4-configure-minimum-terms-to-match) in onze gebruikersgids.
* gedeeltelijk zoeken naar Elasticsearch
* Hiermee verhelpt u het hierboven beschreven probleem met &#39;&#39;zoekopdrachten met afbreekstreepje&#39;&#39;.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
