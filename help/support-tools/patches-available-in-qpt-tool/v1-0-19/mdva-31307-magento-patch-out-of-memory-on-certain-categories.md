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

De MDVA-31307-patch verhelpt het probleem waarbij `Magento\_Csp/Model/BlockCache` Er wordt veel geheugen gebruikt en er worden enorme, in het cachegeheugen opgeslagen tekenreeksen gegenereerd. Dit veroorzaakt problemen voor bepaalde pagina&#39;s met veel dynamisch draaiende scripts en stijlen. De meegeleverde patch optimaliseert dit proces. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-31307. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Hiermee wordt het probleem opgelost waar *Onvoldoende geheugen* fouten op bepaalde categorieën als gevolg van problemen met de dynamische whitelisting van CSP voor in cache geplaatste blokken.

<u>Stappen om te reproduceren:</u>

1. Kleine profielcorrecties genereren (`bin/magento setup:performance:generate-fixtures`).
1. Open alle categoriepagina&#39;s op verschillende tabbladen.

<u>Werkelijk resultaat:</u>

*[datum en tijd] Fatale fout PHP: Geoorloofde geheugengrootte van 1073741824 bytes uitgeput (geprobeerd 90112 bytes toe te wijzen) in Onbekend op regel 0
[datum en tijd] Fatale fout PHP: Geoorloofde geheugengrootte van 1073741824 bytes is uitgeput (geprobeerd 3355440 bytes toe te wijzen) in /app/`<project-id>`/vendor/magento/module-csp/Model/Collector/DynamicCollector.php op regel 31*

<u>Verwacht resultaat:</u>

Alle pagina&#39;s zijn correct geopend.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
