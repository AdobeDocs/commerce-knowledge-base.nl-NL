---
title: '"ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* ingesteld op Ja zonder de *[!UICONTROL Use in Search]* option '''
description: Pas de ACSD-50887-patch toe om het Adobe Commerce-probleem op te lossen waar de eigenschap productkenmerk *[!UICONTROL Use in Search Results Layered Navigation]* kan worden ingesteld op *Ja* zonder de *[!UICONTROL Use in Search]* wordt ook ingesteld op *Ja*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: b597709b-7489-41a0-b1ff-d68d0def0b46
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-5087: *[!UICONTROL Use in Search Results Layered Navigation]* instellen op *Ja* zonder *[!UICONTROL Use in Search]* option

De ACSD-50887-patch verhelpt het probleem waarbij de eigenschap van het productkenmerk *[!UICONTROL Use in Search Results Layered Navigation]* kan worden ingesteld op *Ja* zonder *[!UICONTROL Use in Search]* ook ingesteld op *Ja*. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.36 is geïnstalleerd. De patch-id is ACSD-50887. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De eigenschap productkenmerk *[!UICONTROL Use in Search Results Layered Navigation]* kan worden ingesteld op *Ja* zonder *[!UICONTROL Use in Search]* ook ingesteld op *Ja*.

Deze instellingen zijn ontworpen voor gezamenlijk gebruik. Wanneer de pleister is aangebracht, wordt de *[!UICONTROL Use in Search]* optie is ingesteld op *Nee* de *[!UICONTROL Use in Search Results Layered Navigation]* -optie is verborgen zodat deze werkt alsof deze ook is ingesteld op *Nee*.

<u>Stappen om te reproduceren</u>:

1. Navigeer in Beheer naar **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** en maak een kenmerk met het type multiselect en stel het volgende in:

   * *[!UICONTROL Use in Search]= Nee*
   * *[!UICONTROL Use in Layered Navigation]= (Willekeurige optie)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Ja*
   * *Name = Test_attribute*
   * *Opties*:
      * *Sticker*
      * *Picker*

1. Voeg het nieuwe kenmerk toe aan de standaardkenmerkset.
1. Twee producten maken:

   1. Eerste product:
      * Name = Sticker
      * Prijs, QTY, Gewicht instellen op 1
      * Test_attribute = select, optie *Sticker*

   1. Tweede product:
      * Naam = kiezer
      * Prijs, QTY, Gewicht instellen op 1
      * Test_attribute = selecteer beide opties

1. Uitvoeren `catalogsearch_fulltext` redex:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Zoeken op het woord *sticker* op de opslagplaats.

<u>Verwachte resultaten</u>:

Alleen het product *Sticker* wordt geretourneerd, omdat [!DNL Elasticsearch] Test_attribute niet indexeren wanneer *[!UICONTROL Use in Search]* is ingesteld op *Nee*.

<u>Werkelijke resultaten</u>:

Beide producten worden geretourneerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
