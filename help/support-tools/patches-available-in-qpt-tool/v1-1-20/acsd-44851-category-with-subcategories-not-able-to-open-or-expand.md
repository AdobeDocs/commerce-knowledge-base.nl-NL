---
title: 'ACSD-44851: Categorie met subcategorieën die niet kunnen worden geopend of uitgebreid'
description: Dit artikel biedt een oplossing voor het probleem waarbij de gebruiker een categorie met subcategorieën niet kan openen of uitbreiden.
exl-id: 46ad9f9d-ed66-44df-b66d-ab9ff3923c36
feature: Categories
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-44851: Categorie met subcategorieën die niet kunnen worden geopend of uitgebreid

De ACSD-44851-patch lost het probleem op waarbij de gebruiker een categorie met subcategorieën niet kan openen of uitbreiden. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 geïnstalleerd is. De patch-id is ACSD-44851. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker kan een categorie met subcategorieën niet openen of uitbreiden.

<u> Stappen om </u> te reproduceren:

1. Maak in Adobe Commerce Admin een categoriestructuur met twee hoofdcategorieën en enkele subcategorieën voor elk hoofdknooppunt.
1. Open de mobiele weergave/emulator of maak de vensterbreedte kleiner totdat de lay-out mobiel wordt.
1. Open het hoofdmenu van de catalogus.
1. Probeer de hoofdcategorieën uit te vouwen.
1. Open de rubriek.

<u> Verwachte resultaten </u>:

Het menu is toegankelijk.

<u> Ware resultaten </u>:

Het tweede niveau van het mobiele menu wordt niet geopend.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Hulpmiddelen van de Patches van de Kwaliteit > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de gids van het Hulpmiddel van de Patches van de Kwaliteit.

* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de gids van het Hulpmiddel van de Patches van de Kwaliteit.
