---
title: 'ACSD-56246: De updates van het product plannen ontruimen multiselect attributenwaarden'
description: Pas de ACSD-56246-patch toe om het Adobe Commerce-probleem op te lossen, waarbij tijdens de planning van productupdates multiselect-kenmerkwaarden worden gewist.
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: ddca8ac0-6aa8-4bf1-b8c2-4819758cb198
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56246: Door productupdates te plannen worden waarden voor multiselect-kenmerken gewist

De ACSD-56246-patch verhelpt het probleem waarbij tijdens de planning van productupdates multiselect-kenmerkwaarden worden gewist. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 wordt geïnstalleerd. De patch-id is ACSD-56246. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De geplande productupdates wissen multiselect kenmerkwaarden.

<u> Stappen om </u> te reproduceren:

1. Adobe Commerce installeren.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** en maak het volgende kenmerk:

   * Standaardlabel: Programma
   * Invoertype catalogus voor winkeleigenaar: Meerdere selecties
   * Opties beheren (waarden van uw kenmerk): keuze, zonsondergang, veiligheidsschild
   * Kenmerkcode: customer_program
   * Bereik: Algemeen
   * Toevoegen aan kolomopties: Nee
   * Gebruiken in filteropties: Nee
   * Eigenschappen van Storefront
   * Positie: *333*
   * HTML-tags toestaan in winkelfront: Nee

1. Uitvoeren
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Uitvoeren
   `bin/magento setup:upgrade`.
1. Ga naar **[!UICONTROL Admin]** > Een eenvoudig product kiezen > Alle items in programmakenmerk selecteren > Klik op **[!UICONTROL Save the product]** .
1. Plan een update voor dit product in de komende minuut, en stel hieronder het bevel in werking om de Staging van de Inhoud te krijgen werkend:
   `for i in {1..100}; do bin/magento cron:run; done`.

<u> Verwachte resultaten </u>:

Het kenmerk **[!UICONTROL program]** van het product mag niet worden gewijzigd.

<u> Ware resultaten </u>:

Het kenmerk **[!UICONTROL program]** van het product wordt gewist.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
