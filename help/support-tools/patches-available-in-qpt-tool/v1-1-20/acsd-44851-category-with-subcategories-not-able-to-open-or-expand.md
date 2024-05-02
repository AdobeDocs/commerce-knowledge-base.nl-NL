---
title: "ACSD-44851: Categorie met subcategorieën die niet kunnen worden geopend of uitgebreid"
description: Dit artikel biedt een oplossing voor het probleem waarbij de gebruiker een categorie met subcategorieën niet kan openen of uitbreiden.
exl-id: 46ad9f9d-ed66-44df-b66d-ab9ff3923c36
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-44851: Categorie met subcategorieën die niet kunnen worden geopend of uitgebreid

De ACSD-44851-patch lost het probleem op waarbij de gebruiker een categorie met subcategorieën niet kan openen of uitbreiden. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 is geïnstalleerd. De patch-id is ACSD-44851. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker kan een categorie met subcategorieën niet openen of uitbreiden.

<u>Stappen om te reproduceren</u>:

1. Maak in Adobe Commerce Admin een categoriestructuur met twee hoofdcategorieën en enkele subcategorieën voor elk hoofdknooppunt.
1. Open de mobiele weergave/emulator of maak de vensterbreedte kleiner totdat de lay-out mobiel wordt.
1. Open het hoofdmenu van de catalogus.
1. Probeer de hoofdcategorieën uit te vouwen.
1. Open de rubriek.

<u>Verwachte resultaten</u>:

Het menu is toegankelijk.

<u>Werkelijke resultaten</u>:

Het tweede niveau van het mobiele menu wordt niet geopend.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Quality Patches Tools > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding voor het gereedschap Kwaliteitspatches.

* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de handleiding voor het gereedschap Kwaliteitspatches.
