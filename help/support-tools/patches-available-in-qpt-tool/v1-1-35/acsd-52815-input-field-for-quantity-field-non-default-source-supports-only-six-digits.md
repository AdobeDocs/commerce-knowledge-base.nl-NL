---
title: 'ACSD-52815: invoerveld voor kwantiteitsveld van niet-standaard bron ondersteunt slechts maximaal 6 cijfers'
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

De ACSD-52815-patch verhelpt het probleem dat het invoerveld voor het kwantitatieve veld van een niet-standaardbron slechts maximaal zes cijfers ondersteunt, in tegenstelling tot 8 voor een standaardvoorraad. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.35 is geïnstalleerd. De patch-id is ACSD-52815. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het invoerveld voor het kwantitatieve veld van een niet-standaardbron ondersteunt slechts maximaal 6 cijfers, in tegenstelling tot 8 voor een standaardvoorraad.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe voorraad en bron.
1. Maak een product met de nieuwe bronvoorraad ingesteld op 123.
1. Controleer de verkoopbare hoeveelheid (123).
1. Werk de bronhoeveelheid bij naar 12345678.
1. Controleer de verkochte hoeveelheid opnieuw.

<u>Verwachte resultaten</u>:

De juiste hoeveelheid wordt aangegeven.

<u>Werkelijke resultaten</u>:

De verkoopbare hoeveelheid bedraagt 999999,9999.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
