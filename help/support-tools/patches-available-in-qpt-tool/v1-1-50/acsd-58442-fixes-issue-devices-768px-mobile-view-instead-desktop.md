---
title: 'ACSD-58442: Het probleem waarbij apparaten met een breedte van 768 px als mobiel worden behandeld, waardoor menu''s en kopteksten in de mobiele weergave niet als bureaublad worden geladen'
description: Pas de ACSD-58442-patch toe om het Adobe Commerce-probleem op te lossen, waarbij apparaten met een breedte van 768 px als mobiel worden beschouwd, waardoor het menu en de koptekst in een mobiele weergave in plaats van op het bureaublad worden geladen.
feature: Storefront
role: Admin, Developer
exl-id: 05d812b9-c5f5-4397-9755-bed2424e70b3
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-58442: Het probleem waarbij apparaten met een breedte van 768 px als mobiel worden behandeld, waardoor menu&#39;s en kopteksten in de mobiele weergave niet als bureaublad worden geladen

De ACSD-58442-patch verhelpt het Adobe Commerce-probleem waarbij apparaten met een breedte van 768 px als mobiel worden beschouwd, waardoor het menu en de koptekst in een mobiele weergave in plaats van op een bureaublad worden geladen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-58442. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het systeem behandelt apparaten met een breedte van 768 px als Desktop, die ervoor zorgen dat het menu en de kopbal correct laden. Eerder werden apparaten met een breedte van 768 px als mobiel beschouwd, waardoor het menu en de koptekst in een mobiele weergave werden geladen.

<u> Stappen om </u> te reproduceren:

1. Laad de homepage op een Mini van iPad of gebruik browser inspecteert hulpmiddel resize browser aan een breedte van *768px*.
1. Open het hoofdmenu.

<u> Verwachte resultaten </u>:

Menu- en kopteksten worden geladen als een bureaubladweergave.

<u> Ware resultaten </u>:

Menu- en kopteksten worden geladen als een mobiele weergave.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
