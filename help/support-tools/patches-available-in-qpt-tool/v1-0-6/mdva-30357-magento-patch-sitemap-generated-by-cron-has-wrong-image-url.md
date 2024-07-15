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

De patch MDVA-30357 verhelpt het probleem waarbij de onjuiste afbeeldings-URL wordt gemaakt door een door een uitsnede gegenereerde sitemap in Commerce Admin. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) 2.3.2 tot 2.4.0

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Sitemaps die door uitsnijden in Adobe Commerce worden gegenereerd, bevatten het onjuiste URL-pad voor afbeeldingen.

<u> Stappen om </u> te reproduceren:

1. Maak in Commerce Admin een nieuwe website, winkel of winkelweergave.
1. Voeg ten minste één product toe aan elke winkel en voeg ten minste één afbeelding toe aan elk product.
1. Laat **Sitemap Generatie door Programma** in **toe Admin** > **Opslag** > **Configuratie** > **CATALOG** > **Sitemap van XML** > **de Montages van de Generatie**.
1. Produceer een sitemap voor om het even welke twee opslag manueel in **Admin** > **Marketing** > **Kaart van de Plaats** gebruikend een naam sitemap zoals &quot;*sitemap.xml*&quot;.
   * Wijzig de naam van het dossier aan iets als &quot;*hand \_sitemap.xml*&quot;of kopieer de dossierinhoud aan om het even welke tekstredacteur.
1. Dezelfde sitemap genereren op snijtaak `sitemap_generate` .
1. Vergelijk manueel geproduceerde sitemap &quot;*hand \_sitemap.xml*&quot;en de sitemap die door bebouwing &quot;*wordt geproduceerd sitemap.xml*&quot;.

<u> Verwachte resultaten </u>:

De URL van het afbeeldingspad van de sitemap in de cache is juist.

<u> Ware resultaten </u>:

De sitemap die door uitsnijden wordt gegenereerd, bevat de onjuiste URL voor het afbeeldingspad. Als u probeert om het beeld van &quot;*sitemap.xml* te openen, zal het standaardplaceholder tonen. Dit probleem heeft geen invloed op handmatig gegenereerde sitemap-URL&#39;s.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.

Raadpleeg de volgende artikelen in de documentatie voor ontwikkelaars voor meer informatie over sitemaps:

* [ voeg sitemap en onderzoekmachine robots ](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) toe
* [ vorm en stel kroon ](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) in werking
* [ Veilig cron.php in browser ](https://devdocs.magento.com/guides/v2.4/config-guide/secy/secy-cron.html) in werking te stellen
