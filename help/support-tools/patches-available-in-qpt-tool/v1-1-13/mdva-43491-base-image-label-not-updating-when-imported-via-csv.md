---
title: 'MDVA-43491: basislabel voor afbeelding wordt niet bijgewerkt wanneer het wordt geïmporteerd via CSV'
description: De patch MDVA-43491 verhelpt het probleem waarbij het label "base_image_label" niet wordt bijgewerkt wanneer het wordt geïmporteerd via een CSV-bestand voor een website met meerdere winkels. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-43491. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: d744423a-f582-4410-8d66-861229cce1b5
feature: Data Import/Export
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-43491: basislabel voor afbeelding wordt niet bijgewerkt wanneer het wordt geïmporteerd via CSV

De MDVA-43491-patch verhelpt het probleem waarbij `base_image_label` niet wordt bijgewerkt wanneer het wordt geïmporteerd via een CSV-bestand voor een multi-store-website. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 geïnstalleerd is. De patch-id is MDVA-43491. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De `base_image_label` wordt niet bijgewerkt wanneer deze wordt geïmporteerd met een CSV-bestand voor een website met meerdere opslaglocaties.

<u> Eerste vereisten </u>:

Een of meer bestaande niet-standaardwebsites, winkels en winkelweergaven.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuw product.

   * Upload een afbeelding.
   * Wijs het product toe aan de nieuwe websites.

1. Exporteer het product als CSV.
1. Werk `base_image_label` voor elke archiefmening bij door de standaardrij van het Csv- dossier te dupliceren.
1. Het CSV-bestand importeren. Het zal de etiketten voor elke opslag correct bijwerken, die onder de **Beelden en Video&#39;s** tabel op het product kan worden geverifieerd geeft pagina uit.
1. Exporteer het CSV-bestand opnieuw en werk de kolom `base_image_label` bij met andere waarden.
1. Importeer het CSV-bestand opnieuw.
1. Open het product in de Admin en controleer of het label voor elke winkelweergave is bijgewerkt.

<u> Verwachte resultaten </u>:

Alt Text (afbeeldingslabel) wordt bijgewerkt met de opslagspecifieke waarde volgens het CSV-bestand.

<u> Ware resultaten </u>:

Alt Text (afbeeldingslabel) wordt niet bijgewerkt met de `base_image_label` -waarde in het CSV-bestand.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
