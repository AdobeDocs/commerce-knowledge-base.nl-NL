---
title: 'MDVA-30357: sitemap gegenereerd door cron heeft onjuiste afbeeldings-URL'
description: De patch MDVA-30357 verhelpt het probleem waarbij de onjuiste afbeeldings-URL wordt gemaakt door een door een uitsnede gegenereerde sitemap in Commerce Admin. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: c91f7ae0-0970-4918-9d1f-4ede6bfcb05f
feature: Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---

# MDVA-30357: sitemap gegenereerd door cron heeft onjuiste afbeeldings-URL

De patch MDVA-30357 verhelpt het probleem waarbij de onjuiste afbeeldings-URL wordt gemaakt door een door een uitsnede gegenereerde sitemap in Commerce Admin. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) 2.3.2 tot 2.4.0

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Sitemaps die door uitsnijden in Adobe Commerce worden gegenereerd, bevatten het onjuiste URL-pad voor afbeeldingen.

<u>Stappen om te reproduceren</u>:

1. Maak in Commerce Admin een nieuwe website, winkel of winkelweergave.
1. Voeg ten minste één product toe aan elke winkel en voeg ten minste één afbeelding toe aan elk product.
1. Inschakelen **Sitemap genereren op schema** in **Beheerder** > **Winkels** > **Configuratie** > **CATALOGUS** > **XML Sitemap** > **Generatie-instellingen**.
1. Genereer handmatig een sitemap voor de twee winkels in **Beheerder** > **Marketing** > **Site-overzicht** sitemapnamen gebruiken als &quot;*sitemap.xml*&quot;.
   * Wijzig de naam van het bestand in iets als &quot;*manual\_sitemap.xml*&quot; of kopieer de bestandsinhoud naar een teksteditor.
1. Dezelfde sitemap genereren op basis van een snijtaak `sitemap_generate`.
1. Vergelijk de handmatig gegenereerde sitemap &quot;*manual\_sitemap.xml*&quot; en de sitemap die door de kroon wordt gegenereerd &quot;*sitemap.xml*&quot;.

<u>Verwachte resultaten</u>:

De URL van het afbeeldingspad van de sitemap in de cache is juist.

<u>Werkelijke resultaten</u>:

De sitemap die door uitsnijden wordt gegenereerd, bevat de onjuiste URL voor het afbeeldingspad. Als u de afbeelding probeert te openen met &quot;*sitemap.xml*&quot;, wordt een standaardplaatsaanduiding weergegeven. Dit probleem heeft geen invloed op handmatig gegenereerde sitemap-URL&#39;s.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.

Raadpleeg de volgende artikelen in de documentatie voor ontwikkelaars voor meer informatie over sitemaps:

* [Sitemap- en zoekprogrammarobots toevoegen](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html)
* [Uitsnede configureren en uitvoeren](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)
* [Secure cron.php to run in browser](https://devdocs.magento.com/guides/v2.4/config-guide/secy/secy-cron.html)
