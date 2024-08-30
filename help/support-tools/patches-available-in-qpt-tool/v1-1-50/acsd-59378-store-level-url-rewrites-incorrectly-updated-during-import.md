---
title: '"ACSD-59378: opslag-niveau  [!DNL URL]  herschrijft verkeerd bijgewerkt tijdens de invoer'''
description: Pas ACSD-59378 flard toe om de kwestie van Adobe Commerce te bevestigen waar store-level  [!DNL URL]  herschrijft verkeerd tijdens de invoer wordt bijgewerkt.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 3f400c3e325c3f377a5e12170b08615ebeadbcd1
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# ACSD-59378: op archiefniveau [!DNL URL] wordt tijdens het importeren onjuist bijgewerkt

De ACSD-59378-patch verhelpt het probleem waarbij de herschrijvingen op archiefniveau [!DNL URL] tijdens het importeren onjuist worden bijgewerkt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-59378. Dit probleem is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.5-p5

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.5x (alle versies van 2.4.5)

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Herschrijvingen op winkelniveau [!DNL URL] worden tijdens het importeren onjuist bijgewerkt.

<u> Stappen om </u> te reproduceren:

1. Creeer een product met `url_key = key_default` op het **Alle 2} werkingsgebied van de Mening van de Opslag {.**
1. Plaats `url_key = key_store` in het **Standaard2} werkingsgebied van de Mening van de Opslag {.**
1. Het product exporteren.
1. Importeer een [!DNL CSV] -bestand voor dit product met de volgende gegevens erin:
   * `store_view_code` de kolom wordt geplaatst aan *leeg* zodat het voor het **Alle werkingsgebied van de Kijken van de Opslag** van toepassing is.
   * `url_key` wordt ingesteld op de standaardtoets *`key_default`* .

<u> Verwachte Resultaten </u>:

[!DNL URL] herschrijft wordt alleen opnieuw gegenereerd voor opslagweergaven waarbij er geen sprake is van overschrijven `url_key` (waarbij de standaardwaarde `url_key` van toepassing is).

<u> Ware Resultaten </u>:

`key_store` [!DNL URL] herschrijft wordt geschrapt, maar [!DNL URL] herschrijft op het **Standaard niveau van de Mening van de Opslag** voor het product nog wordt geplaatst aan *`key_store`*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
