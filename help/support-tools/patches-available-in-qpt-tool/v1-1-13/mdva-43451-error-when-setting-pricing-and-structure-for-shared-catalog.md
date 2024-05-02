---
title: 'MDVA-43451: Fout bij het instellen van Prijs en Structuur voor gedeelde catalogus'
description: Met de MDVA-43451-patch wordt het probleem opgelost waarbij de gebruiker de prijs en structuur voor een gedeelde catalogus niet kan instellen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-43451. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 78de2e98-dfd7-4829-8e3f-76eadf5570e8
feature: Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-43451: Fout bij het instellen van Prijs en Structuur voor gedeelde catalogus

Met de MDVA-43451-patch wordt het probleem opgelost waarbij de gebruiker de prijs en structuur voor een gedeelde catalogus niet kan instellen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-43451. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker kan geen Prijs en Structuur voor een gedeelde catalogus plaatsen. Het volgende bericht wordt weergegeven: *De aangevraagde winkel is niet gevonden. Controleer de winkel en probeer het opnieuw.*

<u>Stappen om te reproduceren</u>:

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

<u>Verwachte resultaten</u>:

De gedeelde catalogus wordt zonder problemen opgeslagen.

<u>Werkelijke resultaten</u>:

U kunt de gedeelde catalogus niet opslaan. De volgende fout wordt weergegeven:
*De aangevraagde winkel is niet gevonden. Controleer de winkel en probeer het opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
