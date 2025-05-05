---
title: 'MDVA-43451: Fout bij het instellen van Prijs en Structuur voor gedeelde catalogus'
description: Met de MDVA-43451-patch wordt het probleem opgelost waarbij de gebruiker de prijs en structuur voor een gedeelde catalogus niet kan instellen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-43451. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 78de2e98-dfd7-4829-8e3f-76eadf5570e8
feature: Catalog Management
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-43451: Fout bij het instellen van Prijs en Structuur voor gedeelde catalogus

Met de MDVA-43451-patch wordt het probleem opgelost waarbij de gebruiker de prijs en structuur voor een gedeelde catalogus niet kan instellen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 geïnstalleerd is. De patch-id is MDVA-43451. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker kan geen Prijs en Structuur voor een gedeelde catalogus plaatsen. Het volgende bericht wordt getoond: *de opslag die werd gevraagd werd niet gevonden. Verifieer de opslag en probeer opnieuw.*

<u> Stappen om </u> te reproduceren:

1. Maak een aangepaste website. De id&#39;s van de websites moeten 0, 1, 2 zijn.
1. Maak één winkel onder de bovenstaande website. De voorraden moeten 0,1,2 bevatten.
1. Maak drie winkelweergaven voor de bovenstaande winkel. De id&#39;s van de winkelweergaven moeten 0,1, 2, 3, 4 zijn.
1. Verwijder de winkelweergave met id 2. De opslagtabel moet er nu ongeveer zo uitzien als de onderstaande tabel.

   ```bash
   MariaDB [m24devinvb2b]> SELECT store_id,code,website_id,group_id,name FROM store;
   +----------+----------------+------------+----------+--------------------+
   | store_id | code           | website_id | group_id | name               |
   +----------+----------------+------------+----------+--------------------+
   |        0 | admin          |          0 |        0 | Admin              |
   |        1 | default        |          1 |        1 | Default Store View |
   |        3 | web1storeview2 |          2 |        2 | web1storeview2     |
   |        4 | web1storeview3 |          2 |        2 | web1storeview3     |
   +----------+----------------+------------+----------+--------------------+
   ```

1. Maak een nieuwe gedeelde catalogus.
1. Wanneer het vormen van Prijs en Structuur, selecteer de opslag die in Stap 2 wordt gecreeerd.
1. Sla de gedeelde catalogus op.

<u> Verwachte resultaten </u>:

De gedeelde catalogus wordt zonder problemen opgeslagen.

<u> Ware resultaten </u>:

U kunt de gedeelde catalogus niet opslaan. De volgende fout wordt weergegeven:
*de opslag die werd gevraagd werd niet gevonden. Verifieer de opslag en probeer opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
