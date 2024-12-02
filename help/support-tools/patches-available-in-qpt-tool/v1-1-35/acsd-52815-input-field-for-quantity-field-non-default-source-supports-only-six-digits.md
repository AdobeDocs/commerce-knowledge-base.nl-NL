---
title: 'ACSD-52815: invoerveld voor kwantiteitsveld van niet-standaardbron ondersteunt slechts maximaal 6 cijfers'
description: Pas de ACSD-52815-patch toe om het Adobe Commerce-prestatieprobleem op te lossen, waarbij het invoerveld voor het kwantitatieve veld van een niet-standaard bron maximaal 6 cijfers ondersteunt, in tegenstelling tot 8 voor een standaardvoorraad.
feature: Inventory, Products
role: Admin
exl-id: 44fda5ef-cb8a-481a-9112-f36d886ae3db
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-52815: invoerveld voor kwantiteitsveld van niet-standaardbron ondersteunt slechts maximaal 6 cijfers

De ACSD-52815-patch verhelpt het probleem dat het invoerveld voor het kwantitatieve veld van een niet-standaardbron slechts maximaal zes cijfers ondersteunt, in tegenstelling tot 8 voor een standaardvoorraad. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-52815. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het invoerveld voor het kwantitatieve veld van een niet-standaardbron ondersteunt slechts maximaal 6 cijfers, in tegenstelling tot 8 voor een standaardvoorraad.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe voorraad en bron.
1. Maak een product met de nieuwe bronvoorraad ingesteld op 123.
1. Controleer de verkoopbare hoeveelheid (123).
1. Werk de bronhoeveelheid bij naar 12345678.
1. Controleer de verkochte hoeveelheid opnieuw.

<u> Verwachte resultaten </u>:

De juiste hoeveelheid wordt aangegeven.

<u> Ware resultaten </u>:

De verkoopbare hoeveelheid bedraagt 999999,9999.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
