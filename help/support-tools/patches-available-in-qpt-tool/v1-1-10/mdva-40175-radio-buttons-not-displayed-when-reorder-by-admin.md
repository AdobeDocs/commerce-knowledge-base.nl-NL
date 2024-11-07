---
title: 'MDVA-40175: Keuzerondjes niet weergegeven bij opnieuw ordenen'
description: Met de MDVA-40175-patch wordt het probleem opgelost waarbij de keuzerondjes niet worden weergegeven wanneer gebruikers proberen de volgorde te wijzigen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-40175. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 307c450d-9f53-40b7-b2f5-d867850c043a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-40175: Radio buttons not displayed when reorder

Met de MDVA-40175-patch wordt het probleem opgelost waarbij de keuzerondjes niet worden weergegeven wanneer gebruikers proberen de volgorde te wijzigen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 geïnstalleerd is. De patch-id is MDVA-40175. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Keuzerondjes worden niet weergegeven in het gedeelte Betalings- en verzendgegevens wanneer gebruikers de volgorde opnieuw proberen in te stellen.

<u> Eerste vereisten </u>:

1. Er wordt een Customer account aangemaakt met een verzendadres en een factuuradres.
1. Er wordt een eenvoudig product gemaakt.
1. Verschillende leveringsmethoden zijn geconfigureerd.
1. Er wordt ten minste één bestelling gemaakt.

<u> Stappen om </u> te reproduceren:

1. Ga naar het Admin paneel > **Verkoop** > **Orden**.
1. Selecteer de gemaakte volgorde.
1. Klik de **verbinding van de Mening**.
1. Klik **opnieuw rangschikken** knoop.
1. De rol neer de pagina aan de **Betaling &amp; Verzendinformatie** sectie.
1. Klik **klikken om het verschepen methode** te veranderen.

<u> Verwachte resultaten </u>:

De lijst met leveringsmethoden met keuzerondjes wordt weergegeven.

<u> Ware resultaten </u>:

De lijst met leveringsmethoden zonder keuzerondjes wordt weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
