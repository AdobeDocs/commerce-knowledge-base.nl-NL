---
title: "MDVA-31307: Onvoldoende geheugen voor bepaalde categorieën"
description: De patch MDVA-31307 verhelpt het probleem waarbij 'Magento\_Csp/Model/BlockCache' veel geheugen verbruikt en enorme in de cache opgeslagen tekenreeksen genereert. Dit veroorzaakt problemen voor bepaalde pagina's met veel dynamisch flitelende scripts en stijlen. De meegeleverde patch optimaliseert dit proces. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-31307. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 15d82f5b-bd43-4a0a-b756-d109dac6d2cd
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-31307: Onvoldoende geheugen voor bepaalde categorieën

De patch MDVA-31307 verhelpt het probleem waarbij `Magento\_Csp/Model/BlockCache` veel geheugen verbruikt en enorme tekenreeksen in de cache genereert. Dit veroorzaakt problemen voor bepaalde pagina&#39;s met veel dynamisch draaiende scripts en stijlen. De meegeleverde patch optimaliseert dit proces. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 geïnstalleerd is. De patch-id is MDVA-31307. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.4.0

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op-gebouw en Adobe Commerce op wolkeninfrastructuur 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Verhelpt de kwestie waar er *uit geheugen* fouten op bepaalde categorieën wegens problemen met dynamische CSP die voor caching blokken zijn.

<u> Stappen om te reproduceren:</u>

1. Genereer kleine profielcorrecties (`bin/magento setup:performance:generate-fixtures`).
1. Open alle categoriepagina&#39;s op verschillende tabbladen.

<u> Ware resultaat:</u>

*[datum en tijd ] PHP Onherstelbare fout: Toegestane geheugengrootte van 1073741824 bytes uitgeput (geprobeerd om 90112 bytes toe te wijzen) in Onbekend op lijn 0
[ datum en tijd ] PHP Onherstelbare fout: Toegestane geheugengrootte van 1073741824 bytes uitgeput (geprobeerd om 3355440 bytes toe te wijzen) in /app/ `<project-id>` /vendor/magento/module-csp/Model/Collector/DynamicCollector.php op lijn 31*

<u> Verwacht resultaat:</u>

Alle pagina&#39;s zijn correct geopend.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
