---
title: 'ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* wordt geplaatst aan ja zonder de *[!UICONTROL Use in Search] * optie'
description: Pas ACSD-50887 flard toe om de kwestie van Adobe Commerce te bevestigen waar het bezit van het productkenmerk * [!UICONTROL Use in Search Results Layered Navigation]* kan worden geplaatst aan *Yes* zonder de * [!UICONTROL Use in Search] * optie ook wordt geplaatst aan *Yes*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: b597709b-7489-41a0-b1ff-d68d0def0b46
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* geplaatst aan *ja* zonder de *[!UICONTROL Use in Search]* optie

ACSD-50887 flardfixes de kwestie waar het bezit van de productattributen *[!UICONTROL Use in Search Results Layered Navigation]* aan *ja* zonder de *[!UICONTROL Use in Search]* optie kan worden geplaatst ook aan *ja*. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.36 wordt geïnstalleerd. De patch-id is ACSD-50887. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het bezit van productattributen *[!UICONTROL Use in Search Results Layered Navigation]* kan aan *ja* zonder de *[!UICONTROL Use in Search]* optie worden geplaatst ook aan *ja*.

Deze instellingen zijn ontworpen voor gezamenlijk gebruik. Met het toegepaste flard, wanneer de *[!UICONTROL Use in Search]* optie aan *Nr* wordt geplaatst, is de *[!UICONTROL Use in Search Results Layered Navigation]* optie verborgen om te werken alsof het ook aan *Nr* werd geplaatst.

<u> Stappen om </u> te reproduceren:

1. Navigeer in Beheer naar **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** en maak een kenmerk met het type multiselect en stel het volgende in:

   * *[!UICONTROL Use in Search]= Nee*
   * *[!UICONTROL Use in Layered Navigation]= (Om het even welke optie)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Ja*
   * *Naam = Test_attribute*
   * *Opties*:
      * *Sticker*
      * *Plukker*

1. Voeg het nieuwe kenmerk toe aan de standaardkenmerkset.
1. Twee producten maken:

   1. Eerste product:
      * Name = Sticker
      * Prijs, QTY, Gewicht instellen op 1
      * Test_attribute = uitgezochte optie *Sticker*

   1. Tweede product:
      * Naam = kiezer
      * Prijs, QTY, Gewicht instellen op 1
      * Test_attribute = selecteer beide opties

1. `catalogsearch_fulltext` opnieuw indexeren:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Onderzoek door het woord *klever* op de storefront.

<u> Verwachte resultaten </u>:

Slechts wordt de product *Sticker* teruggekeerd, omdat [!DNL Elasticsearch] niet Test_attribute zal indexeren wanneer *[!UICONTROL Use in Search]* aan *Nr* is geplaatst.

<u> Ware resultaten </u>:

Beide producten worden geretourneerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
