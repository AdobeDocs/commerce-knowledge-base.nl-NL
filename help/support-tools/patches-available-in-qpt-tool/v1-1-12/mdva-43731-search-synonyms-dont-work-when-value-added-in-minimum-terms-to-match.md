---
title: '"MDVA-43731: De Synoniemen van het onderzoek werken niet wanneer de waarde in "Minimumtermijnen aan Gelijke"wordt toegevoegd'
description: De patch MDVA-43731 verhelpt het probleem waarbij Zoeksynoniemen niet meer werken wanneer een waarde wordt toegevoegd in "Minimumvoorwaarden voor overeenkomst". Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-43731. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: b795989c-d10b-443e-aebe-f3859930396a
feature: Cache, Marketing Tools, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-43731: De Synoniemen van het onderzoek werken niet wanneer de waarde in &quot;Minimumtermijnen aan Gelijke&quot;wordt toegevoegd

De patch MDVA-43731 verhelpt het probleem waarbij Zoeksynoniemen niet meer werken wanneer een waarde wordt toegevoegd in &quot;Minimumvoorwaarden voor overeenkomst&quot;. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 geïnstalleerd is. De patch-id is MDVA-43731. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Zoeksynoniemen werken niet meer wanneer een waarde wordt toegevoegd in &quot;Minimumvoorwaarden voor overeenkomst&quot;.

<u> Stappen om </u> te reproduceren:

1. Installeer Adobe Commerce met voorbeeldgegevens.
1. Configureer Elasticsearch7 als zoekprogramma.
1. Zoek naar het woord &quot;Jasje&quot;. Er wordt een lijst met producten weergegeven.
1. Voeg de parameter [ 4&lt;60% ] in **Configuratie** toe > **Catalogus** > **het Onderzoek van de Catalogus** > **Minimale Termen om** aan te passen.
1. Wis het Geheime voorgeheugen Config en doe een herdex.
1. Zoek opnieuw naar het woord &quot;Jasje&quot;. U ziet dat er een lijst met producten wordt weergegeven.
1. Ga naar **Marketing** > **SEO &amp; Onderzoek** > **Synoniemen van het Onderzoek**.
1. Creeer de Synoniemen van het Onderzoek door de volgende synoniemen toe te voegen: jasje, bagtecs, express plus.
1. Voer een herindex uit.
1. Zoek een product met een van de synoniemen. Bijvoorbeeld jasje.

<u> Verwachte resultaten </u>:

Je krijgt dezelfde productlijst als voorheen in de zoekresultaten.

<u> Ware resultaten </u>:

Er wordt geen product weergegeven in de zoekresultaten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
